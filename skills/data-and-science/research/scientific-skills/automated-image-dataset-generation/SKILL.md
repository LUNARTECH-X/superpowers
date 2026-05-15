---
name: automated-image-dataset-generation
description: Generate large-scale image datasets automatically using web scraping and Large Multimodal Models (LMMs) like Gemini Vision. This skill implements the methodology from the research paper "Automated Image Dataset Generation Using Web Scraping and Large Multimodal Models for Construction Applications" by Gharib & Moselhi. Achieves ~95% accuracy in metadata generation for image classification and object detection tasks.
allowed-tools: [Read, Write, Edit, Bash, WebFetch, Browser]
license: MIT license
metadata:
    skill-author: Adapted from Gharib & Moselhi (ISARC 2025)
    paper-source: "Automated Image Dataset Generation Using Web Scraping and LMMs for Construction Applications"
---

# Automated Image Dataset Generation with LMMs

## Overview

This skill provides a scalable, reusable framework for automatically generating labeled image datasets using web scraping combined with Large Multimodal Models (LMMs) for metadata generation. The methodology addresses the challenge of manual data collection being resource-intensive, error-prone, and time-consuming.

**Key Capabilities:**
- Automated web image collection at scale (50,000+ images)
- LMM-powered metadata generation with ~95% accuracy
- Rule-based filtering for domain-specific categorization
- Structured output for object detection and classification tasks

## When to Use This Skill

Use this skill when:
- Building custom image datasets for machine learning applications
- Collecting domain-specific images that aren't available in existing datasets
- Needing automated image labeling/metadata generation
- Working on object detection or image classification projects
- Manual annotation is too expensive or time-consuming
- Requiring large-scale training data for computer vision models

## Core Workflow

### Phase 1: Query Design and Planning

1. **Define Target Categories**:
   - Identify specific objects/classes to collect
   - Create hierarchical category structure if needed
   - Example categories: beams, columns, trusses, steel frames

2. **Design Search Queries**:
   ```python
   # Generate diverse search queries
   categories = ["structural steel beam", "steel column construction", "roof truss"]
   query_variations = [
       f"{cat} {mod}" 
       for cat in categories 
       for mod in ["photo", "site", "construction", "building"]
   ]
   ```

3. **Set Collection Parameters**:
   - Target image count per category
   - Image quality thresholds (resolution, format)
   - Source diversity requirements

### Phase 2: Web Scraping

1. **Implement Multi-Source Scraping**:
   ```python
   import requests
   from bs4 import BeautifulSoup
   from selenium import webdriver
   
   def scrape_images(query, num_images=1000):
       """
       Scrape images from multiple sources:
       - Google Images
       - Bing Images
       - Domain-specific sites
       """
       images = []
       
       # Use appropriate rate limiting
       # Respect robots.txt
       # Store source URLs for attribution
       
       return images
   ```

2. **Image Download and Storage**:
   ```python
   def download_images(image_urls, output_dir):
       """
       Download images with:
       - Duplicate detection (hash-based)
       - Format validation
       - Resolution filtering
       - Metadata preservation
       """
       pass
   ```

3. **Initial Filtering**:
   - Remove corrupted/invalid images
   - Filter by minimum resolution (e.g., 224x224)
   - Deduplicate using perceptual hashing

### Phase 3: LMM-Based Metadata Generation

1. **Configure LMM (Gemini Vision or equivalent)**:
   ```python
   import google.generativeai as genai
   
   genai.configure(api_key=os.environ['GOOGLE_API_KEY'])
   model = genai.GenerativeModel('gemini-1.5-flash')
   
   def generate_metadata(image_path, categories):
       """
       Use LMM to analyze image and generate metadata
       """
       image = PIL.Image.open(image_path)
       
       prompt = f"""
       Analyze this image and determine:
       1. Does it contain any of these objects: {categories}?
       2. If yes, which specific category?
       3. Confidence level (high/medium/low)
       4. Object location description (for detection tasks)
       5. Image quality assessment
       
       Return structured JSON response.
       """
       
       response = model.generate_content([prompt, image])
       return parse_response(response.text)
   ```

