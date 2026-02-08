# Credit Risk PD Modeling using Logistic Regression

This project demonstrates a basic **Probability of Default (PD) model** using **Logistic Regression** on a synthetically generated credit dataset.

The focus is on understanding model behavior, evaluation metrics, and common challenges such as **class imbalance** in credit risk modeling.

---

## 📌 Problem Statement

Can borrower attributes such as income, loan amount, credit score, and age be used to estimate the probability of default, and what challenges arise when modeling rare default events using logistic regression?

This is framed as a **binary classification problem**:
- `1` → Default
- `0` → Non-default

---

## 📊 Synthetic Dataset Generation

The dataset is fully synthetic and generated using NumPy.

**Features include:**
- Loan Amount
- Income
- Credit Score
- Age
- Default (binary target)

Key characteristics:
- Dataset size: 1000 samples
- Default rate: ~10%
- Data generated for **educational and demonstration purposes only**

---

## 📊 Synthetic Dataset Assumptions

The synthetic dataset is generated based on simplified statistical assumptions.
As shown in the data generation step in the notebook, continuous variables such as **loan amount**, **income**, and **credit score** are sampled from **normal distributions** with predefined means and standard deviations, while **age** is sampled from a bounded uniform distribution.

The target variable (**Default**) is generated using a **Bernoulli process** with a fixed probability of default, independent of borrower features.
This assumption enables controlled experimentation but does not reflect real-world credit behavior, where default risk is typically correlated with borrower characteristics.

Because the default outcome is generated independently of the explanatory variables, the dataset lacks an underlying predictive signal.
As a result, model performance metrics—particularly the ROC–AUC score—primarily reflect the limitations of the data assumptions rather than the effectiveness of the Logistic Regression model itself.

This section intentionally highlights how unrealistic or oversimplified data-generation assumptions can lead to misleading accuracy metrics and poor discriminatory power in credit risk models.

---

## ⚙️ Methodology

- **Model Used:** Logistic Regression
- **Train-Test Split:** Standard train-test split
- **Evaluation Metrics:**
  - Classification Report
  - ROC Curve
  - AUC Score

---

## 📈 Model Evaluation & Results

### Classification Report Summary

- High overall accuracy due to class imbalance
- Model predicts the majority (non-default) class well
- Poor recall and precision for the default class

### ROC–AUC Score

- **AUC ≈ 0.43**
- Indicates performance worse than random guessing

This highlights a common issue in credit risk modeling:
> Accuracy alone is misleading when default events are rare.

---

## 🧠 Key Learnings

- Class imbalance can severely distort model performance
- Accuracy is not a reliable metric for credit risk problems
- ROC–AUC is critical for evaluating PD models
- Model performance is highly sensitive to data-generation assumptions
- Logistic Regression struggles without:
  - Meaningful feature–target relationships
  - Class weighting or resampling
  - Domain-informed data design

---

## ⚠️ Limitations

- Synthetic data lacks real-world correlations
- Default variable is randomly generated
- No feature engineering or domain constraints applied
- Model not suitable for real credit decisions

---

## 🚀 Future Improvements

- Introduce realistic relationships between features and default
- Apply class weighting or resampling techniques (e.g., SMOTE)
- Compare performance with tree-based models
- Add KS statistic and precision–recall curves
- Tune probability thresholds for better risk separation

---

## 🛠️ Tools & Libraries

- Python  
- NumPy  
- Pandas  
- Scikit-learn  
- Matplotlib  
