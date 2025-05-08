# 🏡🐟 Regression Analysis Using California Housing and Fish Datasets

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Regression-orange?logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📘 Project Overview

This project involves implementing various regression models on two datasets:

- **[California Housing Dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)** to predict median house values.
- **[Fish Dataset](https://www.kaggle.com/datasets/aungpyaeap/fish-market)** to predict fish weight based on physical measurements.

The models implemented include **Linear Regression**, **Ridge Regression**, **Lasso Regression**, and **Ordinary Least Squares (OLS)**. Performance was evaluated using **R² Score** and **Mean Squared Error (MSE)**.

---

## 🛠️ Technologies Used

- Python 3.10+
- pandas, NumPy
- scikit-learn
- matplotlib, seaborn
- statsmodels

---

## 🏡 California Housing Dataset

### 🔍 What I Did

- Performed exploratory data analysis (EDA) with histograms, box plots, and scatter plots to understand feature distributions and relationships.
- Identified outliers and investigated correlations between variables.
- Scaled features using `StandardScaler` to prepare data for regression models.

### 🤖 Models Applied

- Implemented:
  - Simple Linear Regression (single feature)
  - Multiple Linear Regression (all features)
  - Ridge Regression
  - Lasso Regression
  - OLS Regression using `statsmodels`

- Evaluated each model using:
  - **R² Score**
  - **Mean Squared Error (MSE)**

- Compared models to understand the impact of regularization. Ridge and Lasso improved generalization and reduced overfitting compared to basic linear models.

---

## 🐟 Fish Dataset

### 🔍 What I Did

- Built a linear regression model to predict fish weight using features: **length, height, and width**.
- Calculated coefficients using standard **Least Squares Estimation**.
- Reported **R² score** and **standard error** of the coefficients.

- Applied **Ridge** and **Lasso** regression to improve robustness and handle multicollinearity.
- Compared results with standard linear regression to assess model stability and feature impact.


