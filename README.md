# Machine_Learning
# 📊 Machine Learning Model Results and Performance Comparison

In this analysis, the following preprocessing steps were applied:
- Removed the "Label" column and company names,
- Extracted the first two digits from the SIC code,
- Kept the state name as a categorical feature,
- Used all available numerical features.

The data was split using a **time-based split** (based on year and quarter) into:
- **Training set**: 2009–2022  
- **Test set**: 2023–2025  

The models evaluated include:
- **Linear Regression**
- **Ridge Regression (α=1)**
- **Random Forest**
- **XGBoost** *(only if it ran efficiently)*

### 📋 Model Performance Comparison

> **Note**: Higher R² and lower RMSE, MAE, MAPE indicate better performance.

| Model                    | RMSE         | MAE          | MAPE      | R²     | Training Time (sec) |
|--------------------------|--------------|--------------|-----------|--------|----------------------|
| Linear Regression        | 7.38×10⁹     | 4.68×10⁹     | ~46413%   | 0.40   | 0.40                 |
| Ridge Regression (α=1)   | 7.38×10⁹     | 4.68×10⁹     | ~46100%   | 0.40   | 0.13                 |
| Random Forest            | 2.78×10⁹     | 3.31×10⁸     | ~2113%    | 0.915  | 2.64                 |

---

### 📝 Notes:

- The **very high MAPE values** are due to the presence of **zero or negative net income** in some records, which leads to extremely high percentage errors.
- **Random Forest**:
  - Achieved the **lowest error metrics** (RMSE, MAE),
  - Provided the **highest R² score** on the test set (0.915),
  - Shows signs of **overfitting** (Training R² ≈ 0.988).
- **Linear and Ridge Regression**:
  - Lower prediction accuracy,
  - But **extremely fast training times**,
  - Similar R² scores for training and test sets suggest **minimal overfitting**.

### 🔐 Data Leakage Considerations:

- **No data leakage** was detected because a **temporal split** was used and no future data was leaked into the training set.

### 🏆 Conclusion:

- **Best-performing model (accuracy-wise):** Random Forest — *lowest RMSE and MAE, highest R²*  
- **Fastest models:** Linear and Ridge Regression — *very short training time*

> Although XGBoost was tested, it was excluded from the table due to long execution time in the given environment. Final conclusions are based on the models listed above.

---

### 📚 References:

The results presented are based solely on the given dataset and independently computed metrics. No external sources were used for numerical benchmarks. Definitions of metrics and discussions on overfitting and data leakage are based on standard machine learning practices.
