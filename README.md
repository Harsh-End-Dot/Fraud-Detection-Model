# Fraud Detection Model 🚨
   
A machine learning-based fraud detection system built with a Random Forest Classifier to identify fraudulent financial transactions. This project tackles class imbalance and provides robust performance for fraud detection. 🕵️‍♂️

---

## 📑 Table of Contents
- [Project Overview 🌟](#-project-overview)
- [Dataset 📊](#-dataset)
- [Features 🔍](#-features)
- [Installation ⚙️](#️-installation)
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
git clone https:///github.com/yourusername/fraud-detection-repo.git
cd fraud-detection-repo
-Install dependencies
pip install -r requirements.txt
-requirements
numpy
pandas
matplotlib
seaborn
scikit-learn
imbalanced-learn
---
## 🧹 Preprocessing Steps
- **Load Data**: Using `pandas`  
- **EDA**:  
  - Summary statistics (`describe()`)  
  - Check for missing values (✅ none found)  
  - Visualize fraud distribution  
- **Feature Engineering**:  
  - Drop irrelevant columns  
  - One-hot encode `type`  
  - Standardize `amount` → `z_amount` using `StandardScaler`  
- **Train-Test Split**: 80/20 split  
- **Handle Imbalance**: Apply **SMOTE** to oversample fraud class in training data  

---

## 🤖 Model Training
- **Algorithm**: Random Forest Classifier (`n_estimators=100, random_state=42`)  
- **Training**: Fit on **SMOTE-balanced** training data  
- **Why Random Forest?**  
  - Handles non-linear relationships  
  - Provides feature importance  
  - Effective for imbalanced datasets  

ROC-AUC Score: 0.9896149688518895

Classification Report:
              precision    recall  f1-score   support
0                 1.00      1.00      1.00   1270904
1                 0.89      0.85      0.87      1620

accuracy                           1.00   1272524
macro avg          0.94      0.92      0.93   1272524
weighted avg       1.00      1.00      1.00   1272524

[[1270752    152]
 [    247   1373]]
---
## 🔝 Feature Importance

Top features contributing to fraud prediction:

| Feature        | Importance |
|----------------|------------|
| oldbalanceOrg  | 0.297      |
| z_amount       | 0.142      |
| amount         | 0.136      |
| type_TRANSFER  | 0.120      |
| type_CASH_OUT  | 0.094      |
| step           | 0.087      |
| oldbalanceDest | 0.074      |
| type_PAYMENT   | 0.050      |
| type_DEBIT     | 0.000      |
| isFlaggedFraud | 0.000      |

📊 Bar plot visualization is available in the notebook.

---

## 🎯 Results
- ✅ Detects **~85% of fraud cases** with minimal false positives  
- 💡 **Key Insight**: Fraudulent transactions often involve **TRANSFER** or **CASH_OUT** with high amounts draining originator accounts  
- ⚠️ **Limitation**: Dataset is synthetic; real-world deployment requires further validation  

**Future Improvements**:  
- Experiment with **deep learning** (e.g., Autoencoders)  
- Try ensemble methods like **XGBoost** or **LightGBM**  

---

## 🤝 Contributing
Contributions are welcome!  


