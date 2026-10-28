# RabTech Task 6 — Digital Payments Fraud Detection

## Research question
How effectively can supervised models identify rare fraudulent transactions in an imbalanced dataset, and how does alert-threshold selection affect precision and recall?

## Dataset
Download `creditcard.csv` from the ULB / Worldline dataset on Kaggle: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
Place it at `data/raw/creditcard.csv`. The dataset is not included in this ZIP and should not be uploaded to GitHub due to its size.

## Windows / VS Code setup
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```
Open `notebooks/task6_digital_payments_fraud.ipynb`, select the `.venv` kernel, and choose **Run All**. Save with Ctrl+S.

## Workflow
Data checks, class imbalance, chronological 60/20/20 train-validation-test split, Logistic Regression and Random Forest with class weighting, validation-only threshold selection, test metrics (precision, recall, F1, average precision, ROC-AUC), confusion matrices, PR curve, and permutation importance.

## Important limitations
The dataset is historical and anonymized, not live bank data. `V1`–`V28` are PCA-transformed and lack original business meaning. Accuracy alone is misleading for rare fraud. Results do not establish production readiness. Use actual notebook results in the whitepaper; do not invent metrics.

## Deliverables
Executed notebook, requirements files, 8–12 page evidence-based PDF whitepaper, and public GitHub repository. Exclude `.venv`, caches, and the dataset CSV from GitHub.
