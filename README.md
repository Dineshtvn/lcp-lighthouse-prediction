# Predicting Largest Contentful Paint from Lighthouse Diagnostic Metrics: A Leakage-Aware Machine Learning Study

Official implementation accompanying the research paper:

**Predicting Largest Contentful Paint from Lighthouse Diagnostic Metrics: A Leakage-Aware Machine Learning Study**

---

## Overview

This repository contains the complete implementation of a leakage-aware machine learning pipeline for predicting Google's Largest Contentful Paint (LCP) using Google Lighthouse diagnostic metrics.

Unlike previous Lighthouse-based studies, this work explicitly separates leakage-free (SAFE) diagnostic features from leakage-prone (FULL) features to measure the true predictive capability of Lighthouse metrics without target leakage.

The repository provides the complete implementation, datasets, and reproducibility resources required to reproduce the experiments reported in the paper.

---

## Repository Structure

```
.
├── DATASET_generation.ipynb
├── Implementation.ipynb
├── final_raw_dataset.csv
├── Raw_Lighthouse_Crawl_Datasets.zip
├── README.md
├── requirements.txt
├── figures.zip

```

---

## Dataset

The dataset consists of **1,785 unique desktop websites** collected using Google Lighthouse desktop audits.

Each website was audited **three times** before aggregation to reduce measurement variability.

The repository includes:

- Raw Lighthouse crawl datasets
- Final processed dataset
- Dataset generation notebook

---

## Methodology

The proposed pipeline includes:

- Leakage-aware SAFE/FULL feature engineering
- Fold-safe preprocessing
- Winsorization
- Group-aware train/test splitting
- GroupKFold cross-validation
- Hyperparameter optimization
- SHAP explainability
- Permutation importance
- Feature ablation analysis
- Secondary LCP severity classification

---

## Machine Learning Models

### Regression

- Linear Regression
- Ridge Regression
- Random Forest
- Gradient Boosting
- XGBoost
- LightGBM
- CatBoost
- Support Vector Regression (SVR)

### Classification

- Random Forest (Class-weighted)
- Random Forest (SMOTE-balanced)

---

## Key Results

Leakage-free (SAFE) prediction:

- Holdout Test R² = **0.330**
- 5-Fold GroupKFold CV R² = **0.334 ± 0.027**

Leakage-prone (FULL) prediction:

- CatBoost R² = **0.955**

Measured leakage inflation:

- **ΔR² = 0.625**

SHAP and permutation importance consistently identify **Speed Index** and **First Contentful Paint (FCP)** as the dominant leakage-free predictors.

---

## Reproducing the Experiments

### Step 1

Run

```
DATASET_generation.ipynb
```

to generate and preprocess the dataset.

### Step 2

Run

```
Implementation.ipynb
```

to reproduce all experiments, figures, tables, and evaluation results reported in the paper.

---

## Repository Contents

- Complete implementation
- Dataset generation pipeline
- Raw Lighthouse crawl datasets
- Final processed dataset
- Experimental configuration
- Feature engineering pipeline
- Reproducibility package

---

## Requirements

Install the required Python packages:

```bash
pip install -r requirements.txt
```

---

## Citation

If you use this repository in your research, please cite:

> Predicting Largest Contentful Paint from Lighthouse Diagnostic Metrics: A Leakage-Aware Machine Learning Study

(Bibliographic information will be updated after publication.)

---

## License

This project is released under the MIT License.

---

## Contact

For questions regarding the implementation or the accompanying paper, please open a GitHub Issue in this repository.
