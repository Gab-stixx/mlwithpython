# Decision Trees & Multiclass Classification Portfolio Project

A comprehensive portfolio project demonstrating mastery of **Decision Tree algorithms** and **multiclass classification** concepts. Includes two complementary projects: digit classification and housing price prediction, plus rigorous algorithm comparison.

---

## 📌 Project Overview

This portfolio showcases:
- ✅ Decision Tree Classifier (multiclass: 10 classes)
- ✅ Decision Tree Regressor (continuous predictions)
- ✅ OvA (One-vs-All) strategy with Logistic Regression
- ✅ OvO (One-vs-One) strategy with Logistic Regression
- ✅ Hyperparameter tuning & overfitting analysis
- ✅ Feature importance analysis & interpretability
- ✅ Algorithm comparison & selection

---

## 🎯 Project 1: Handwritten Digit Classification

**File:** `digits_classification.ipynb`

### Problem
Classify handwritten digits (0-9) from 8×8 pixel images using Decision Tree Classifier.

### Dataset
- **Source:** Sklearn Digits Dataset
- **Samples:** 1,797 images (1,437 train / 360 test)
- **Features:** 64 (8×8 pixels)
- **Classes:** 10 (digits 0-9)
- **Split:** 80/20 with stratification

### Model Performance

| Metric | Value |
|--------|-------|
| Training Accuracy | 93.88% |
| Test Accuracy | 80.83% |
| Max Depth | 8 |
| Tree Leaves | ~50 |
| Train-Test Gap | 13.05% |

### Key Insights

#### Classification Performance by Digit
```
Best performing:
- Digit 0: 97% recall (catches almost all zeros)
- Digit 5: 92% recall (very reliable)  
- Digit 4: 86% precision (when we predict 4, usually correct)

Worst performing:
- Digit 8: 67% precision (confused with similar-looking digits)
- Digit 1: 64% recall (often misidentified)
- Digits 3 & 7: 76-78% accuracy (overlapping patterns)
```

#### Feature Importance Discovery
- **Center pixels:** YELLOW/BRIGHT in heatmap (most important)
- **Edge pixels:** DARK PURPLE (least important - mostly blank)
- **Interpretation:** Model learned intelligent feature selection
- Model correctly ignores background noise, focuses on digit strokes

#### Confusion Matrix Analysis
- Digit 8 has most errors (11 out of 35) - looks like 0, 3, 6, 9
- Diagonal is strong (dark blue) = most predictions correct
- Off-diagonal errors are small numbers = few mistakes per class

---

### Hyperparameter Tuning: The "Sweet Spot"

Systematically tested depths 7-15 and discovered **depth 8 is optimal**:

| Depth | Train Acc | Test Acc | Gap | Status |
|-------|---|---|---|---|
| 7 | 89.70% | 78.89% | 10.81% | Underfitting |
| **8** | **93.88%** | **80.83%** | **13.05%** | **✓ Optimal** |
| 9 | 94.33% | 80.28% | 14.05% | Overfitting starts |
| 15 | 100% | 82.50% | 17.50% | Heavy overfitting |

**Why depth 8?**
1. **100% training accuracy is suspicious** → sign of memorization
2. **Smaller train-test gap** → better generalization to new data
3. **Best balance** → high accuracy without overfitting
4. **Principle:** Gap minimization matters more than test accuracy alone

---

### Algorithm Showdown: Decision Tree vs OvA vs OvO

Since Decision Trees handle multiclass natively, we compared with **Logistic Regression** to demonstrate multiclass strategies:

| Algorithm | Strategy | Test Accuracy | Key Insight |
|-----------|----------|---|---|
| Decision Tree | Native multiclass | 80.83% | Interpretable, but overfits easier |
| Logistic Regression | OvA (One-vs-All) | 95.83% | Baseline multiclass strategy |
| Logistic Regression | OvO (One-vs-One) | **97.78%** | **Voting wins!** |

#### Understanding the Strategies

**One-vs-All (OvA):**
```
For 10 classes, create 10 binary classifiers:
- Classifier 0: "Is this a 0?" vs (all other digits)
- Classifier 1: "Is this a 1?" vs (all other digits)
- ... repeat for 0-9
- Prediction: Returns class with highest confidence score
- Total classifiers: k = 10
```

