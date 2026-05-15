---
name: llm-web-data-collection
description: Automate web-scale data collection for research datasets using a human-in-the-loop LLM framework. This skill implements the methodology from "LLM-Based Web Data Collection for Research Dataset Creation" (EMNLP 2025 Findings). Automatically formulates search queries, navigates web pages, extracts structured data, and performs quality control while mitigating search bias and LLM hallucinations.
allowed-tools: [Read, Write, Edit, Bash, WebFetch, Browser]
license: MIT license
metadata:
    skill-author: Adapted from Berkane, Charpignon & Majumder (EMNLP 2025)
    paper-source: "LLM-Based Web Data Collection for Research Dataset Creation"
---

# LLM-Based Web Data Collection for Research Datasets

## Overview

This skill provides a human-in-the-loop framework for automating web-scale data collection using Large Language Models. It addresses the challenges of manual data collection being time-consuming and error-prone by automating:

1. **Query Formulation**: Automatically generate search engine queries from dataset descriptions
2. **Web Navigation**: Identify and navigate to relevant web pages
3. **Data Extraction**: Extract structured data points of interest
4. **Quality Control**: Validate extracted data for accuracy and completeness

**Key Innovation**: Human-in-the-loop design allows researchers to inspect and adjust decisions at each stage, ensuring alignment with research objectives while mitigating LLM hallucinations and search engine bias.

## When to Use This Skill

Use this skill when:
- Collecting structured data from diverse web sources
- Building research datasets that require web scraping
- Manual data collection is too slow or error-prone
- Need quality-controlled, structured output from unstructured web data
- Requiring human oversight for data collection decisions
- Creating custom datasets for medical, scientific, or social research

## Core Workflow

### Phase 1: Dataset Specification

1. **Define Target Dataset**:
   ```python
   dataset_spec = {
       "name": "Clinical Trial Sites",
       "description": "Collect information about clinical trial sites including location, specialties, and contact information",
       "fields": [
           {"name": "site_name", "type": "string", "required": True},
           {"name": "location", "type": "string", "required": True},
           {"name": "specialties", "type": "list", "required": False},
           {"name": "contact_email", "type": "email", "required": False},
           {"name": "phone", "type": "phone", "required": False},
           {"name": "website", "type": "url", "required": False}
       ],
       "constraints": [
           "Only include active sites",
           "Focus on US-based facilities",
           "Prefer academic medical centers"
       ]
   }
   ```

2. **Human Review Point**: 
   - Review and refine dataset specification
   - Clarify ambiguous requirements
   - Adjust field definitions as needed

### Phase 2: Automated Query Formulation

1. **LLM-Based Query Generation**:
   ```python
   def generate_search_queries(dataset_spec, llm):
       """
       Use LLM to generate diverse search queries
       from dataset description
       """
       prompt = f"""
       Given this dataset specification:
       {json.dumps(dataset_spec, indent=2)}
       
       Generate 20 diverse search engine queries that would help
       find web pages containing this information.
       
       Consider:
       - Different phrasings of the same concept
       - Specific vs general queries
       - Including and excluding certain terms
       - Different source types (directories, databases, articles)
       
       Return as JSON list of queries.
       """
       
       response = llm.generate(prompt)
       queries = parse_json(response)
       
       return queries
   ```

2. **Query Diversification**:
   ```python
   def diversify_queries(initial_queries, llm):
       """
       Expand queries to reduce search engine bias:
       - Add synonyms
       - Vary query structure
       - Include different geographic modifiers
       - Add temporal modifiers if relevant
       """
       diversified = []
       for query in initial_queries:
           variations = llm.generate_variations(query)
           diversified.extend(variations)
       
       # Remove duplicates and near-duplicates
       return deduplicate(diversified)
   ```

3. **Human Review Point**:
   - Review generated queries
   - Add domain-specific queries
   - Remove irrelevant or biased queries

### Phase 3: Web Navigation and Discovery

1. **Search Execution**:
   ```python
   def execute_search(queries, search_engine="google"):
       """
       Execute search queries and collect URLs
       """
       all_results = []
       
       for query in queries:
           results = search_api.search(
               query, 
               num_results=50,
               engine=search_engine
           )
           for result in results:
               result['source_query'] = query
           all_results.extend(results)
       
       return deduplicate_urls(all_results)
   ```

2. **Page Relevance Scoring**:
   ```python
   def score_page_relevance(url, page_content, dataset_spec, llm):
       """
       Use LLM to assess page relevance to dataset spec
       """
       prompt = f"""
       Dataset objective: {dataset_spec['description']}
       
       Page URL: {url}
       Page content (first 5000 chars): {page_content[:5000]}
       
       Score this page's relevance (0-10) and explain:
       1. Does it contain relevant data points?
       2. Is the data structured or extractable?
       3. Is this a primary source or aggregator?
       
       Return JSON: {{"score": X, "reasoning": "...", "data_fields_present": [...]}}
       """
       
       return llm.generate(prompt)
   ```

3. **Human Review Point**:
   - Review top-scoring pages
   - Adjust relevance criteria
   - Add/remove page types

### Phase 4: Data Extraction

