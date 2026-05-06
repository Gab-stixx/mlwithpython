# Housing Price Prediction with Decision Trees

## 🏠 Project Overview

Comprehensive housing price prediction project using **Decision Tree Regressor** and **Linear Regression**, demonstrating the power of tree-based models for capturing non-linear relationships in real estate data.

---

## 📊 Dataset

**California Housing Dataset (sklearn)**
- **Source:** Scikit-learn built-in dataset
- **Size:** 20,640 houses
- **Train/Test Split:** 80/20 (16,512 train / 4,128 test)
- **Target:** Median house value (in $100,000s)
- **Price Range:** $14,999 - $500,001
- **Mean Price:** $206,856

### Features (8 total)
1. **MedInc** - Median income in block group
2. **HouseAge** - Median house age in block group
3. **AveRooms** - Average number of rooms per household
4. **AveBedrms** - Average number of bedrooms per household
5. **Population** - Block group population
6. **AveOccup** - Average household occupancy
7. **Latitude** - Block group latitude
8. **Longitude** - Block group longitude

---

## 🎯 Problem Statement

**Objective:** Predict median housing prices given geographic location and housing characteristics.

**Why it matters:**
- Real estate valuation for lending/insurance
- Investment decision-making
- Market analysis & trend forecasting
- Demonstrates regression vs classification

---

## 🔧 Model Approach

### Decision Tree Regressor
**How it works:**
- Splits features recursively to minimize prediction error
- Each leaf node predicts the **average price** of training samples in that region
- Creates axis-aligned splits (good for spatial data like lat/lon)

**Parameters:**
- `max_depth=10` - Tree can be maximum 10 levels deep
- `min_samples_split=10` - Leaf needs at least 10 samples to split

### Linear Regression (Comparison)
- Assumes linear relationship between features and price
- Provides baseline for comparison
- Interpretable coefficients

---

## 📈 Model Performance

### Decision Tree Regressor Results

| Metric | Training | Test |
|--------|----------|------|
| **R² Score** | 0.8274 | 0.6818 |
| **RMSE** | $0.4804 | $0.6457 |
| **MAE** | $0.3301 | $0.4341 |
| **Tree Depth** | 10 | - |
| **Number of Leaves** | 587 | - |

**Interpretation:**
- R² = 0.6818 means model explains 68.18% of price variance on test set
- RMSE = $64,570 average prediction error (penalizes large errors)
- MAE = $43,410 average absolute error (more robust metric)
- Gap between train & test indicates slight overfitting (acceptable)

### Linear Regression Comparison

| Metric | Decision Tree | Linear Regression |
|--------|---|---|
| **R² Score** | 0.6818 | 0.5758 (+18.4% better) |
| **RMSE** | 0.6457 | 0.7456 (+15.5% better) |
| **MAE** | 0.4341 | 0.5332 (+18.5% better) |
| **Interpretability** | Feature importance | Linear coefficients |

---

## 💡 Key Insights

### 1. Feature Importance (What drives prices?)
Decision tree learns which features matter most:
- **Median Income (61.4%)** - Overwhelmingly dominant predictor
- **Average Occupancy (13.0%)** - Neighborhood density indicator
- **Latitude (8.0%)** - North-South geographic split
- **Longitude (6.7%)** - East-West geographic split
- **House Age (4.4%)** - Newer homes valued higher
- **Average Rooms (3.7%)** - More rooms = moderately higher price
- **Population (1.5%)** - Weak effect
- **Average Bedrooms (1.2%)** - Minimal effect

### 2. Non-linear Relationships
Example: High-income areas have exponential price increases, not linear.
- Decision Tree captures this ✓
- Linear Regression assumes straight line ✗

### 3. Geographic Patterns
Tree splits on latitude/longitude reveal:
- Coastal areas (high latitude/longitude) → Premium prices
- Inland areas → Moderate prices
- Each region gets its own sub-model

### 4. Residuals Analysis
- Mean residual = -0.0026 (essentially 0, perfectly unbiased) ✓
- Std Dev of residuals = 0.6457 (consistent with RMSE)
- Distribution: Nearly normal with slight right skew
- Outliers: Some high-price homes (>$400k) underpredicted
- Pattern: Random scatter around 0 (no systematic bias) ✓

---

## 📊 Visualizations Included

1. **Price Distribution**
   - Histogram: Right-skewed (expensive homes are rare)
   - Box plot: Shows median, quartiles, outliers

2. **Feature Correlations**
   - Which features correlate with price?
   - Median Income: Strongest correlation
   - Population: Weak/no correlation

3. **Actual vs Predicted**
   - Scatter plot around diagonal = good model
   - Points below line = underprediction
   - Points above line = overprediction

4. **Residuals Plot**
   - Top: Distribution of errors
   - Bottom: Errors vs predictions (should be random)

