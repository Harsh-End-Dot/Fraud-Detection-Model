# Fraud Detection Model 🚨
   
A machine learning-based fraud detection system built with a Random Forest Classifier to identify fraudulent financial transactions. This project tackles class imbalance and provides robust performance for fraud detection. 🕵️‍♂️

---

## 📑 Table of Contents
- [Project Overview 🌟](#-project-overview)
- [Dataset 📊](#-dataset)
- [Features 🔍](#-features)
- [Installation ⚙️](#️-installation)
- [Usage 🚀](#-usage)
- [Preprocessing Steps 🧹](#-preprocessing-steps)
- [Model Training 🤖](#-model-training)
- [Evaluation 📈](#-evaluation)
- [Feature Importance 🔝](#-feature-importance)
- [Results 🎯](#-results)
- [Contributing 🤝](#-contributing)
- [License 📜](#-license)

---

## 🌟 Project Overview
This repository contains a Jupyter Notebook (**fraud_detection.ipynb**) that builds a fraud detection model for financial transactions.  
The goal is to classify transactions as fraudulent (`isFraud=1`) or non-fraudulent (`isFraud=0`) using supervised learning.

**Key Highlights:**
- Dataset Size: **6,362,620 transactions**
- Class Imbalance: **~0.13% fraudulent transactions** (handled with SMOTE)
- Model: **Random Forest Classifier**
- Performance: **~99.95% accuracy** with strong precision/recall for fraud cases
- Environment: **Google Colab with Python 3**

This project showcases **data exploration, preprocessing, model training, and evaluation** for imbalanced classification tasks. 🚀

---

## 📊 Dataset
The dataset (`Fraud.csv`) is a synthetic financial transaction log, simulating payment systems.  

**Columns:**
- `step`: Time unit (e.g., hour)  
- `type`: Transaction type (CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER)  
- `amount`: Transaction amount  
- `nameOrig`: Originator's account name  
- `oldbalanceOrg`: Originator's balance before transaction  
- `newbalanceOrig`: Originator's balance after transaction  
- `nameDest`: Recipient's account name  
- `oldbalanceDest`: Recipient's balance before transaction  
- `newbalanceDest`: Recipient's balance after transaction  
- `isFraud`: Fraud flag (1 = fraud, 0 = legitimate)  
- `isFlaggedFraud`: Flag for large transfers (>200,000) attempting to empty accounts  

**Fraud Distribution:**
- Non-Fraud: **6,354,407 (99.87%)**
- Fraud: **8,213 (0.13%)**

📌 Source: Loaded from Google Drive in the notebook (replace with your dataset path).  
⚠️ Dataset not included in repo due to size (~500MB). Download from sources like **PaySim Fraud Dataset**.  

**Visualizations in notebook:**
- Transaction type distribution 📉  
- Fraud occurrences by transaction type 📊  

---

## 🔍 Features
**Processed Features:**
- Numerical: `step`, `amount`, `oldbalanceOrg`, `oldbalanceDest`, `isFlaggedFraud`, `z_amount` (standardized amount)  
- Categorical: One-hot encoded `type` (e.g., `type_CASH_OUT`, `type_TRANSFER`)  

**Dropped:**
- `nameOrig`, `nameDest`, `newbalanceOrig`, `newbalanceDest` (redundant/irrelevant)  

---

## ⚙️ Installation

Clone the repository:
```bash
git clone https://github.com/yourusername/fraud-detection-repo.git
cd fraud-detection-repo
