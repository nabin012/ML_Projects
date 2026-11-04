# 🛡️ AI for Cybersecurity: Detecting Malicious DNS-over-HTTPS (DoH) Traffic

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![TensorFlow](https://img.shields.io/badge/TensorFlow-CNN-orange?logo=tensorflow)
![Security](https://img.shields.io/badge/Domain-Network%20Security-darkgreen)

---

## 📘 Project Overview

**DNS-over-HTTPS (DoH)** encrypts DNS queries, which improves privacy but lets attackers hide **DNS tunneling** (e.g., data exfiltration and command-and-control with tools like `dnscat2`) inside normal-looking HTTPS traffic.

This project builds a full pipeline to tell **benign DoH traffic** (Cloudflare resolver) apart from **malicious DoH tunneling traffic (dnscat2)**: from raw packet captures, to feature engineering, to classical ML and deep learning, and finally explainability and adversarial attacks on the model.

---

## 🛠️ Technologies Used

- Python, pandas, NumPy
- **NFStream** (network flow feature extraction from `.pcap`)
- scikit-learn (Linear/Lasso Regression, Logistic Regression, Decision Tree, Random Forest)
- TensorFlow / Keras (1D CNN)
- **Trustee** (model explainability via decision-tree surrogates), Graphviz
- matplotlib, seaborn

---

## 🗂️ Notebooks

| # | Notebook | What it does |
|---|---|---|
| 01 | `01_Data_Creation.ipynb` | Converts `Doh_traffic.pcap` into flow-level features with NFStream (bytes, packets, ratios, duration, packet-size stats, delays) → `sample-features.csv` |
| 02 | `02_Dataset_Exploration.ipynb` | Compares benign vs. malicious traffic with pairplots of volume, packet-size, median/ratio, and timing features |
| 03 | `03_Linear_Regression.ipynb` | Simple, multiple, **Lasso**, and **Non-Negative Least Squares** regression to study relationships between traffic features |
| 04 | `04_Logistic_Regression.ipynb` | Binary classifier (benign vs. malicious) + **permutation feature importance** |
| 05 | `05_Decision_Tree_Random_Forest.ipynb` | Decision trees at different depths and a Random Forest |
| 06 | `06_CNN_Model.ipynb` | 1D CNN on 16 flow features; compares training settings and a new deeper architecture |
| 07 | `07_Explainability_and_Adversarial_Attack.ipynb` | Explains the CNN with **Trustee** decision-tree surrogates, then tries to **trick the CNN** by modifying a feature |

---

## 📊 Results

| Model | Accuracy | Notes |
|---|---|---|
| Lasso Regression | R² = 0.994 | Kept only 2 of 9 features (feature selection) |
| Logistic Regression | 0.9988 | `bytes_ratio` and `avgdelay` were the most important features |
| Decision Tree (depth 2 → 10) | 0.9988 → 0.9992 | Even a depth-2 tree separates the classes well; F1 = 0.999 |
| Random Forest | 1.00 | Perfect on the test split |
| 1D CNN (baseline → deeper) | val acc 0.9979 → 0.9989 | More epochs, smaller batches and a deeper architecture reduced validation loss |
| Trustee surrogate tree | fidelity 1.00 | A simple decision tree fully mimics the CNN's decisions |

### 🎯 Adversarial Attack
I took 100 malicious samples the CNN classified correctly and replaced one feature (`median_in`) with the **benign average**.
**30% of the malicious samples were then misclassified as benign**, showing that the model relies heavily on a few features and can be evaded.

---

## ✅ Key Takeaways

- Simple flow statistics (byte ratio, delays) are enough to detect DoH tunneling with ~99.9% accuracy.
- Very high accuracy does **not** mean robustness: a single-feature change fooled the CNN 30% of the time.
- Explainability tools like Trustee reveal which features the model really depends on.

## ⚠️ Limitations / Not Done Yet

- Only one tunneling tool (dnscat2) and one benign resolver (Cloudflare), so results may not generalize to other tools or resolvers.
- The full benign/malicious CSV datasets are not included in this repo (only the sample pcap and extracted features).
- No adversarial training or defense was implemented yet.

---

## ▶️ How to Run

1. Open the notebooks in order in Google Colab.
2. Install dependencies: `pip install nfstream pandas scikit-learn tensorflow matplotlib seaborn trustee graphviz`
3. Notebook 01 uses `Doh_traffic.pcap` from this folder. Later notebooks expect the benign (`normal_doh_traffic_cloudflare_server.csv`) and malicious (`dnscat2_data_4.csv`) DoH datasets uploaded to Colab.
