# Deep Learning–Driven Anomaly Detection for Web-Based Intrusions

This repository provides the official implementation and supporting resources for the research paper:

**“A Deep Learning–Driven Anomaly Detection Model for Web-Based Intrusions Using Autoencoders”**

The project explores an unsupervised intrusion detection framework that leverages deep autoencoders to identify web-based cyberattacks without relying on labeled attack data. By learning the latent structure of benign network traffic, the model detects anomalous and zero-day attacks through reconstruction error deviations.

---

## 🔍 Overview

Web applications remain a primary target for modern cyberattacks such as SQL injection, cross-site scripting (XSS), and brute-force authentication attempts. Traditional intrusion detection systems (IDS) often depend on signature-based or supervised learning techniques, which struggle to generalize to previously unseen or zero-day attacks.

This project proposes a **fully unsupervised, anomaly-based IDS** using a deep autoencoder trained exclusively on benign traffic from the **CIC-IDS2017** dataset. Any significant deviation from normal reconstruction behavior is flagged as a potential intrusion.

---

## ✨ Key Features

- Fully **unsupervised anomaly detection** (no labeled attack data required)
- Deep **symmetric autoencoder** implemented in PyTorch
- Trained solely on **benign web traffic**
- Reconstruction-error–based anomaly scoring
- Validation-driven threshold selection
- Evaluation using:
  - Accuracy, Precision, Recall, F1-score
  - ROC Curve
  - Confusion Matrix
- Designed for **zero-day and unseen web attack detection**

---

## 🧠 Model Architecture

The implemented autoencoder is a fully connected, symmetric neural network:

**Encoder:**  
80 → 64 → 32 → 16  

**Latent Space:**  
16-dimensional compressed representation  

**Decoder:**  
16 → 32 → 64 → 80  

- Activation: ReLU (hidden layers), Linear (output layer)
- Loss Function: Mean Squared Error (MSE)
- Optimizer: Adam

Anomalies are detected when the reconstruction error exceeds a predefined threshold.

---

## 📊 Dataset

- **Dataset:** CIC-IDS2017  
- **Source:** Canadian Institute for Cybersecurity (CIC)
- **Features:** 80 statistical flow-based features
- **Training Data:** Benign web traffic only
- **Evaluation Data:** Mixed benign + attack traffic

### Preprocessing Steps
- Removal of missing and corrupted samples
- Dropping non-numeric and identifier fields
- Min–Max normalization
- Binary labeling for evaluation (Normal vs Anomaly)
- Data split: 80% train, 10% validation, 10% test

---

## 🧪 Experimental Results

| Model | Accuracy | Precision | Recall | F1-score |
|------|---------|-----------|--------|----------|
| Random Forest (Supervised) | ~99% | ~99% | ~99% | ~99% |
| KNN (Supervised) | ~98% | ~98% | ~99% | ~98% |
| **Autoencoder (Proposed)** | **~80%** | **~79%** | **~78%** | **~78.5%** |

While supervised models achieve higher accuracy on known attacks, the proposed autoencoder generalizes better to **novel and zero-day threats**, making it more suitable for real-world dynamic environments.

---
