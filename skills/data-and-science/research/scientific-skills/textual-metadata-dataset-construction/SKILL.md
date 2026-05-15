---
name: textual-metadata-dataset-construction
description: Automatically construct large-scale image datasets from web sources using multiple textual metadata for semantic expansion and CNN-based filtering. This skill implements the methodology from "Automatic Image Dataset Construction with Multiple Textual Metadata" (IEEE ICME 2016). Reduces dataset bias and improves cross-dataset generalization through query expansion and progressive filtering.
allowed-tools: [Read, Write, Edit, Bash, WebFetch]
license: MIT license
metadata:
    skill-author: Adapted from IEEE ICME 2016
    paper-source: "Automatic Image Dataset Construction with Multiple Textual Metadata"
---

# Automatic Image Dataset Construction with Multiple Textual Metadata

## Overview

This skill provides a framework for automatically collecting diverse, high-quality image datasets from the web using semantic query expansion and progressive CNN-based filtering. The methodology addresses key challenges:

1. **Dataset Bias**: Reduces bias by expanding queries semantically
2. **Noise Reduction**: Filters irrelevant images through clustering and CNNs
3. **Cross-Dataset Generalization**: Creates datasets that generalize well to unseen domains

**Key Innovation**: Uses Google Books Ngrams Corpora for query expansion to capture richer semantic descriptions, then progressively filters using CNNs.

## When to Use This Skill

Use this skill when:
- Building training datasets that need to generalize across domains
- Current datasets suffer from selection bias
- Manual annotation budget is limited
- Need diverse image coverage for a concept
- Building datasets for image classification or object detection
- Comparing performance with established datasets (STL-10, CIFAR-10)

## Core Workflow

### Phase 1: Query Expansion

1. **Initial Query Definition**:
   ```python
   initial_queries = ["dog", "car", "airplane"]
   ```

2. **Semantic Expansion with N-gram Corpora**:
   ```python
   def expand_query_with_ngrams(query, ngram_data):
       """
       Expand query using Google Books Ngrams:
       - Find co-occurring terms
       - Add synonyms and related concepts
       - Include descriptive modifiers
       
       Example: "dog" → ["dog breed", "puppy", "canine", 
                         "dog playing", "dog running", ...]
       """
       expansions = []
       
       # Get bigrams containing the query
       bigrams = get_ngrams(query, n=2, ngram_data=ngram_data)
       
       # Get trigrams for context
       trigrams = get_ngrams(query, n=3, ngram_data=ngram_data)
       
       # Combine and rank by frequency
       expansions = rank_by_relevance(bigrams + trigrams)
       
       return expansions
   ```

3. **Visual Saliency Filtering**:
   ```python
   def filter_expansions(expansions, visual_model):
       """
       Remove expansions that are:
       - Visually non-salient (abstract concepts)
       - Less relevant to visual domain
       - Too generic or too specific
       
       Use pre-trained visual model to score saliency
       """
       filtered = []
       for exp in expansions:
           # Check if expansion corresponds to visually identifiable concept
           saliency_score = visual_model.predict_saliency(exp)
           if saliency_score > threshold:
               filtered.append(exp)
       return filtered
   ```

### Phase 2: Web Image Retrieval

1. **Multi-Query Image Collection**:
   ```python
   def collect_images(expanded_queries, images_per_query=500):
       """
       Retrieve images using expanded queries:
       - Use multiple search engines
       - Collect metadata (source URL, query used)
       - Diversify sources to reduce bias
       """
       all_images = []
       
       for query in expanded_queries:
           images = search_engine.image_search(
               query, 
               num_results=images_per_query
           )
           for img in images:
               img['source_query'] = query
           all_images.extend(images)
       
       return all_images
   ```

2. **Initial Preprocessing**:
   ```python
   def preprocess_images(images):
       """
       - Remove duplicates (perceptual hash)
       - Validate image format
       - Resize to standard dimensions
       - Remove corrupted files
       """
       pass
   ```

### Phase 3: Clustering-Based Noise Filtering

1. **Feature Extraction**:
   ```python
   def extract_features(images, cnn_model):
       """
       Extract deep features using pre-trained CNN
       (e.g., VGG, ResNet features from penultimate layer)
       """
       features = []
       for img in images:
           feat = cnn_model.extract_features(img)
           features.append(feat)
       return np.array(features)
   ```