2. **Batch Processing**:
   ```python
   def process_dataset(image_dir, categories, batch_size=100):
       """
       Process images in batches with:
       - Rate limiting
       - Error handling
       - Progress tracking
       - Checkpoint saving
       """
       results = []
       for batch in get_batches(image_dir, batch_size):
           batch_results = [
               generate_metadata(img, categories) 
               for img in batch
           ]
           results.extend(batch_results)
           save_checkpoint(results)
       return results
   ```

3. **Quality Metrics**:
   - Track LMM confidence scores
   - Flag low-confidence predictions for review
   - Calculate category distribution

### Phase 4: Rule-Based Filtering

1. **Apply Category Rules**:
   ```python
   def filter_by_rules(metadata, rules):
       """
       Apply domain-specific rules:
       - Minimum confidence threshold (e.g., 0.8)
       - Category-specific validation
       - Cross-reference with search query
       """
       filtered = []
       for item in metadata:
           if item['confidence'] >= rules['min_confidence']:
               if validate_category(item, rules):
                   filtered.append(item)
       return filtered
   ```

2. **Handle Edge Cases**:
   - Multi-label images (multiple categories)
   - Ambiguous classifications
   - Partial object visibility

### Phase 5: Dataset Finalization

1. **Generate Dataset Structure**:
   ```
   dataset/
   ├── images/
   │   ├── category_1/
   │   ├── category_2/
   │   └── ...
   ├── annotations/
   │   ├── metadata.json
   │   └── labels.csv
   ├── splits/
   │   ├── train.txt
   │   ├── val.txt
   │   └── test.txt
   └── README.md
   ```

2. **Create Annotation Files**:
   ```python
   def create_annotations(filtered_data, output_dir):
       """
       Generate standard annotation formats:
       - COCO format (for object detection)
       - CSV with labels (for classification)
       - YOLO format (if needed)
       """
       pass
   ```

3. **Split Dataset**:
   - Train/Val/Test split (typically 70/15/15)
   - Stratified splitting by category
   - Ensure no data leakage

## Best Practices

### Web Scraping
1. **Respect rate limits**: 1-2 requests per second
2. **Rotate user agents**: Avoid detection
3. **Use proxies**: For large-scale collection
4. **Cache responses**: Avoid redundant downloads
5. **Store source URLs**: For attribution and verification

### LMM Usage
1. **Use appropriate prompts**: Be specific about expected output format
2. **Batch processing**: Optimize API costs
3. **Handle API errors**: Implement retry logic with exponential backoff
4. **Validate responses**: Parse and validate JSON responses

### Data Quality
1. **Verify sample manually**: Check 100-200 random samples
2. **Calculate inter-annotator agreement**: If using multiple LMMs
3. **Document accuracy metrics**: Report precision/recall per category
4. **Version your dataset**: Track changes over time

### Legal & Ethical
1. **Check image licenses**: Prefer CC-licensed content
2. **Respect robots.txt**: Don't scrape disallowed pages
3. **Attribute sources**: Maintain source URLs
4. **Consider privacy**: Filter personal/sensitive content

## Expected Results

Based on the original research:
- **Collection scale**: 50,000+ raw images
- **After filtering**: ~5% relevant images (domain-specific)
- **Metadata accuracy**: 94.8%
- **Categories**: Successfully identifies 5+ distinct categories

## Integration with Other Skills

- **scientific-schematics**: Generate dataset visualization diagrams
- **exploratory-data-analysis**: Analyze dataset statistics
- **pytorch**: Train models on generated dataset
- **matplotlib/seaborn**: Visualize class distributions

## Dependencies

```bash
# Core
pip install requests beautifulsoup4 selenium pillow

# LMM
pip install google-generativeai  # or openai for GPT-4V

# Image processing
pip install imagehash opencv-python

# Dataset tools
pip install pandas scikit-learn
```

## References

- Gharib, S., & Moselhi, O. (2025). Automated Image Dataset Generation Using Web Scraping and Large Multimodal Models for Construction Applications. ISARC 2025.