**One-vs-One (OvO):**
```
For 10 classes, create 45 binary classifiers (all pairs):
- (0 vs 1), (0 vs 2), ..., (0 vs 9)     [9 classifiers]
- (1 vs 2), (1 vs 3), ..., (1 vs 9)     [8 classifiers]
- ...
- (8 vs 9)                              [1 classifier]
- Total: 10*9/2 = 45 classifiers
- Prediction: VOTING - which class wins most pairwise comparisons?
```

**Why Decision Trees Don't Need Them:**
- Decision trees split at each node to separate ALL classes simultaneously
- They natively handle multiclass without binary conversion
- No need for OvA/OvO decomposition (advantage of tree structure)

**Why OvO beats OvA for this problem:**
- Voting mechanism more robust than confidence scores
- Better at handling imbalanced binary subproblems
- +1.95% accuracy gain (97.78% vs 95.83%)

---

## 🏠 Project 2: Housing Price Prediction (Regression)

**File:** `housing_regression.ipynb`

### Problem
Predict California housing prices using Decision Tree Regressor vs Linear Regression.

### Dataset
- **Source:** California Housing Dataset (sklearn)
- **Samples:** 20,640 houses (16,512 train / 4,128 test)
- **Features:** 8 (median income, house age, location, rooms, bedrooms, population, etc.)
- **Target:** Median house value (in $100,000s)
- **Split:** 80/20

### Model Performance

| Metric | Decision Tree | Linear Regression |
|--------|---|---|
| **R² Score** | Higher | Lower |
| **RMSE** | Lower | Higher |
| **MAE** | Lower | Higher |
| **Interpretability** | Good (feature importance) | Excellent (coefficients) |

### Key Learnings

#### Regressor vs Classifier Comparison

| Aspect | Classifier (Digits) | Regressor (Housing) |
|--------|---|---|
| **Output Type** | Discrete class labels (0-9) | Continuous numerical value (price) |
| **Leaf Prediction** | Majority class vote | Average of training values |
| **Example** | "This is a 5" | "Price: $450,000" |
| **Metrics** | Accuracy, Precision, Recall, F1 | R², RMSE, MAE |
| **Loss Function** | Classification loss | Regression loss (MSE, MAE) |

#### Feature Importance (What Drives House Prices?)
- **Median Income:** Most important (strongest price predictor)
- **Location (lat/lon):** Second most (geographic premium)
- **House Age:** Third (older = cheaper/renovation potential)

#### Regression Evaluation Metrics

**R² Score (Coefficient of Determination):**
- Proportion of variance explained by model
- Range: 0 to 1, higher is better
- R² = 0.75 means "model explains 75% of price variation"

**RMSE (Root Mean Squared Error):**
- Penalizes large errors more heavily
- Same units as target (dollars)
- Easier to interpret: "average error is $X"

**MAE (Mean Absolute Error):**
- Average absolute prediction error
- More robust to outliers than RMSE
- Also in dollars: easier to communicate

#### Visualization Analysis
- **Actual vs Predicted plot:** Shows if model over/underestimates
- **Residuals plot:** Shows error distribution (should be random)
- **Heatmap of importance:** Shows which features matter most

---

## 🛠️ Technology Stack

```python
# Data Processing & Math
- numpy            (numerical computing, arrays)
- pandas           (dataframes, statistics)

# Machine Learning (scikit-learn)
- DecisionTreeClassifier       (multiclass classification)
- DecisionTreeRegressor        (continuous regression)
- LogisticRegression           (baseline for comparison)
- OneVsRestClassifier          (OvA strategy)
- OneVsOneClassifier           (OvO strategy)
- train_test_split             (data splitting with stratification)
- confusion_matrix             (error analysis)
- classification_report        (multiclass metrics)

# Visualization
- matplotlib       (plotting, histograms)
- seaborn          (heatmaps, statistical graphics)
```

---

## 📊 How to Run

