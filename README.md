# ML with Python - Portfolio Projects

Welcome to my machine learning portfolio! This repository showcases my journey building ML models from fundamentals through advanced techniques.

## 📚 Projects

### 1. 📊 [Decision Trees & Multiclass Classification](./1-decision-trees/)
**Status:** ✅ Complete

Comprehensive exploration of Decision Tree algorithms with two applications:
- **Handwritten Digit Classification** (10-class multiclass problem)
- **Housing Price Prediction** (Regression problem)

**Key Topics:**
- Decision Tree Classifier (multiclass)
- Decision Tree Regressor
- OvA (One-vs-All) vs OvO (One-vs-One) strategies
- Hyperparameter tuning & overfitting analysis
- Feature importance & interpretability

**Performance Highlights:**
- Digit Classification: 80.83% accuracy (Decision Tree)
- Logistic Regression OvO: 97.78% (comparison)
- Housing Regression: R² score analysis

[→ Read full project details](./1-decision-trees/dc_readme.md)

---

### 2. 📞 [Customer Churn & Revenue Analysis](./2-customer-churn/)
**Status:** ✅ Complete

Predictive analytics for telecom customer retention:
- **Churn Prediction** (Logistic Regression)
- **Revenue Prediction** (Linear Regression)

**Key Topics:**
- Binary classification with imbalanced data
- Feature engineering from categorical variables
- Model evaluation (precision, recall, F1-score)
- Business recommendations & insights

**Performance Highlights:**
- Churn Prediction: 82% accuracy
- Revenue Prediction: R² = 0.998 (99.8% variance explained)
- Precision (Churn): 69%, Recall: 60%

[→ Read full project details](./2-customer-churn/cca_readme.md)

---

### 3. 🏠 Housing Regression (In Progress)
Deeper dive into regression techniques using Decision Trees and advanced models.

---

## 🛠️ Technology Stack

```
Python 3.x
├── Data Processing: NumPy, Pandas
├── ML Algorithms: Scikit-learn
│   ├── Decision Trees (DecisionTreeClassifier, DecisionTreeRegressor)
│   ├── Logistic Regression
│   ├── Linear Regression
│   └── Multiclass strategies (OneVsRestClassifier, OneVsOneClassifier)
└── Visualization: Matplotlib, Seaborn
```

---

## 📈 Learning Journey

**Foundation Phase:**
- Linear Regression (predicting continuous values)
- Logistic Regression (binary classification, probability)

**Tree-Based Phase (Current):**
- Decision Trees (multiclass, interpretable, non-linear)
- Multiclass strategies (OvA, OvO)
- Regression with trees
- Feature importance analysis

**Advanced Phase (Next):**
- Ensemble Methods (Random Forest, Gradient Boosting)
- Neural Networks & Deep Learning
- Time Series Forecasting
- NLP & Advanced ML

---

## 📊 Quick Stats

| Project | Type | Algorithm | Best Accuracy |
|---------|------|-----------|---|
| Decision Trees | Classification | Logistic Regression OvO | 97.78% |
| Decision Trees | Classification | Decision Tree | 80.83% |
| Customer Churn | Classification | Logistic Regression | 82% |
| Revenue | Regression | Linear Regression | R²=0.998 |

---

## 🚀 How to Use

### Clone Repository
```bash
git clone https://github.com/Gab-stixx/mlwithpython.git
cd mlwithpython
```

### Install Dependencies
```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### Run Projects
```bash
# Decision Trees project
jupyter notebook 1-decision-trees/digits_classification.ipynb

# Customer Churn project
jupyter notebook 2-customer-churn/customer_churn_analysis.ipynb
```

---

## 📁 Repository Structure

```
mlwithpython/
├── README.md                              # Main overview (you are here)
├── .gitignore                             # Git ignore file
│
├── 1-decision-trees/
│   ├── digits_classification.ipynb        # Multiclass & regression project
│   └── dc_readme.md                       # Detailed project documentation
│
├── 2-customer-churn/
│   ├── customer_churn_analysis.ipynb      # Churn & revenue prediction
│   └── cca_readme.md                      # Detailed project documentation
│
└── 3-housing-regression/  (coming soon)
    ├── housing_regression.ipynb
    └── hr_readme.md
```

---

## 💡 Key Learnings Across Projects

✅ **Machine Learning Fundamentals:**
- Train-test splitting with stratification
- Hyperparameter tuning and model selection
- Overfitting vs underfitting detection
- Feature importance analysis

✅ **Multiclass Classification:**
- Native multiclass vs binary decomposition
- OvA (One-vs-All) vs OvO (One-vs-One) strategies
- Confusion matrix interpretation
- Per-class metrics (precision, recall, F1)

✅ **Regression Analysis:**
- R² score, RMSE, MAE metrics
- Residual analysis
- Feature correlation
- Linear vs non-linear relationships

✅ **Communication & Analysis:**
- Clear visualization of results
- Honest algorithm comparison
- Business insights from data
- Professional documentation

---

## 📝 Each Project Includes

Every project folder contains:
- **Jupyter Notebook** - Complete implementation with step-by-step explanations
- **README** - Detailed documentation, insights, and learnings
- **Code Comments** - Clear explanation of what each cell does
- **Visualizations** - Charts, heatmaps, confusion matrices
- **Results** - Performance metrics and analysis

---

## 🎯 Portfolio Purpose

This repository demonstrates:
- ✅ Ability to implement ML algorithms from scratch understanding
- ✅ Strong grasp of model evaluation & validation techniques
- ✅ Honest reporting (showing when other algorithms outperform)
- ✅ Clear communication of technical findings
- ✅ Progressive learning path (beginner → intermediate)

---

## 🔗 Connect

- **GitHub:** [Gab-stixx](https://github.com/Gab-stixx)
- **LinkedIn:** [Coming soon]
- **Email:** [Coming soon]

---

## 📚 Resources & References

- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Decision Trees Guide](https://scikit-learn.org/stable/modules/tree.html)
- [Multiclass Classification](https://scikit-learn.org/stable/modules/multiclass.html)
- [Model Evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html)

---

## 📜 License

This portfolio is open source and available for learning and reference purposes.

---

**Last Updated:** May 5, 2026

**Status:** Actively learning and adding new projects! 🚀