1. **Schema-Guided Extraction**:
   ```python
   def extract_data(page_content, dataset_spec, llm):
       """
       Extract structured data according to schema
       """
       prompt = f"""
       Extract the following fields from this page content:
       
       Fields to extract:
       {json.dumps(dataset_spec['fields'], indent=2)}
       
       Page content:
       {page_content}
       
       Rules:
       - Only extract explicitly stated information
       - Mark uncertain extractions with confidence score
       - Return null for missing required fields
       - Flag potential hallucination risks
       
       Return JSON matching the schema.
       """
       
       extracted = llm.generate(prompt)
       return validate_extraction(extracted, dataset_spec)
   ```

2. **Hallucination Mitigation**:
   ```python
   def verify_extraction(extracted_data, page_content, llm):
       """
       Verify extracted data against source to prevent hallucination
       """
       verification_results = []
       
       for field, value in extracted_data.items():
           # Check if value appears verbatim or closely in source
           if not find_in_source(value, page_content):
               # Use LLM to verify derivation
               prompt = f"""
               Verify this extraction:
               Field: {field}
               Extracted value: {value}
               
               Source text: {page_content}
               
               Is this value:
               1. Directly stated in source
               2. Reasonably derived from source
               3. Possibly hallucinated
               
               Return confidence score and evidence.
               """
               verification = llm.generate(prompt)
               verification_results.append(verification)
       
       return flag_low_confidence(verification_results)
   ```

3. **Human Review Point**:
   - Review flagged extractions
   - Correct hallucinated values
   - Provide feedback for future extractions

### Phase 5: Quality Control

1. **Cross-Validation**:
   ```python
   def cross_validate(dataset, external_sources):
       """
       Validate extracted data against known sources
       """
       validation_results = []
       
       for record in dataset:
           # Check against external databases/APIs
           external_match = lookup_external(record, external_sources)
           
           if external_match:
               agreement = compute_agreement(record, external_match)
               validation_results.append({
                   'record': record,
                   'external_match': external_match,
                   'agreement': agreement
               })
       
       return validation_results
   ```

2. **Consistency Checks**:
   ```python
   def check_consistency(dataset):
       """
       Check for internal consistency:
       - Duplicate detection
       - Conflicting values
       - Outlier detection
       - Format validation
       """
       issues = []
       
       # Duplicate detection
       duplicates = find_duplicates(dataset)
       issues.extend(duplicates)
       
       # Value consistency (same entity, different values)
       conflicts = find_conflicts(dataset)
       issues.extend(conflicts)
       
       # Outlier detection
       outliers = detect_outliers(dataset)
       issues.extend(outliers)
       
       return issues
   ```

3. **Human Review Point**:
   - Review flagged quality issues
   - Resolve conflicts
   - Approve final dataset

### Phase 6: Dataset Export

1. **Generate Research-Ready Output**:
   ```python
   def export_dataset(dataset, output_format="csv"):
       """
       Export in standard research formats
       """
       # CSV for tabular data
       if output_format == "csv":
           df = pd.DataFrame(dataset)
           df.to_csv("dataset.csv", index=False)
       
       # JSON for nested data
       elif output_format == "json":
           with open("dataset.json", "w") as f:
               json.dump(dataset, f, indent=2)
       
       # Generate data dictionary
       generate_data_dictionary(dataset)
       
       # Generate provenance log
       generate_provenance_log(dataset)
   ```

2. **Documentation**:
   ```markdown
   # Dataset Documentation
   
   ## Collection Methodology
   - Queries used: [list]
   - Sources searched: [list]
   - Date range: [dates]
   
   ## Quality Metrics
   - Total records: X
   - Verified records: Y%
   - Human-reviewed: Z%
   
   ## Limitations
   - Search engine bias mitigation: [description]
   - Known gaps: [description]
   
   ## Provenance
   - Each record includes source URL
   - Extraction confidence scores included
   ```

## Mitigating Bias and Hallucinations

### Search Engine Bias
1. **Use multiple search engines** (Google, Bing, DuckDuckGo)
2. **Diversify query formulations** 
3. **Vary geographic/temporal modifiers**
4. **Track query-to-result mapping**

### LLM Hallucinations
1. **Always verify against source text**
2. **Flag uncertain extractions**
3. **Use confidence thresholds**
4. **Cross-validate with external sources**
5. **Human review of edge cases**

## Best Practices

1. **Start small**: Test with 10-20 pages before scaling
2. **Iterate specifications**: Refine based on early results
3. **Document decisions**: Log all human review points
4. **Track provenance**: Maintain source URLs for all data
5. **Version datasets**: Track changes over time

## Human-in-the-Loop Checkpoints

| Phase | Checkpoint | Decision |
|-------|------------|----------|
| 1 | Dataset spec review | Approve/modify schema |
| 2 | Query review | Add/remove queries |
| 3 | Page relevance | Adjust scoring criteria |
| 4 | Extraction review | Correct extractions |
| 5 | Quality review | Resolve conflicts |
| 6 | Final approval | Approve dataset |

## Dependencies

```bash
# LLM
pip install openai  # or anthropic, google-generativeai

# Web
pip install requests beautifulsoup4 selenium

# Data
pip install pandas

# Search APIs (optional)
pip install googlesearch-python
```

## Integration with Other Skills

- **browser**: Navigate complex web pages
- **perplexity-search**: Alternative search source
- **exploratory-data-analysis**: Analyze collected data
- **statistical-analysis**: Validate dataset quality

## References

- Berkane, T., Charpignon, M.-L., & Majumder, M. S. (2025). LLM-Based Web Data Collection for Research Dataset Creation. Findings of EMNLP 2025.
