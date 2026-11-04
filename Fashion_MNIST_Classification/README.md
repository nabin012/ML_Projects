# 👕 Fashion-MNIST Classification: Shallow NNs vs. CNNs vs. Ensembles

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange?logo=tensorflow)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-CNN-red)

---

## 📘 Project Overview

This project classifies clothing images from the **[Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist)** dataset (Zalando): 60,000 training and 10,000 test images, 28×28 grayscale, 10 classes:

`T-shirt/top · Trouser · Pullover · Dress · Coat · Sandal · Shirt · Sneaker · Bag · Ankle boot`

It starts with simple fully connected networks, tunes them systematically, then moves to **convolutional neural networks** and finally combines models into an **ensemble / committee**.

---

## 🛠️ Technologies Used

- Python, NumPy
- TensorFlow / Keras
- scikit-learn (confusion matrix, classification report)
- matplotlib, seaborn

---

## 🔍 What I Did

### 1. Data Preparation
- Loaded the dataset with `tf.keras.datasets.fashion_mnist` and visualized sample images.
- Normalized pixels from 0–255 to 0–1 for faster, more stable training.

### 2. Shallow Neural Networks (Flatten → Dense → Softmax)
- Trained with **SGD** and **Adam** for 10 epochs: ~**85–86%** test accuracy.
- Searched learning rates `[0.0001, 0.001, 0.01, 0.1, 1.0]` for SGD.
- Compared hidden-layer sizes `(50,50)`, `(50,100)`, `(100,100)`, `(100,150)`, `(200,250)`, `(50,150,250)` with **ReLU, tanh, and LeakyReLU** activations.
- Best SGD configuration reached **~86.5%** (ReLU, 100–150 neurons).

### 3. Convolutional Neural Networks
- Built several CNNs (Conv2D + MaxPooling), including a deeper 4-layer CNN (32→64→128→256 filters).
- Added **Batch Normalization, Dropout, more filters and padding** for a more advanced model.
- CNNs reached **~90.6–91.7%** test accuracy.

### 4. Model Comparison & Ensembles
- **Model 1:** MLP with two 150-unit ReLU layers.
- **Model 2:** CNN with 3 conv layers (32/64/128 filters).
- **Model 3:** CNN with 64/128/256 filters, max pooling, and dropout.
- Combined them with averaged predictions (**ensemble**) and majority vote (**committee**).

| Model | Test Accuracy |
|---|---|
| Model 1 (MLP) | 0.886 – 0.912 |
| Model 2 (CNN) | 0.905 – 0.916 |
| Model 3 (Deeper CNN + Dropout) | 0.916 – **0.931** |
| Ensemble (averaged) | **0.927** |
| Committee (vote) | 0.911 |

*(Ranges cover two separate training runs in the notebook.)*

---

## ✅ Key Takeaways

- CNNs beat fully connected networks by about **5–6 percentage points**.
- Batch normalization and dropout helped the deeper CNN generalize best.
- Averaging predictions (ensemble) was more accurate than majority voting.
- "Shirt", "T-shirt/top", "Pullover" and "Coat" are the hardest classes to separate.

## ⚠️ Limitations / Not Done Yet

- No data augmentation was used.
- Models were trained for a small number of epochs; no learning-rate scheduling.
- Transfer learning (pretrained backbones) was not explored.

---

## ▶️ How to Run

1. Open `Fashion_MNIST_NN_vs_CNN.ipynb` in Google Colab (GPU recommended) or Jupyter.
2. `pip install tensorflow scikit-learn matplotlib seaborn`
3. Run all cells. The dataset downloads automatically through Keras.
