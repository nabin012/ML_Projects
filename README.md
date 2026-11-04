# 🤖 Machine Learning Projects

A collection of my machine learning and deep learning projects, from classic regression and classification to computer vision and AI for cybersecurity. Each folder has its own notebooks and a README explaining what I did, the results, and what's left to improve.

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep%20Learning-orange?logo=tensorflow)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green?logo=opencv)

---

## 📂 Projects

| Project | Type | Highlights | Best Result |
|---|---|---|---|
| [🛡️ DoH Malicious Traffic Detection](./DoH_Malicious_Traffic_Detection) | Cybersecurity · Classification | Packet capture → flow features (NFStream), Logistic Regression, Decision Tree, Random Forest, 1D CNN, Trustee explainability, adversarial attack | 99.9% accuracy; attack fooled CNN 30% of the time |
| [🖐️ Fingerprint Spoof Detection](./Fingerprint_Spoof_Detection) | Computer Vision · CNN | Live vs. fake fingerprints, image preprocessing comparison, hyperparameter grids | 79% with sharpening |
| [👕 Fashion-MNIST Classification](./Fashion_MNIST_Classification) | Deep Learning · Image Classification | Shallow NN tuning (optimizers, layers, activations), CNNs, ensembles | 93.1% (CNN), 92.7% (ensemble) |
| [💳 Credit Card Fraud Detection](./Credit_Card_Fraud_Detection) | Imbalanced Classification | Undersampling, SVM vs. KNN vs. Random Forest | 93% accuracy, 0.99 precision (RF) |
| [⚖️ BMI Classification](./BMI_CLASSIFICATION) | Imbalanced Multi-class | SMOTE / over- / under-sampling, Logistic Regression, KNN, tuned SVM | 96% (tuned SVM) |
| [🏡🐟 Regression Implementation](./Regression%20Implementation) | Regression | California Housing & Fish weight with Linear, Ridge, Lasso, OLS | R² / MSE comparison |

---

## 🛠️ Tech Stack

**Languages & data:** Python · pandas · NumPy
**Machine learning:** scikit-learn · imbalanced-learn · statsmodels
**Deep learning:** TensorFlow / Keras
**Computer vision:** OpenCV
**Security tooling:** NFStream · Trustee
**Visualization:** matplotlib · seaborn
**Environment:** Jupyter · Google Colab

---

## ▶️ Running the Notebooks

Most notebooks were written in **Google Colab**. Open any `.ipynb` file in Colab, install the libraries listed in that project's README, and add the dataset described there.
