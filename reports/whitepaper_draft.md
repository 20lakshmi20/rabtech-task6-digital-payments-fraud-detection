# Research Whitepaper Draft — Digital Payments Fraud Detection

> TEMPLATE ONLY: Replace every bracketed placeholder with actual notebook results before submitting. Do not invent metrics.

## Title
**Evaluating Imbalanced Machine-Learning Models for Digital Payment Fraud Detection: A Reproducible Benchmark Study**

## Abstract
This study compares Logistic Regression and Random Forest for identifying rare fraudulent transactions. It uses a chronological train/validation/test split, class-weighted learning, validation-only threshold selection, and metrics suited to rare-event detection. [Insert actual row counts, best model, test average precision, precision, recall, F1 and key conclusion after running the notebook.]

## 1. Introduction and Research Question
Digital-payment fraud detection is a rare-event classification problem. A classifier can have high accuracy by predicting the majority class while detecting few or no fraud cases. This study asks: How effectively can supervised models identify rare fraudulent transactions, and how does threshold selection affect precision and recall?

## 2. Literature Background
The ULB / Worldline dataset hosted on Kaggle contains anonymized transactions from European cardholders in September 2013. Its published description reports 284,807 transactions and 492 fraud cases (about 0.172%). `V1`–`V28` are PCA-transformed to protect confidential information; `Time` and `Amount` are also supplied. This is a benchmark, not a live banking feed.
Prior work investigates sampling and feature extraction for imbalanced fraud data (Salekshahrezaee, Leevy, & Khoshgoftaar, 2023). A systematic review also discusses evaluation under original class imbalance (Computers, 2025). This project reports its own independent experimental results.

## 3. Data and Methodology
### 3.1 Data source
[Insert actual downloaded dataset version/date and notebook row/column counts.] Target: `Class` (1 = fraud, 0 = legitimate).

### 3.2 Data quality
[Report actual missing values and duplicate counts. Explain any cleaning decisions.]

### 3.3 Split design
Sort by `Time`; use earliest 60% for training, next 20% for validation, and final 20% for testing. Use validation only to choose a decision threshold. Reserve test data for final evaluation.

### 3.4 Preprocessing and models
Standardize `Time` and `Amount` using training-only preprocessing. Use `V1`–`V28` as provided. Compare class-weighted Logistic Regression and Random Forest.

### 3.5 Metrics
Report precision, recall, F1, average precision (PR-AUC summary), ROC-AUC, confusion matrix, and threshold. Accuracy is secondary because of class imbalance.

## 4. Results
### 4.1 Dataset profile
[Insert actual row count, fraud count, legitimate count, fraud percentage, missing values and duplicates.]

### 4.2 Model comparison
[Insert the actual test_results.csv table from notebook output.]

### 4.3 Threshold and confusion matrix
[Insert the validation-selected threshold and held-out test precision/recall, true positives, false positives, false negatives and true negatives.]

### 4.4 Feature importance
[Insert top permutation-importance features. V1–V28 are anonymized PCA components and cannot be mapped directly to business meanings.]

## 5. Discussion
[Interpret actual results. Explain the precision–recall trade-off, false-alert workload and missed-fraud risk. Do not claim superiority unless supported by test results.]

## 6. Business Implications
A production system must balance missed fraud, false declines and analyst review capacity. The appropriate threshold depends on institution-specific costs and operational requirements. This dataset does not provide reliable bank-loss estimates; do not invent savings figures. Real deployment requires institution-specific validation, secure data handling, monitoring, human oversight and an appeal process.

## 7. Limitations and Ethics
The dataset is historical and covers a short period. Most features are anonymized PCA components. The data do not represent all current digital payments or contain live device/location context. A single chronological split does not prove generalization. False positives can inconvenience legitimate customers, while false negatives can cause financial harm. The model is not a live bank integration.

## 8. Conclusion
[Summarize the best model by the chosen primary metric, the observed precision–recall trade-off, and what further validation is needed.]

## References
1. Machine Learning Group, ULB, and Worldline. *Credit Card Fraud Detection* dataset. Kaggle. https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
2. Salekshahrezaee, Z., Leevy, J. L., & Khoshgoftaar, T. M. (2023). The effect of feature extraction and data sampling on credit card fraud detection. *Journal of Big Data, 10*, 6. https://doi.org/10.1186/s40537-023-00684-w
3. *A Systematic Review of Machine Learning in Credit Card Fraud Detection Under Original Class Imbalance*. *Computers, 14*(10), 437 (2025). https://www.mdpi.com/2073-431x/14/10/437
