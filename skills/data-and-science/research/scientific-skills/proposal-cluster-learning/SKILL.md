---
name: proposal-cluster-learning
description: Implement Proposal Cluster Learning (PCL) for Weakly Supervised Object Detection (WSOD). This skill implements the methodology from the IEEE TPAMI paper "PCL: Proposal Cluster Learning for Weakly Supervised Object Detection" by Tang et al. Enables training object detectors using only image-level labels without bounding box annotations.
allowed-tools: [Read, Write, Edit, Bash]
license: MIT license
metadata:
    skill-author: Adapted from Tang et al. (IEEE TPAMI)
    paper-source: "PCL: Proposal Cluster Learning for Weakly Supervised Object Detection"
---

# Proposal Cluster Learning for Weakly Supervised Object Detection

## Overview

Proposal Cluster Learning (PCL) is an end-to-end deep network approach for Weakly Supervised Object Detection (WSOD). It allows training object detectors using only **image-level labels** (e.g., "this image contains a dog") without requiring expensive bounding box annotations.

**Key Innovation**: Instead of treating detection as classification (like standard MIL approaches), PCL generates "proposal clusters" - groups of spatially adjacent proposals associated with the same object - and uses these clusters to iteratively refine instance classifiers.

**Benefits**:
- Reduces annotation cost (no bounding boxes needed)
- Detects complete objects (not just discriminative parts)
- State-of-the-art results on PASCAL VOC, ImageNet, MS-COCO

## When to Use This Skill

Use this skill when:
- You have image-level labels but no bounding box annotations
- Annotation budget is limited for object detection tasks
- Building detection systems for new domains without existing annotations
- Need to rapidly prototype object detectors
- Working with large-scale datasets where box annotation is infeasible

## Core Concepts

### The Problem with Standard MIL

