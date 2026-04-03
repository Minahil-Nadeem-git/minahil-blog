---
title: "Loan Approval Prediction Using Random Forest Classifier"
date: 2026-04-02
categories: [Machine Learning]
tags: [python, scikit-learn, random-forest, analysis]
math: true
mermaid: true
layout: post
comments: true
toc: true
image:
  path: https://github.com/user-attachments/assets/43937498-47c4-466a-8e61-2df6da74085a
  alt: SQL Database
---


This post presents a comprehensive machine learning project for loan approval prediction, focusing on data preprocessing, feature engineering, and classification using a Random Forest model.

<!--more-->

# 💼 Loan Approval Prediction using Random Forest

## 📌 Project Overview
Automating loan eligibility is a critical task for financial institutions.  

In this project, I developed a **machine learning pipeline** to predict loan approvals based on applicant profiles. The model uses a **Random Forest Classifier** to evaluate factors such as:

- Credit history  
- Income  
- Employment status  

This helps determine whether a loan should be approved or not.

---

## 🛠️ Technical Stack

The project was built using the Python data science ecosystem:

- **Data Manipulation:** `pandas`  
- **Data Visualization:** `matplotlib`, `seaborn`  
- **Machine Learning:** `scikit-learn`  

---

## 📊 Data Processing Workflow

### 🔹 1. Data Cleaning & Imputation
Real-world data often contains missing values. These were handled using:

- **Categorical Features:** Mode  
  - `gender`, `married`, `dependents`, `self_employed`  

- **Numerical Features:** Median  
  - `loanamount`, `loan_amount_term`  

- **Credit History:** Mode (most frequent value)

---

### 🔹 2. Feature Engineering

To prepare the dataset for modeling:

- **Removed Irrelevant Data:**  
  - Dropped `loan_id` (no predictive value)

- **Label Encoding:**  
  - Converted `loan_status` into numeric format  

- **One-Hot Encoding:**  
  - Applied `pd.get_dummies()` to categorical variables  

---

## 🤖 Model Development

A **Random Forest Classifier** was selected due to:

- High accuracy  
- Resistance to overfitting  
- Ability to handle non-linear relationships  

```python
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_train, y_train)
```
---

## 💻 Implementation (Python Code)

Below is the complete implementation of the project:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

# Load dataset
df = pd.read_csv("Loan Approval Prediction dataset.csv")

# Basic info
print(df.head())
print(df.info())

# Handling missing values
for col in ['gender', 'married', 'dependents', 'self_employed']:
    df[col].fillna(df[col].mode()[0], inplace=True)

df['loanamount'].fillna(df['loanamount'].median(), inplace=True)
df['loan_amount_term'].fillna(df['loan_amount_term'].median(), inplace=True)
df['credit_history'].fillna(df['credit_history'].mode()[0], inplace=True)

# Drop unnecessary column
df.drop(columns=['loan_id'], inplace=True)

# Visualization
plt.hist(df["applicantincome"])
plt.title("Applicant Income Distribution")
plt.xlabel("Income")
plt.ylabel("Count")
plt.show()

sns.countplot(data=df, x="loan_status")
plt.title("Loan Status Distribution")
plt.show()

# Encoding
le = LabelEncoder()
df['loan_status'] = le.fit_transform(df['loan_status'])

df = pd.get_dummies(df, drop_first=True)

# Splitting data
X = df.drop("loan_status", axis=1)
y = df["loan_status"]

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Model training
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_train, y_train)

# Predictions
y_pred = rf.predict(X_test)

# Evaluation
print("Accuracy:", accuracy_score(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred))

# Confusion Matrix
cm = confusion_matrix(y_test, y_pred)

sns.heatmap(cm, annot=True, fmt="d", cmap="Blues")
plt.title("Random Forest Confusion Matrix")
plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.show()
---

## 📈 Results

- Achieved an accuracy of **78%** on test data  
- Model performed well in predicting loan approvals  
- Confusion matrix shows balanced classification performance  

---
## ✅ Conclusion

This project demonstrates how machine learning can automate loan approval decisions efficiently.  
The Random Forest model provided reliable predictions and handled the dataset effectively.

---
