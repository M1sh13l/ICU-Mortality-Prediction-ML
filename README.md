# ICU Mortality Prediction using Machine Learning

## Overview
This project develops a machine learning model to predict ICU patient mortality risk using structured clinical data. The goal is to support early identification of high-risk patients and improve clinical decision-making.

---

## Problem Statement
ICU datasets are highly imbalanced, where survival cases significantly outnumber mortality cases. Traditional models may achieve high accuracy but fail to detect critical high-risk patients.

This project focuses on:
- Handling class imbalance
- Prioritizing recall over accuracy
- Evaluating robustness under noisy data conditions

---

## Dataset
- 15,000 ICU patient records
- 24 initial features → reduced to 7 final features
- Target: `mortality_label` (0 = survived, 1 = died)

### Final Features:
- ventilation_required
- vasopressor_used
- sepsis_flag
- apache_score
- sofa_score
- comorbidity_score
- age

---

## Methodology

### Phase 1: Data Preparation
- Data cleaning
- Missing value handling
- Feature encoding and scaling

### Phase 2: EDA
- Class distribution analysis
- Feature distributions
- Correlation heatmap
- Outlier detection

### Phase 3: Baseline Models
Trained 8 classifiers:
- Logistic Regression
- Decision Tree
- Random Forest
- SVM
- KNN
- Naive Bayes
- Gradient Boosting
- XGBoost

Used cross-validation for evaluation.

### Phase 4: Model Optimization
- Feature refinement (22 → 7)
- Class imbalance handling (training set only)
- Threshold tuning (0.35, 0.40, 0.45)

### Phase 5: Robustness Testing
- Introduced 15% label noise
- Simulates real-world clinical data imperfections

---

## Results

**Best Model:** Tuned XGBoost (threshold = 0.35)

| Metric | Value |
|------|------|
| Accuracy | 58.0% |
| Precision | 55.0% |
| Recall | 88.45% |
| F1-score | 67.83% |
| ROC-AUC | 64.15% |

### Key Insight
High recall ensures that most high-risk ICU patients are correctly identified, which is critical in healthcare.

---

## Model Interpretation
Top predictors:
- vasopressor_used
- ventilation_required
- sepsis_flag

These features align with clinical indicators of severe patient conditions.

---

## Prototype
A simple interface allows:
- Input: patient clinical data
- Output:
  - mortality probability
  - predicted class
  - risk category

---

## Limitations
- Moderate ROC-AUC
- False positives due to recall prioritization
- Dataset may not represent all ICU populations

---

## Future Work
- Use real hospital data
- Add time-series features
- Improve model calibration
- Apply advanced imbalance techniques (SMOTE)

---

## Contributors
- Mashael Saeed
- Sarah Elshiaty
- Seifeldin Elshiaty

---

## License
This project is for academic purposes.