5. **Feature Importance Bar Chart**
   - Visual ranking of feature importance
   - Guides business decisions

6. **Model Comparison**
   - Side-by-side comparison of Decision Tree vs Linear Regression
   - Shows advantages of tree-based approach

---

## 🔑 Key Learnings

### Regressor vs Classifier

| Aspect | Classifier (Digits) | Regressor (Housing) |
|--------|---|---|
| **Output** | Discrete class (0-9) | Continuous value (price) |
| **Leaf Prediction** | Majority vote | Average value |
| **Error Metric** | Accuracy, Precision | RMSE, MAE, R² |
| **Example** | "This is digit 5" | "Price: $450,000" |

### Why Decision Trees > Linear Regression Here

1. **Captures non-linearity**
   - Income effect on price: exponential
   - Location effect: step changes
   - Trees handle both ✓

2. **Interpretability**
   - Feature importance directly visible
   - Geographic splits intuitive
   - Business stakeholders understand it

3. **No scaling required**
   - Tree works on raw feature values
   - Linear regression needs normalization

---

## 🚀 How to Run

### Requirements
```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### Execute Notebook
```bash
jupyter notebook housing_regression.ipynb
```

### Cells in Order
1. **Imports & Setup** - Load libraries, set random seed
2. **Load & Explore** - Download dataset, basic statistics
3. **Correlation Analysis** - Which features matter?
4. **Train-Test Split** - Prepare for modeling
5. **Train Decision Tree** - Build regressor
6. **Evaluate Metrics** - Check R², RMSE, MAE
7. **Visualize Predictions** - Actual vs Predicted plot
8. **Analyze Residuals** - Check for errors
9. **Feature Importance** - Which features matter most?
10. **Compare with Linear** - Decision Tree vs Linear Regression
11. **Summary** - Key takeaways

---

## 📈 Results Interpretation

### What the metrics mean:

**R² Score = 0.6818**
- Fraction of variance explained: 68.18%
- Model captures most price variation
- 0.50-0.70 = Good fit; 0.70+ = Excellent fit
- We're at the upper end of "good" → approaching excellent

**RMSE = $64,570** (0.6457 in $100ks)
- Root Mean Squared Error
- Penalizes large errors heavily
- Decision Tree RMSE is 13.4% lower than Linear Regression
- Typical error: ±$64k on a ~$200k house (±32%)

**MAE = $43,410** (0.4341 in $100ks)
- Mean Absolute Error  
- Average of absolute errors (more robust)
- Easier to interpret: "Predictions off by $43k on average"
- Decision Tree MAE is 18.5% lower than Linear Regression

---

## 🎓 What This Demonstrates

✅ **Technical Skills:**
- Regression modeling (continuous prediction)
- Model evaluation metrics (R², RMSE, MAE)
- Algorithm comparison (trees vs linear)
- Feature importance analysis
- Residuals analysis & diagnostics

✅ **ML Concepts:**
- Difference between classification & regression
- How trees average values at leaves
- Importance of non-linear relationships
- Trade-offs: accuracy vs interpretability

✅ **Communication:**
- Clear visualization of results
- Honest comparison with alternatives
- Business insights from data
- Professional documentation

---

## 🔄 Comparison with Previous Projects

| Project | Type | Target | Best Model |
|---------|------|--------|-----------|
| Customer Churn | Classification (Binary) | Churn: Yes/No | Logistic Regression (69% precision) |
| Digit Classification | Classification (Multiclass) | Digit 0-9 | Logistic OvO (97.78%) |
| **Housing** | **Regression** | **Price $206.8k avg** | **Decision Tree (R² = 0.682)** |

---

## 🚀 Next Steps

1. **Hyperparameter Tuning:** Test different max_depth values
2. **Cross-Validation:** 5-fold CV for robust evaluation
3. **Ensemble Methods:** Random Forest for better accuracy
4. **Feature Engineering:** Create polynomial features
5. **Outlier Analysis:** Handle luxury homes separately
6. **Geographic Analysis:** Visualize splits on actual map

---

## 📚 Key References

- [Scikit-learn Regression Guide](https://scikit-learn.org/stable/modules/regression.html)
- [Decision Trees for Regression](https://scikit-learn.org/stable/modules/tree.html#regression)
- [Evaluation Metrics for Regression](https://scikit-learn.org/stable/modules/model_evaluation.html#regression-metrics)
- [California Housing Dataset](https://inrix.com/blog/2018/02/housing/)

---

## 📝 Summary

This project demonstrates:
- Complete regression pipeline (load → explore → train → evaluate)
- How decision trees predict continuous values
- Importance of feature analysis
- Honest algorithm comparison
- Professional documentation & visualization

Perfect portfolio piece showing progression from classification to regression!

---

**Last Updated:** May 5, 2026

**Status:** ✅ Complete
