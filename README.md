# 🧠 Self-Pruning Neural Network (AI Engineering Case Study)

## 📌 Overview

This project implements a **Self-Pruning Neural Network** that learns to remove unnecessary weights during training.

Unlike traditional pruning (done after training), this model integrates pruning **directly into the learning process** using learnable gate parameters.

---

## 🚀 Key Features

- Custom **Prunable Linear Layer** (no use of `torch.nn.Linear`)
- Learnable **gate mechanism** for dynamic pruning
- **L1 sparsity regularization** to encourage zero weights
- Hybrid architecture (**CNN + Prunable Layers**)
- Evaluation of **accuracy vs sparsity trade-off**
- Visualization of **gate value distribution**

---

## 🏗️ Model Architecture

- Convolutional layers for feature extraction  
- Custom fully connected layers using `PrunableLinear`

### Pruning Mechanism:

- Gate ≈ 1 → weight is active  
- Gate ≈ 0 → weight is pruned  

---

## ⚙️ Working Principle

1. Each weight has a corresponding **gate parameter**  
2. Gates are passed through a **sigmoid function** (range: 0 to 1)  
3. Weights are multiplied by gates  
4. L1 regularization pushes gates toward **zero**, creating sparsity  

---

## 📉 Loss Function

- **Classification Loss**: CrossEntropyLoss  
- **Sparsity Loss**: Sum of all gate values (L1 penalty)  

---

## 🧪 Experiments

The model is trained with 4 different λ values:

| Lambda | Effect |
|--------|--------|
| 1e-5   | Minimal pruning |
| 1e-4   | Low pruning |
| 1e-3   | Moderate pruning |
| 1e-2   | Aggressive pruning |

---

## 📊 Evaluation Metrics

- **Test Accuracy (%)**  
- **Sparsity Level (%)**  

Sparsity is calculated as:

---

## 📈 Expected Results

| Lambda | Accuracy | Sparsity |
|--------|---------|----------|
| 1e-5   | High    | Very Low |
| 1e-4   | High    | Low      |
| 1e-3   | Medium  | Medium   |
| 1e-2   | Lower   | High     |

---

## 📊 Visualization

A histogram of gate values is plotted:
- Peak near **0 → successful pruning**  
- Remaining values → important weights  

---

## 🛠️ Tech Stack

- Python  
- PyTorch  
- Torchvision  
- Matplotlib  
