# Genomic Biomarker Discovery for Breast Cancer Using Machine Learning and Cloud Computing

An end-to-end bioinformatics and machine learning pipeline for breast cancer biomarker discovery using TCGA RNA-seq datasets, differential gene expression analysis, pathway enrichment, and leakage-free transcriptomic classification workflows.

---

# Overview

This project analyzes TCGA Breast Cancer (BRCA) RNA-seq data to identify stable genomic biomarkers associated with tumor progression and transcriptomic dysregulation.

The workflow combines:
- RNA-seq preprocessing
- Differential gene expression (DEG) analysis
- Stable biomarker discovery
- KEGG pathway enrichment
- Leakage-free machine learning
- PCA and heatmap visualization

---

# Objectives

- Build a reproducible transcriptomic analysis workflow
- Identify significantly dysregulated genes
- Discover stable breast cancer biomarkers
- Develop leakage-free ML classification pipelines
- Evaluate tumor vs normal transcriptomic separation

---

# Dataset

## Source
- TCGA Breast Cancer (BRCA)

## Data Used
- RNA-seq TPM gene expression matrix
- Clinical metadata

---

# Tech Stack

## Languages
- Python
- R

## Bioinformatics
- DESeq2
- GSEApy
- KEGG
- Bioconductor

## Machine Learning
- Scikit-learn
- Logistic Regression
- LASSO Regression
- Random Forest

## Data Processing
- Pandas
- NumPy
- SciPy

## Visualization
- Matplotlib
- Seaborn
- Plotly

## Environment
- Google Colab
- GitHub

---

# Pipeline Architecture

```text
TCGA RNA-seq Data
        │
        ▼
Data Cleaning & Normalization
        │
        ▼
Tumor vs Normal Labeling
        │
        ▼
Differential Expression Analysis
        │
        ▼
Stable Biomarker Selection
        │
        ▼
KEGG Pathway Enrichment
        │
        ▼
Leakage-Free ML Pipeline
        │
        ▼
PCA & Heatmap Visualization
```

---

# Workflow

## 1. Data Preprocessing
- Cleaned and normalized TPM gene expression data
- Removed missing and low-expression genes
- Generated tumor vs normal labels

---

## 2. Differential Gene Expression Analysis

Performed tumor vs normal DEG analysis using:
- Fold-change computation
- Welch’s t-test
- Benjamini-Hochberg FDR correction

### Result
- Identified ~1,300 significantly dysregulated genes

---

# Biomarker Discovery

To prevent information leakage:
- DEG analysis was performed independently within each training fold
- Top biomarkers were selected fold-wise
- Stable biomarkers were identified across stratified cross-validation folds

---

# Machine Learning Pipeline

## Models Evaluated
- Logistic Regression
- LASSO Logistic Regression
- Random Forest

## Validation Strategy
- Stratified 5-Fold Cross Validation
- Fold-wise DEG analysis
- Train-only feature selection
- ROC-AUC evaluation

---

# Results

| Model | Mean Accuracy | Mean ROC-AUC |
|---|---|---|
| Logistic Regression | 99.4% | 0.9994 |
| LASSO Regression | 99.5% | 0.9997 |
| Random Forest | 99.3% | 0.9993 |

---

# Pathway Enrichment Analysis

KEGG enrichment analysis identified pathways associated with breast cancer progression, including:
- Cell cycle regulation
- Cytokine signaling
- Viral carcinogenesis
- PPAR signaling

---

# Visualizations

## Differential Expression Volcano Plot
![Volcano Plot](volcano_plot.png)

## LASSO ROC Curve
![ROC Curve](lasso_roc_curve.png)

## Stable Biomarker Heatmap
![Heatmap](Biomarkers_Heatmap.png)

## PCA of Transcriptomic Biomarkers
![PCA Plot](pca_biomarker_plot.png)

---

# Key Features

- End-to-end transcriptomic analysis workflow
- Leakage-free ML evaluation
- Stable biomarker discovery
- Fold-wise DEG analysis
- KEGG pathway interpretation
- Publication-style genomics visualizations

---

# Project Structure

```text
bioinformatics-cancer-pipeline/
│
├── notebooks/
│   ├── 1_data_ingestion&Preprocessing.ipynb
│   ├── 2_differential_expression.ipynb
│   └── 3_ml_modeling_&visualization.ipynb
│
├── outputs/
│   ├── graphs/
│   ├── biomarkers/
│   └── model_metrics/
│
├── models/
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Future Improvements

- External validation using GEO cohorts
- Survival analysis
- Multi-omics integration
- SHAP-based interpretability
- Streamlit deployment
- MLflow experiment tracking
- GCP Vertex AI integration