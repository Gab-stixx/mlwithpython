# Telco Customer Churn & Revenue Prediction

A machine learning project predicting customer churn and revenue using logistic and linear regression.

## Overview

A telecom company wants to reduce customer churn and maximize revenue. This project builds two models:
- **Logistic Regression** — predicts which customers will leave
- **Linear Regression** — predicts customer monthly and total revenue

Combined, these models identify high-value customers at risk of churning, enabling targeted retention strategies.

## Dataset

[Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) — 7,043 customers with 21 features including demographics, services, account info, and churn status.

## Key Findings

### Churn Drivers (Logistic Regression)

| Feature | Impact |
|---------|--------|
| Tenure | Longer stay = less likely to churn |
| Contract type | Month-to-month customers churn significantly more |
| Monthly charges | Higher charges = higher churn risk |
| Fiber optic | Fiber optic users churn more often |
| Streaming services | Users with streaming services have higher churn |

### Revenue Prediction (Linear Regression)

- Monthly charges predicted with **R² = 0.998**, RMSE = $1.05
- Strongest predictors: tenure, contract type, and internet service

### Business Recommendation

> Target month-to-month, fiber optic customers with high monthly charges in their first year. Offer contract discounts before they churn.

## Model Performance

| Model | Metric | Score |
|-------|--------|-------|
| Logistic Regression | Accuracy | 82% |
| Logistic Regression | Precision (Churn) | 69% |
| Logistic Regression | Recall (Churn) | 60% |
| Linear Regression (Monthly) | R² | 0.998 |
| Linear Regression (Monthly) | RMSE | $1.05 |

## Tools

- Python 3
- pandas, NumPy
- scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

## Project Structure

churn-project/
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── notebooks/
│   └── analysis.ipynb
├── README.md
└── requirements.txt