2. **Cluster Analysis**:
   ```python
   from sklearn.cluster import KMeans
   
   def cluster_and_filter(features, images, n_clusters=10):
       """
       Cluster images by visual similarity:
       - Identify core clusters (likely relevant)
       - Remove outlier clusters (likely noise)
       - Keep images from dense, coherent clusters
       """
       kmeans = KMeans(n_clusters=n_clusters)
       clusters = kmeans.fit_predict(features)
       
       # Analyze cluster statistics
       cluster_stats = analyze_clusters(clusters, features)
       
       # Remove outlier clusters (low density, high variance)
       valid_clusters = [
           c for c in cluster_stats 
           if c['density'] > threshold and c['coherence'] > min_coherence
       ]
       
       filtered_images = [
           img for img, c in zip(images, clusters)
           if c in valid_clusters
       ]
       
       return filtered_images
   ```

### Phase 4: Progressive CNN Filtering

1. **Initial CNN Training**:
   ```python
   def train_initial_classifier(clustered_images, num_classes):
       """
       Train initial CNN classifier on clustered data:
       - Use cluster assignments as pseudo-labels
       - Fine-tune pre-trained model
       """
       model = load_pretrained_cnn()
       model = fine_tune(model, clustered_images)
       return model
   ```

2. **Progressive Refinement**:
   ```python
   def progressive_filtering(images, model, iterations=3):
       """
       Iteratively refine dataset:
       1. Classify all images with current model
       2. Remove low-confidence predictions
       3. Retrain model on refined set
       4. Repeat
       """
       for i in range(iterations):
           # Predict on all images
           predictions = model.predict(images)
           
           # Filter by confidence
           confident_samples = [
               (img, pred) for img, pred in zip(images, predictions)
               if pred['confidence'] > confidence_threshold(i)
           ]
           
           # Retrain on refined set
           model = train_classifier(confident_samples)
           
           images = [s[0] for s in confident_samples]
       
       return images, model
   ```

### Phase 5: Dataset Finalization

1. **Quality Verification**:
   ```python
   def verify_dataset_quality(dataset, test_set):
       """
       Evaluate dataset quality:
       - Cross-dataset generalization (test on STL-10, CIFAR-10)
       - Class balance analysis
       - Diversity metrics
       """
       # Train classifier on generated dataset
       model = train_classifier(dataset)
       
       # Test on external datasets
       stl10_accuracy = evaluate(model, stl10_test)
       cifar10_accuracy = evaluate(model, cifar10_test)
       
       return {
           'cross_dataset_acc': (stl10_accuracy + cifar10_accuracy) / 2,
           'class_balance': compute_balance(dataset),
           'diversity': compute_diversity(dataset)
       }
   ```

2. **Export Dataset**:
   ```
   dataset/
   ├── train/
   │   ├── class_1/
   │   ├── class_2/
   │   └── ...
   ├── val/
   ├── test/
   ├── metadata.json
   └── dataset_stats.md
   ```

## Key Techniques

### Query Expansion Strategy
- Use Google Books Ngrams (n=2,3,4) for semantic expansion
- Filter by visual saliency to remove abstract terms
- Balance specificity vs. diversity in expansions

### Progressive Filtering
- Start with loose confidence threshold (~0.5)
- Increase threshold each iteration (~0.6, 0.7, 0.8)
- Allows gradual refinement without losing good samples early

### Reducing Dataset Bias
- Use multiple search engines
- Diversify query expansions
- Cluster analysis ensures visual diversity
- Cross-domain validation confirms generalization

## Best Practices

1. **Query Expansion**:
   - Start with 5-10 core concepts per category
   - Generate 20-50 expansions per core concept
   - Filter to top 10-20 based on visual saliency

2. **Clustering**:
   - Use k-means with k = 10-20 clusters per category
   - Validate cluster coherence manually on samples
   - Remove clusters with < 5% of total images

3. **Progressive Filtering**:
   - Use 3-5 iterations
   - Start confidence threshold: 0.5
   - Increase by 0.1 per iteration
   - Stop when dataset size stabilizes

4. **Validation**:
   - Always test on external datasets
   - Compare with CIFAR-10, STL-10 baselines
   - Report cross-dataset accuracy

## Expected Results

Based on original research:
- Generates datasets larger than manually labeled alternatives
- Achieves comparable generalization to STL-10, CIFAR-10
- Significant performance gains on:
  - Image classification
  - Cross-dataset generalization
  - Object detection

## Dependencies

```bash
# Deep learning
pip install torch torchvision  # or tensorflow

# Clustering
pip install scikit-learn

# Image processing
pip install pillow opencv-python

# N-gram data
# Download Google Books Ngrams: https://storage.googleapis.com/books/ngrams/books/datasetsv3.html
```

## Integration with Other Skills

- **pytorch**: Train classifiers during filtering
- **scikit-learn**: Clustering and evaluation
- **matplotlib**: Visualize cluster distributions
- **exploratory-data-analysis**: Dataset statistics

## References

- "Automatic Image Dataset Construction with Multiple Textual Metadata" (IEEE ICME 2016)
- Google Books Ngram Viewer: https://books.google.com/ngrams
