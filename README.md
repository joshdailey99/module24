# 🏡 Housing Loan Approval Prediction (California 2022–2024)

## 🎯 Research Question  
**Can we accurately predict whether a housing loan application will be approved (True/False) based on applicant demographics, financial metrics, loan structure, and property characteristics?**

---

## 📊 Project Overview  
This project analyzed **3 years of California housing-loan application data (2022–2024)**, narrowed to a **typical single-family homebuyer use case (1–4 owner-occupied units)** and excluded:

- 🏭 Manufactured-home lending
- 🏢 Multifamily rental or large property transactions
- 💼 Business/commercial-purpose applications

Analysis notebook: [Module_24.ipynb](https://github.com/joshdailey99/module24/blob/main/Module_24.ipynb)

---

## 💼 Business Benefit
Being able to predict approval in advance provides:

- ⚡ **Faster application decisions**
- 📥 **Better underwriting prioritization**
- 💰 **Reduced processing cost**
- 🤖 **A sound baseline for future automation**
- 📊 **A fair and reliable metric for model comparison and optimization**

---

## ✅ Key Work Completed (Baseline Phase)
- 🧼 **Data cleaning & validation**
- 🚨 **Outlier analysis and percentile capping (Winsorization)**
- ❓ **Missing-value treatment (imputation where appropriate)**
- 🧠 **Feature engineering (e.g., loan-to-income ratios)**
- 🔢 **Baseline model benchmarking using multiple ML families**

Models evaluated:
- **Logistic Regression**
- **K-Nearest Neighbors (KNN)**
- **Decision Tree**
- **Linear SVM (Support Vector Machine)**

---

## 📈 Evaluation Metric Selected  
The chief model-comparison benchmark was **ROC AUC (Receiver Operating Characteristic — Area Under Curve)**.

### Rationale for Selecting ROC AUC ✅
- Measures **how well the model separates Approved vs Denied applications across ALL thresholds**, not just 0.5
- Evaluates **probability ranking quality**, which is critical in underwriting
- Remains reliable for **approval-dominant (skewed) populations**
- Allows future decisions like:
  - risk-tier routing
  - automated-underwriting cutoffs
  - model family stability comparison

> ❗ **Denial-reason fields were excluded from predictive modeling** because the denial reason cannot be known at submission time and would introduce **outcome leakage**, undermining the integrity of approval prediction.

---

## 📊 Baseline Model Performance Summary

| Model | Accuracy | F1 Score | ROC AUC | 
|---|---:|---:|---:|
| Logistic Regression (Baseline) | 94.94% | 97.08% | 98.42% | 
| KNN (Baseline) | 93.97% | 96.53% | 95.80% | 
| Decision Tree (Baseline) | 94.94% | 97.09% | 88.84% | 
| Linear SVM (Baseline) | 94.91% | 97.06% | 98.39% | 


---


## 🚀 Next Steps (Future Model Tuning & Comparison Phase 2025)
Section 12–13 of the notebook will later:

1. **Tune ML models using a smaller stratified cross-validation sample**
2. Benchmark tuned models using:
   - ROC AUC and PR AUC for ranking quality
   - confusion matrices at justified business cutoffs
   - F1 evaluation AFTER selecting an operational decision threshold
3. Deliver final business reporting including:
   - Best model selection
   - improvement deltas
   - threshold recommendation for automated underwriting
   - fairness and performance verification

---

## 📍 Recommendations for Stakeholders (Plain Language)

- ✅ Retain **3 years of data minimum (2022–2024)** to avoid bias from single-year anomalies
- ✅ **One-hot encode categorical fields** to preserve applicant and loan-structure signals
- ✅ **Cap extreme financial outliers**, do not drop applications unnecessarily
- ✅ **Exclude denial-reason fields from predictive modeling** to avoid invalid predictions
- ✅ Use **ROC AUC as the primary benchmarking metric for model family comparison**
- ✅ Score **F1 only after choosing an underwriting decision cutoff**
- 🔁 Continue tuning using **Linear SVM or Logistic Regression families**, then pick an operational threshold before automation.

---

> **Conclusion:**  
A probability-aware baseline based on ROC AUC ensures fair model comparison and supports next-phase model tuning, threshold selection, and underwriting automation integrity.

---
