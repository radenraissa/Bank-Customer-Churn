# 🏦 Bank Customer Churn Analysis & Prediction

An end-to-end Data Analytics and Machine Learning project that analyzes customer churn behavior and predicts customers who are likely to leave a bank.

The project covers the complete analytics pipeline, from data preprocessing and exploratory analysis to dashboard development and predictive modeling. A key part of this project was catching `Complain` as a data leakage feature, it matched the target 99.86% of the time, which would have inflated model performance to ~99% without reflecting anything a bank could realistically predict in advance. After removing it, RandomForest and XGBoost were tuned and compared under an identical setup (same resampling, same cross-validation folds, same threshold-tuning procedure) to make sure the final model choice was a fair one rather than an artifact of mismatched pipelines.

---

## 📌 Project Overview

This project aims to:

- Analyze customer churn behavior using Business Analytics.
- Build an interactive dashboard for business insights.
- Develop machine learning models to predict customer churn.

---

## 📂 Repository Structure

```
.
├── data/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── data-preprocessing.ipynb
├── business-analytics.ipynb
├── churn-prediction.ipynb
├── Customer Churn Analytical Dashboard.png
├── README.md
└── .gitignore
```

---

## 🔄 Project Workflow


![Project Pipeline](images/Pipeline.png)

---

## 🛠️ Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- XGBoost
- Imbalanced-Learn (SMOTE)
- Looker Studio

---

### BA Dashboard

(https://datastudio.google.com/reporting/e4d5658f-16e7-48f2-b7ee-75a632208d54)

---

## 🤖 Machine Learning

Two ensemble learning algorithms were developed and compared.

### Models

- Random Forest
- XGBoost


## 📈 Model Performance

| Model | Accuracy | Macro F1 |
|---|---|---|
| Baseline Random Forest | 0.8695 | 0.7606 |
| Best Random Forest (thr=0.5) | 0.8555 | 0.7683 |
| Best Random Forest (tuned thr) | 0.8555 | 0.7683 |
| Best XGBoost (thr=0.5) | 0.8640 | **0.7786** |
| Best XGBoost (tuned thr) | 0.8415 | 0.7689 |

**Best model: XGBoost (default threshold = 0.5)** — 0.864 accuracy / 0.7786 macro F1.

Threshold tuning (searching for the decision cutoff that maximizes macro F1 on a held-out validation set) was tested for both models. It made no difference for Random Forest and slightly *hurt* XGBoost's test performance — a sign the "optimal" threshold was partly fitting noise in the validation split rather than a pattern that generalizes. The default threshold (0.5) was kept for the final model as the more reliable choice.

---


## 📁 Dataset

The dataset contains information from 10,000 bank customers, including:

- CustomerId
- CreditScore
- Geography
- Gender
- Age
- Tenure
- Balance
- NumOfProducts
- HasCrCard
- IsActiveMember
- EstimatedSalary
- Exited
- Complain
- SatisfactionScore
- CardType
- PointEarned

---
