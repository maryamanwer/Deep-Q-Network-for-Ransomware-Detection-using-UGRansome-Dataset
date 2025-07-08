# 🛡️ Deep Q-Network for Ransomware Detection using the UGRansome Dataset

This project implements a Deep Q-Network (DQN)-based reinforcement learning framework to detect ransomware activity in network traffic. Using the **UGRansome dataset**, the model demonstrates high accuracy under both standard and Zero-Day conditions, showcasing its capability to generalize to unseen threats.

---

## 📂 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Experiments](#experiments)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Future Work](#future-work)
- [License](#license)

---

## 📌 Overview

Ransomware continues to be one of the most serious cyber threats. Traditional detection methods struggle with Zero-Day attacks. This research proposes a **Deep Reinforcement Learning** approach where an agent learns to classify traffic flows using Q-learning, enabling adaptive and signature-less ransomware detection.

---

## ✨ Key Features

- 🔍 **Binary and multiclass ransomware classification**
- 🚨 **Zero-Day simulation** — detects ransomware from families unseen during training
- 🧠 **Custom RL environment** that mimics real-world network traffic inspection
- 📊 **Evaluation metrics**: accuracy, confusion matrix, and Q-network loss curves
- ⚙️ **Efficient training** with experience replay and target network

---

## 📈 Dataset

- **Source**: [UGRansome Dataset on Kaggle](https://www.kaggle.com/datasets)
- Contains network flow features labeled as **benign** or from **15 ransomware families**
- Features include: protocol, flags, ports, BTC amounts, netflow bytes, and threat indicators

---

## 🧪 Methodology

1. **Preprocessing**:
   - Cleaned missing entries
   - Encoded categorical features (`Protocol`, `Flags`, `Threats`)
   - Normalized numeric features using MinMaxScaler

2. **Zero-Day Simulation**:
   - 70/30 split by ransomware family
   - Ensured test families were unseen during training

3. **Custom Environment**:
   - Agent processes one flow per step
   - Action: classify as benign (0) or ransomware (1)
   - Rewards:
     - True Positive: +1.0
     - True Negative: +0.1
     - False Positive: -0.5
     - False Negative: -1.0

4. **DQN Agent**:
   - Two hidden layers (64 neurons, ReLU)
   - Epsilon-greedy strategy
   - Experience replay
   - Target network for stable Q-learning

---

## 🔬 Experiments

| Experiment | Description | Accuracy |
|-----------|-------------|----------|
| **1** | Random 80/20 split (binary) | 96.70% |
| **2** | Zero-Day family split | 96.92% |
| **3** | Multiclass classification (16 classes) | ~60% |
| **4** | Multiclass Zero-Day open-set detection | 90.9% Unknown detection rate |

---

## 🛠️ Installation

```bash
https://github.com/maryamanwer/Deep-Q-Network-for-Ransomware-Detection-using-UGRansome-Dataset

