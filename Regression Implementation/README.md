
# 🏡🐟 Machine Learning Regression Analysis on California Housing and Fish Datasets

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Regression-orange?logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 🛠️ Technologies Used

- Python 3.10+
- pandas, NumPy
- scikit-learn
- matplotlib, seaborn
- statsmodels

---

## 📊 California Housing Dataset

### 🔍 Task 1: Data Exploration & Preprocessing

- Visualized target and features using:
  - Histograms
  - Box Plots
  - Scatter Plots
- Detected outliers and examined correlations.
- **Feature Scaling**: StandardScaler used for normalization before training models.

### 🤖 Task 2: Regression Models Implemented

- Simple Linear Regression  
- Multiple Linear Regression  
- Ridge Regression  
- Lasso Regression  
- OLS (via `statsmodels`)

### 📈 Evaluation Metrics

- R² Score  
- Mean Squared Error (MSE)

> ✅ Regularized models (Ridge & Lasso) helped in controlling overfitting and improved generalization.

---

## 🐟 Fish Dataset

### 🔍 Task 1: Linear Regression

**Objective:** Predict fish weight using length, height, and width.

Computed:
- Regression coefficients using Least Squares Estimation  
- R² and standard error of estimates

### 🧠 Task 2: Ridge & Lasso Regression

- Applied regularization to handle feature correlation  
- Compared coefficients and error terms with standard Linear Regression

---

## 📈 Summary of Results

| Model  | Dataset     | R² Score | MSE     | Notes                           |
|--------|-------------|----------|---------|----------------------------------|
| Linear | California  | 0.xx     | xxx.xx  | Baseline model                  |
| Ridge  | California  | 0.xx     | xxx.xx  | Reduced overfitting             |
| Lasso  | California  | 0.xx     | xxx.xx  | Feature selection behavior      |
| OLS    | California  | 0.xx     | xxx.xx  | Statistical analysis included   |
| Linear | Fish        | 0.xx     | xxx.xx  | Uses 3 features                 |
| Ridge  | Fish        | 0.xx     | xxx.xx  | Regularized regression          |
| Lasso  | Fish        | 0.xx     | xxx.xx  | Drives some coefficients to zero |

> 📝 Replace placeholder values (0.xx, xxx.xx) with your actual results.

---

## 💻 How to Run the Project

### 1. Clone the repository
```bash
git clone https://github.com/your-username/regression-analysis.git
cd regression-analysis
