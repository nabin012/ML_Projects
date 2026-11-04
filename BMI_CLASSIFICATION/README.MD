# ⚖️ BMI Category Classification (Imbalanced Multi-class)

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Classification-orange?logo=scikit-learn)
![imbalanced-learn](https://img.shields.io/badge/imbalanced--learn-SMOTE-purple)

---

## 📘 Project Overview

This project predicts a person's **BMI category** from **Gender, Height (cm), and Weight (kg)**.
The target (`Index`) has 6 classes:

| Index | Category |
|---|---|
| 0 | Severely Underweight |
| 1 | Underweight |
| 2 | Normal |
| 3 | Overweight |
| 4 | Obesity |
| 5 | Severely Obese |

The dataset is **heavily imbalanced** (very few samples in classes 0–1), so the project compares resampling strategies and three classifiers: **Logistic Regression**, **KNN**, and **SVM**.

---

## 🛠️ Technologies Used

- Python, pandas, NumPy
- scikit-learn (LogisticRegression, KNeighborsClassifier, SVC, GridSearchCV)
- imbalanced-learn (RandomOverSampler, RandomUnderSampler, SMOTE)
- matplotlib, seaborn

---

## 🔍 What I Did

### 1. Exploratory Data Analysis
- Checked data types, summary statistics, and missing values (none).
- Detected outliers in Height/Weight with the **IQR method** and box plots.
- Plotted class distribution, BMI category by gender, height/weight histograms, and scatter/lm plots.
- Built **correlation heatmaps** for the full, male-only, and female-only data.
- Finding: Height and Weight are positively correlated within each BMI category; gender alone does not strongly change the BMI index.

### 2. Preprocessing
- Label-encoded `Gender`.
- 80/20 train-test split, `StandardScaler` for distance-based models.

### 3. Handling Class Imbalance (Logistic Regression)

| Strategy | Accuracy | Weighted F1 |
|---|---|---|
| No resampling | 0.85 | 0.86 |
| Random Oversampling | 0.77 | 0.78 |
| Random Undersampling | 0.74 | 0.74 |
| SMOTE | 0.77 | 0.78 |

SMOTE and oversampling beat undersampling, and they help the minority classes, even though overall accuracy drops compared with no resampling.

### 4. Models on General, Male-only, and Female-only Data

| Model | General | Male | Female |
|---|---|---|---|
| Logistic Regression | 0.87 | 0.94 | 0.84 |
| KNN (k = 5) | 0.85 | 0.90 | 0.88 |
| KNN (best k via error-rate curve) | 0.89 (k=3) | 0.92 (k=3) | 0.90 (k=1) |
| SVM (default) | 0.90 | 0.92 | 0.90 |
| **SVM + GridSearchCV** | **0.96** | **1.00** | **0.92** |

Best SVM params: `C=100, gamma='scale'`, kernel `rbf` (general & female) / `linear` (male).

---

## ✅ Key Takeaways

- **Tuned SVM was the best model** (96% accuracy on the general dataset).
- Choosing k from an error-rate curve improved KNN on all three splits.
- Splitting by gender helped the male model but the female split is small, so its scores are less stable.

## ⚠️ Limitations / Not Done Yet

- Test set is small (~100 rows), so the 100% male score is likely optimistic; cross-validated scores would be more reliable.
- Resampling was only compared with Logistic Regression, not with KNN/SVM.
- No feature engineering (e.g., computing the BMI formula directly as a feature).

---

## ▶️ How to Run

1. Download `bmi.csv` (Gender, Height, Weight, Index) — e.g. the [Kaggle 500 Person Gender-Height-Weight-BMI dataset](https://www.kaggle.com/datasets/yersever/500-person-gender-height-weight-bodymassindex).
2. Open `BMI_Classification.ipynb` in Jupyter or Google Colab and place `bmi.csv` next to it.
3. `pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn` and run all cells.
