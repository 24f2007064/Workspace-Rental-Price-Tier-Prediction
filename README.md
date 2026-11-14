# Workstation Rental Price-Tier Prediction

Multiclass classification project to predict the **price tier** of bookable workspaces using tabular data.

> Competition-style project focused on large-scale data cleaning, feature engineering, and gradient boosting ensembles.

---

## Overview

Workspaces rent at very different prices depending on location, facilities, booking terms, availability, and review history.  

**Goal:** Predict the `price_tier` of each listing.

**Evaluation Metric:** Macro F1 Score

---
## Dataset Structure
workstation-rental-price-tier-prediction/

└── kaggle_ready_dataset/

├── train.csv

├── test.csv

└── sample_submission.csv


## Dataset

| Split       | Records     | Columns |
|-------------|-------------|---------|
| Train       | 279,000+    | 60      |
| Test        | 114,000+    | 60      |

### Key Column Groups
- **Location & Physical attributes**
- **Facilities** (multi-label style strings)
- **Booking terms & Availability**
- **Operator information**
- **Review history**

---

## Pipeline Summary

### 1. Data Cleaning
- Missing value analysis (15–35% missing on several columns)
- Removed **1,116 duplicate rows**
- Median imputation for numeric features
- Mode imputation for categorical features
- Explicit **missingness indicators** for important fields (`operator`, `layout`, etc.)
- Invalid date values coerced to missing

### 2. Feature Engineering
Created several temporal and behavioral features:
- Listing age
- Review recency
- Operator platform age
- Activity gap
- Review presence & review share
- Additional derived features from facilities and availability patterns

### 3. Modeling
- **XGBoost** and **LightGBM** multiclass models
- **75:25 LightGBM + XGBoost ensemble**
- Class-specific probability calibration
- Careful handling of class imbalance

---

## Results

| Metric                        | Score    |
|-------------------------------|----------|
| Validation Macro F1           | **0.7462** |
| Kaggle Public Leaderboard     | **0.71482** |

---


> **Note:** The original dataset is not included in this repository due to size.  
> The notebook is designed to run on Kaggle with the competition data.

---

## Key Technical Highlights

- Large-scale tabular preprocessing (279K+ rows)
- Systematic missing value strategy + missingness indicators
- Meaningful temporal & behavioral feature engineering
- Gradient boosting ensemble with probability calibration
- Strong validation → leaderboard consistency

---

## How to Run

1. Open the notebook in a Kaggle environment (or local setup with the data).
2. Ensure the competition data is available at the expected path.
3. Run all cells sequentially.
4. The final model produces predictions in the required submission format.

----

## Author

Anirban Das  
BS Data Science – IIT Madras
