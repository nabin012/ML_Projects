# 💳 Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Classification-orange?logo=scikit-learn)

---

## 📘 Project Overview

This project detects fraudulent credit card transactions using the **[Kaggle Credit Card Fraud dataset (ULB)](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)**: 284,807 European card transactions, of which only **492 are fraud (~0.17%)**. Features `V1–V28` are PCA-transformed, plus `Time` and `Amount`.

Because the data is so imbalanced, a model that always predicts "legit" would look 99.8% accurate, so the data is balanced before training.

---

## 🛠️ Technologies Used

- Python, pandas, NumPy
- scikit-learn (SVC, KNeighborsClassifier, RandomForestClassifier)
- matplotlib, seaborn

---

## 🔍 What I Did

### 1. Exploration
- Inspected the data, checked for missing values, and compared the class counts (legit vs. fraud).
- Compared transaction `Amount` statistics and feature means for legit vs. fraud transactions.

### 2. Balancing with Undersampling
- Randomly sampled **492 legit transactions** to match the 492 frauds, giving a balanced dataset of 984 rows.
- Split 80/20 with stratification.

### 3. Models

| Model | Accuracy | Precision (fraud) | Recall (fraud) | F1 (fraud) |
|---|---|---|---|---|
| SVM (linear kernel) | 0.90 | 1.00 | 0.81 | 0.89 |
| KNN (k = 5) | 0.62 | 0.61 | 0.65 | 0.63 |
| **Random Forest** | **0.93** | **0.99** | **0.88** | **0.93** |

Random Forest also scored a **Matthews Correlation Coefficient of 0.87**. I plotted confusion matrices and an ROC curve for the Random Forest.

---

## ✅ Key Takeaways

- **Random Forest performed best**, with very few false alarms and 88% of frauds caught.
- KNN performed poorly because the features were not scaled and it is sensitive to feature magnitude.

## ⚠️ Limitations / Not Done Yet

- Undersampling throws away >99% of legit transactions; SMOTE or class weights on the full data would be a fairer test.
- Models were evaluated on a balanced test set, not the real-world 0.17% fraud rate.
- Features were not scaled before KNN/SVM, and no hyperparameter tuning was done.

---

## ▶️ How to Run

1. Download `creditcard.csv` from [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud).
2. Open `credit_card_fraud_detection.ipynb` in Google Colab and update the CSV path in the loading cell.
3. Run all cells.
