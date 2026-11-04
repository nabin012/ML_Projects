# 🖐️ Fingerprint Spoof (Liveness) Detection with CNNs

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange?logo=tensorflow)
![OpenCV](https://img.shields.io/badge/OpenCV-Image%20Processing-green?logo=opencv)

---

## 📘 Project Overview

Fingerprint scanners can be fooled by **fake fingerprints** made from materials like gelatin, silicone, or latex. This project trains **Convolutional Neural Networks** to classify fingerprint images as **Live** or **Spoof**, and studies how **image preprocessing** and **hyperparameters** affect performance.

- Training set: 407 images (2 classes)
- Test set: 400 images (2 classes)

It also includes an introductory image-analysis notebook covering histogram equalization, augmentation, edge detection, and blurring.

---

## 🛠️ Technologies Used

- Python, NumPy
- TensorFlow / Keras (Conv2D, BatchNormalization, Dropout, EarlyStopping, ModelCheckpoint)
- OpenCV (histogram equalization, Gaussian blur, sharpening, Canny edges)
- scikit-learn (classification report, confusion matrix)
- matplotlib, seaborn · Google Colab + Google Drive

---

## 🗂️ Notebooks

| # | Notebook | What it does |
|---|---|---|
| 01 | `01_Image_Preprocessing_Basics.ipynb` | Histogram equalization, random affine augmentation (rotation ±30°, scaling 0.8–1.2) with before/after stats, **Canny edge detection**, **Gaussian blur** |
| 02 | `02_Baseline_CNN.ipynb` | Baseline 3-block CNN with data augmentation |
| 03 | `03_Enhanced_CNN.ipynb` | Wider CNN (64 → 128 → 256 filters) with augmentation preview and best-model checkpointing |
| 04 | `04_Deeper_CNN_with_Callbacks.ipynb` | 4-block CNN with EarlyStopping + ModelCheckpoint and sample predictions |
| 05 | `05_Preprocessing_Comparison.ipynb` | Trains the same CNN on Original vs. **Histogram Equalized**, **Blurred**, and **Sharpened** images |
| 06 | `06_Hyperparameter_Tuning.ipynb` | Grid over learning rate (1e-3, 5e-4, 1e-4) × dropout (0.35, 0.50, 0.65) |
| 07 | `07_Preprocessing_x_Hyperparameter_Grid.ipynb` | Combined grid: 4 preprocessing types × 2 learning rates × 2 dropout rates |

---

## 📊 Results

| Experiment | Best Test Accuracy |
|---|---|
| Baseline CNN | 57% |
| Enhanced CNN | 65% |
| Original images (no preprocessing) | 50% |
| Histogram Equalization | 67.5% |
| Gaussian Blur | 63.75% |
| **Sharpening** | **79%** |
| Hyperparameter grid (original images) | 50% |
| Preprocessing × hyperparameter grid | 63.5% (HE, LR 1e-3, dropout 0.6) |

---

## ✅ Key Takeaways

- **Preprocessing mattered more than hyperparameters**: sharpening raised accuracy from 50% to **79%**, likely because it highlights ridge and pore detail that differs between real and fake fingers.
- On raw images, the CNN often collapsed to predicting a single class (50% accuracy) regardless of learning rate or dropout.

## ⚠️ Limitations / Not Done Yet

- The dataset is small (~800 images), which limits what a CNN trained from scratch can learn.
- Results vary between runs; the 79% sharpening result was not reproduced in the later combined grid.
- Next steps: transfer learning (e.g., MobileNet/ResNet), class-balanced sampling, and cross-validation.
- The fingerprint dataset itself is not included in this repo.

---

## ▶️ How to Run

1. Put the dataset in Google Drive as `Spoof_data/train/{live,spoof}` and `Spoof_data/test/{live,spoof}`.
2. Open a notebook in Google Colab, mount Drive, and update `BASE_PATH` if needed.
3. Run all cells (GPU runtime recommended).