Traditional Multiple Instance Learning (MIL) for WSOD:
- Treats each image as a "bag" of region proposals
- Learns to classify based on most discriminative regions
- **Problem**: Often focuses on object PARTS (e.g., dog's face) not complete objects

### PCL Solution: Proposal Clusters

1. **Group related proposals**: Proposals covering the same object are spatially adjacent
2. **Cluster-based learning**: Treat each cluster as a mini-bag
3. **Iterative refinement**: Multiple CNN streams refine detections

## Architecture Overview

```
Image
  │
  ▼
┌─────────────────────────────────────────────────────────┐
│                    CNN Backbone (VGG16)                  │
└─────────────────────────────────────────────────────────┘
  │
  ▼
┌─────────────────────────────────────────────────────────┐
│              Region Proposal Network (RPN)               │
│                  or Selective Search                     │
└─────────────────────────────────────────────────────────┘
  │
  ▼
┌─────────────────────────────────────────────────────────┐
│                  ROI Pooling Layer                       │
└─────────────────────────────────────────────────────────┘
  │
  ├──────► Stream 1: MIL Network (Initial Classification)
  │
  ├──────► Stream 2: PCL Refinement 1
  │
  ├──────► Stream 3: PCL Refinement 2
  │
  └──────► Stream K: PCL Refinement K-1
```

## Core Workflow

### Phase 1: Setup and Data Preparation

1. **Prepare Image-Level Labels**:
   ```python
   # Dataset format: image path + list of classes present
   dataset = {
       "image_001.jpg": ["dog", "person"],
       "image_002.jpg": ["car"],
       "image_003.jpg": ["dog", "cat"],
       # ...
   }
   ```

2. **Generate Region Proposals**:
   ```python
   def generate_proposals(image, method="selective_search"):
       """
       Generate region proposals for each image
       Options:
       - Selective Search (traditional)
       - Edge Boxes
       - RPN (if using two-stage approach)
       """
       if method == "selective_search":
           import cv2
           ss = cv2.ximgproc.segmentation.createSelectiveSearchSegmentation()
           ss.setBaseImage(image)
           ss.switchToSelectiveSearchFast()
           proposals = ss.process()
       
       # Typically use top 2000 proposals
       return proposals[:2000]
   ```

### Phase 2: MIL Network (Stream 1)

1. **Feature Extraction**:
   ```python
   class MILNetwork(nn.Module):
       def __init__(self, num_classes, backbone='vgg16'):
           super().__init__()
           self.backbone = load_pretrained_backbone(backbone)
           self.roi_pool = ROIPool(output_size=(7, 7))
           
           # Two parallel branches
           self.fc_cls = nn.Linear(4096, num_classes)  # Classification
           self.fc_det = nn.Linear(4096, num_classes)  # Detection
       
       def forward(self, image, proposals):
           # Extract features
           features = self.backbone(image)
           
           # ROI pooling for each proposal
           roi_features = self.roi_pool(features, proposals)
           
           # Classification scores (image-level)
           cls_scores = F.softmax(self.fc_cls(roi_features), dim=0)
           
           # Detection scores (proposal-level)
           det_scores = F.softmax(self.fc_det(roi_features), dim=1)
           
           # Combine: proposal score = cls * det
           proposal_scores = cls_scores * det_scores
           
           return proposal_scores
   ```

2. **MIL Loss**:
   ```python
   def mil_loss(proposal_scores, image_labels):
       """
       Image-level classification loss:
       Aggregate proposal scores to image-level prediction
       """
       # Sum over proposals for each class
       image_scores = proposal_scores.sum(dim=0)
       
       # Binary cross-entropy with image labels
       loss = F.binary_cross_entropy(
           torch.sigmoid(image_scores),
           image_labels
       )
       
       return loss
   ```

### Phase 3: Proposal Clustering

1. **Generate Proposal Clusters**:
   ```python
   def generate_proposal_clusters(proposals, proposal_scores, iou_threshold=0.5):
       """
       Group proposals into clusters based on:
       1. Spatial overlap (IoU)
       2. Score similarity
       """
       clusters = []
       
       # For each class
       for c in range(num_classes):
           class_scores = proposal_scores[:, c]
           
           # Find high-scoring proposals
           high_scoring = proposals[class_scores > 0.1]
           
           # Cluster by spatial overlap
           cluster_assignments = cluster_by_iou(
               high_scoring, 
               iou_threshold=iou_threshold
           )
           
           for cluster_id in np.unique(cluster_assignments):
               cluster_proposals = high_scoring[cluster_assignments == cluster_id]
               clusters.append({
                   'class': c,
                   'proposals': cluster_proposals,
                   'center': compute_cluster_center(cluster_proposals)
               })
       
       return clusters
   ```

2. **Assign Labels from Clusters**:
   ```python
   def assign_cluster_labels(proposals, clusters):
       """
       Assign pseudo-labels to proposals based on clusters:
       - Proposals in object cluster → object label
       - Other proposals → background
       """
       labels = np.zeros(len(proposals))  # Default: background
       
       for cluster in clusters:
           for proposal in cluster['proposals']:
               idx = find_proposal_index(proposal, proposals)
               labels[idx] = cluster['class']
       
       return labels
   ```

### Phase 4: PCL Refinement Streams

1. **Refinement Network**:
   ```python
   class PCLRefinementStream(nn.Module):
       def __init__(self, num_classes):
           super().__init__()
           self.fc1 = nn.Linear(4096, 4096)
           self.fc2 = nn.Linear(4096, num_classes + 1)  # +1 for background
       
       def forward(self, roi_features, cluster_labels):
           x = F.relu(self.fc1(roi_features))
           scores = self.fc2(x)
           
           # Supervised by cluster-generated pseudo-labels
           loss = F.cross_entropy(scores, cluster_labels)
           
           return scores, loss
   ```

2. **Iterative Refinement**:
   ```python
   def train_pcl(images, labels, num_refinement_streams=3):
       """
       Train PCL with multiple refinement streams
       """
       model = PCLNetwork(num_classes, num_refinement_streams)
       
       for epoch in range(num_epochs):
           for image, label in dataloader:
               # Generate proposals
               proposals = generate_proposals(image)
               
               # Extract ROI features
               roi_features = model.extract_features(image, proposals)
               
               # Stream 1: MIL
               mil_scores = model.mil_stream(roi_features)
               mil_loss = compute_mil_loss(mil_scores, label)
               
               # Generate clusters from MIL output
               clusters = generate_proposal_clusters(proposals, mil_scores)
               
               # Refinement streams
               total_loss = mil_loss
               current_scores = mil_scores
               
               for stream_idx in range(num_refinement_streams):
                   # Assign labels from clusters
                   pseudo_labels = assign_cluster_labels(proposals, clusters)
                   
                   # Refine
                   refined_scores, refine_loss = model.refinement_streams[stream_idx](
                       roi_features, pseudo_labels
                   )
                   
                   total_loss += refine_loss
                   
                   # Update clusters for next stream
                   clusters = generate_proposal_clusters(proposals, refined_scores)
                   current_scores = refined_scores
               
               # Backprop
               total_loss.backward()
               optimizer.step()
   ```

### Phase 5: Inference

1. **Object Detection**:
   ```python
   def detect_objects(model, image, score_threshold=0.5, nms_threshold=0.3):
       """
       Run inference to detect objects
       """
       proposals = generate_proposals(image)
       roi_features = model.extract_features(image, proposals)
       
       # Use final refinement stream for detection
       final_scores = model.final_stream(roi_features)
       
       # Apply NMS per class
       detections = []
       for c in range(num_classes):
           class_scores = final_scores[:, c]
           high_scoring = class_scores > score_threshold
           
           if high_scoring.any():
               boxes = proposals[high_scoring]
               scores = class_scores[high_scoring]
               
               # Non-maximum suppression
               keep = nms(boxes, scores, nms_threshold)
               
               for idx in keep:
                   detections.append({
                       'class': c,
                       'box': boxes[idx],
                       'score': scores[idx]
                   })
       
       return detections
   ```

## Implementation Tips

### Preventing Part Detection

The key advantage of PCL is detecting complete objects, not just discriminative parts:

1. **Cluster-based learning**: Forces network to consider entire object regions
2. **Multiple refinement streams**: Progressively improves localization
3. **IoU-based clustering**: Groups spatially related proposals

### Hyperparameters

| Parameter | Typical Value | Notes |
|-----------|--------------|-------|
| Proposals per image | 2000 | Top-K from proposal method |
| Refinement streams | 3 | More streams = better but slower |
| IoU threshold (clustering) | 0.4-0.5 | Lower = larger clusters |
| Learning rate | 0.001 | With decay |
| Batch size | 2 | Limited by GPU memory |

### Training Schedule

```python
# Typical training schedule
lr_schedule = {
    0: 0.001,    # Initial LR
    40000: 0.0001,  # Decay at 40k iterations
    70000: 0.00001  # Final decay
}
total_iterations = 80000
```

## Best Practices

1. **Pre-training**: Use ImageNet pre-trained backbone
2. **Proposal quality**: Good proposals are crucial; use multiple methods
3. **Data augmentation**: Standard augmentation (flip, crop, color)
4. **Gradual refinement**: Don't skip refinement streams
5. **Evaluation**: Use standard detection metrics (mAP)

## Expected Results

Based on original paper (PASCAL VOC 2007):

| Method | mAP |
|--------|-----|
| Standard MIL | 39.3% |
| PCL (3 streams) | 48.8% |
| PCL + Regression | 52.2% |

## Dependencies

```bash
# Deep learning
pip install torch torchvision

# Image processing
pip install opencv-python pillow

# Proposals (selective search)
pip install opencv-contrib-python

# Evaluation
pip install pycocotools
```

## Integration with Other Skills

- **pytorch**: Implementation framework
- **torchvision**: Pre-trained backbones
- **exploratory-data-analysis**: Analyze detection results
- **matplotlib**: Visualize detections

## References

- Tang, P., Wang, X., Bai, S., Shen, W., Bai, X., Liu, W., & Yuille, A. PCL: Proposal Cluster Learning for Weakly Supervised Object Detection. IEEE TPAMI.
- ArXiv: https://arxiv.org/abs/1807.03342
