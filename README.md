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

## 📊 Tuned Model Results (Test Set)
| Tuned Model | Accuracy | F1 | ROC AUC | 
|---|---:|---:|---:|
| Logistic Regression (Tuned) | 94.94% | 97.08% | 98.42% | 
| KNN (Tuned) | 94.12% | 96.89% | 97.33% | 
| Decision Tree (Tuned) | 93.77% | 96.65% | 92.31% | 
| Linear SVM (Tuned) | 94.93% | 97.10% | 98.41% | 

---

## ✅ Final Model Selection *
| Selected Model | Accuracy | F1 | ROC AUC | 
|---|---:|---:|---:|
| **Linear SVM (Best Tuning Result)** | 94.93% | 97.10% | **98.41%** | 

**Winner model selected** based on highest **ROC AUC on held-out test set**.

> **Percentile capping (1st–99th)** was applied on financial outliers instead of dropping 7–8% of applications:
> - Preserves sample size  
> - Reduces distortion from extreme values  
> - Prevents biased model dominance from long-tailed financial signals  

---

## 📍 Key Conclusions 
- We can **accurately rank and classify approval likelihood with ML**, but must:
  - Avoid leakage from post-decision outcome fields
  - Preserve sample size for fair representation
  - Compare models by probability separability, not a fixed threshold

- **Linear SVM performed best** at:
  - Ranking approvals ahead of denials across thresholds
  - Maintaining strong accuracy and F1 after threshold-free model selection
  - Supporting next phase underwriting automation integrity

- **KNN performed well after tuning**, but has:
  - Higher inference cost  
  - Best used in optimization stage with neighbor search improvements (KD-tree, BallTree, FAISS, or other approximations)  

- **Decision Tree remains valid**, but shows:
  - Lower ROC AUC separability on full data than linear or margin-based models  

---

## 💼 Next Steps - Business Applications of Prediction Model

- **Accelerate loan decisions**
  - The model delivers an early approval likelihood score, enabling loan teams to move the strongest applications forward faster.

- **Work smarter, not harder**
  - Staff can prioritize time and attention on applications with the highest chance of approval, reducing bottlenecks.

- **Improve buyer experience**
  - Customers gain faster clarity, allowing more productive conversations centered on outcomes they can realistically achieve.

- **Provide proactive guidance**
  - When approval likelihood is low, teams can suggest adjusted loan options or credit-building steps *before* a formal denial.

- **Reduce manual review workload**
  - High-confidence approvals can be pre-flagged for fast-track processing, allowing human review to focus on edge cases only.

- **Enable consistent underwriting support**
  - Predictions apply uniform criteria across all applicants, providing fair, reliable, and scalable decision-support.

- **Support internal planning**
  - Approval volume can be forecasted earlier, improving staffing decisions, processing timelines, and capital planning.

- **Create routing tiers**
  - Applications may be grouped for actioning such as:
    - **High confidence approval**
    - **Likely approval**
    - **Needs review**
    - **High risk**
  - These tiers guide effort prioritization and potential future automation.

> **Conclusion:**  
> The model becomes a decision-support tool that allows the business to estimate approval earlier, work more intelligently, respond faster to buyers, and plan capacity reliably — without depending on information that cannot be known at submission time.