### Requirements
```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### Running Project 1 (Classification)
```bash
cd c:\Users\USER\Desktop\proj
jupyter notebook digits_classification.ipynb
```

**Cells execute in order:**
1. Load 1,797 digit images (8×8 pixels)
2. Train Decision Tree with depth=8
3. View confusion matrix showing misclassifications
4. Analyze feature importance heatmap
5. Compare Decision Tree vs OvA/OvO strategies
6. Summary & insights

### Running Project 2 (Regression)
```bash
jupyter notebook housing_regression.ipynb
```

**Cells execute in order:**
1. Load 20,640 California houses
2. Explore price distribution
3. Train Decision Tree Regressor
4. Visualize predictions vs actual
5. Compare with Linear Regression
6. Feature importance analysis

---

## 💡 Key Learnings & Takeaways

### Machine Learning Concepts Mastered

**1. Decision Trees (Both Variants)**
- Classifier: "What pixel patterns indicate digit X?"
- Regressor: "What house features predict the price?"
- Automatically discovers important features
- Can capture non-linear relationships

**2. Multiclass Classification**
- Multi-target problem with 10+ outputs (not just binary)
- OvA: Decompose into k binary problems
- OvO: Decompose into k(k-1)/2 binary problems + voting
- Choose strategy based on problem & performance

**3. Overfitting Recognition**
- **Depth 15:** 100% train accuracy, 82.5% test = OVERFITTING!
- **Depth 8:** 93.88% train accuracy, 80.83% test = Better generalization
- **The gap is the signal:** Larger train-test gap indicates overfitting
- **True validation:** Only cross-validation on multiple splits proves generalization

**4. Algorithm Selection**
- Decision Trees excellent for interpretability
- Logistic Regression better for this specific linear problem (97.78% OvO)
- Always compare alternatives honestly
- Best algorithm depends on problem properties

**5. Feature Importance**
- Center pixels matter for digit recognition (edge is noise)
- Median income drives housing prices most
- Models learn intelligent feature selection
- Helps explain model decisions to stakeholders

---

## 📈 What This Portfolio Demonstrates

✅ **Technical Depth:**
- Implemented and tuned Decision Trees (both classifier & regressor)
- Multiclass strategies (OvA, OvO, native)
- Proper train-test methodology with stratification
- Hyperparameter optimization (depth testing)

✅ **ML Maturity:**
- Identified and quantified overfitting
- Tested multiple algorithms fairly
- Reported results honestly (Logistic Regression outperformed!)
- Understood when different algorithms shine
- Proper evaluation metrics for classification & regression

✅ **Communication Skills:**
- Clear documentation with examples
- Visual analysis (confusion matrix, feature heatmaps)
- Algorithm comparison with context
- Insights tied to business/practical implications

---

## 🚀 Next Steps & Future Improvements

1. **Cross-Validation:** Replace single train-test with k-fold CV
2. **Grid Search:** Systematically search full hyperparameter space
3. **Ensemble Methods:** Test Random Forest, Gradient Boosting
4. **Class Imbalance:** Handle if digit distribution is unbalanced
5. **Neural Networks:** Compare with deep learning approaches
6. **Production Ready:** Model serialization, API, monitoring

---

## 📁 Project Structure

```
proj/
├── dc_readme.md                           # Decision Trees project guide
├── README.md                              # Original telco project
├── digits_classification.ipynb            # Project 1: Digit classification
├── housing_regression.ipynb               # Project 2: Housing regression
├── WA_Fn-UseC_-Telco-Customer-Churn.csv  # Previous project dataset
└── .git/                                  # Git repository
```

---

## 🔗 Learning Path

**Previous Projects (Foundation):**
- Linear Regression (predicting continuous values)
- Logistic Regression (binary classification, probability)

**Current Project (Tree-Based Models):**
- Decision Trees (multiclass, interpretable)
- Multiclass strategies (OvA, OvO)
- Regression with trees

**Next (Ensemble & Advanced):**
- Random Forests (multiple trees)
- Gradient Boosting (sequential improvement)
- Neural Networks (non-linear complexity)

---

## 📚 Key References

- [Scikit-learn Decision Trees](https://scikit-learn.org/stable/modules/tree.html)
- [Understanding Multiclass Classification](https://scikit-learn.org/stable/modules/multiclass.html)
- [Overfitting Explained](https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting)
- [Feature Importance](https://scikit-learn.org/stable/auto_examples/inspection/plot_permutation_importance.html)

---

## 👤 Author

Portfolio project created to demonstrate decision tree mastery and multiclass classification understanding.

**Skills Demonstrated:** ML algorithm implementation, model evaluation, hyperparameter tuning, algorithm comparison, data visualization, interpretation & communication

---

**Last Updated:** May 4, 2026