## Comparative Dataset Analysis and Exploratory Data Mining

### Author
Michael “Mikey” Morris

---

## Overview

This project explores and compares three real-world datasets using data mining concepts from CSCE 676, with an emphasis on data properties, algorithmic feasibility, bias, and ethical considerations. The goal is to evaluate which mining techniques are appropriate for each dataset, distinguish between course-covered and external methods, and motivate directions for deeper analysis.

The datasets analyzed are:

- MovieLens (user–movie ratings)
- Steam Reviews (user-generated game reviews)
- NASA Exoplanet Archive (astronomical discovery records)

Each dataset represents a different data modality (transactional, text-heavy, scientific tabular data), enabling meaningful comparison across mining tasks.

---

## Datasets

### 1. MovieLens
- User–item rating data with timestamps
- Large-scale transactional dataset
- Suitable for recommendation systems, association rules, and collaborative filtering

### 2. Steam Reviews
- Text-based user reviews with temporal and engagement metadata
- Includes game metadata via joins
- Suitable for text mining, sentiment analysis, and bias analysis

### 3. NASA Exoplanet Archive
- Scientific tabular dataset with many numeric features
- High missingness in derived measurements
- Suitable for clustering, anomaly detection, and trend analysis

---

## Analysis Structure

### (B) Comparative Analysis of Datasets
For each dataset, the following dimensions are evaluated:
- Supported data mining tasks (course vs. external techniques)
- Data quality issues (missingness, noise, sparsity)
- Algorithmic feasibility (scalability of candidate algorithms)
- Bias considerations (engagement, temporal, sampling bias)
- Ethical considerations (privacy, power dynamics, misuse risk)

### (C) Dataset Selection
One dataset is selected for deeper analysis and justified based on:
- Alignment with course techniques
- Opportunities for external methods
- Trade-offs and limitations

### (D) Exploratory Data Analysis
Exploratory analysis includes:
- Distributional properties
- Sparsity and skew
- Temporal patterns
- Initial signals motivating advanced techniques

### (E) Initial Insights and Direction
Based on EDA:
- Key observations are summarized
- Hypotheses are formed
- Potential research questions are proposed

---

## Tools and Libraries

- Python 3
- pandas, numpy
- matplotlib
- gzip, ast, json
- Jupyter Notebook / Google Colab

---

## Notes on Reproducibility

- Large datasets are sampled where necessary for feasibility.
- All reported statistics and observations are derived from executed code.
- External techniques are discussed conceptually unless explicitly implemented.

---

## References

Relevant academic work on recommendation systems, association rules, and collaborative filtering is cited using Markdown-compatible references suitable for Jupyter and Google Colab.
