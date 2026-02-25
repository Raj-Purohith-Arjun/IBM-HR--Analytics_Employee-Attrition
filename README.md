
# IBM HR Analytics — Employee Attrition Modeling

**Author:** Raj Purohith Arjun  
**Stack:** Python · SQL · Logistic Regression · ElasticNet · Statistical Analysis · Dashboarding

---

## 📌 1. Project Overview

Employee attrition has a direct impact on productivity and cost. This project uses the IBM HR Analytics dataset to explore the **key drivers of attrition**, such as:

- Demographics
- Work-life balance
- Job satisfaction
- Compensation and performance

The objective is to deliver **actionable insights** that support **data-driven retention strategies** and **workforce optimization**.

### 🎯 Research Questions

- What factors most influence employee attrition?
- How do salary and commute distance impact turnover?
- Which roles or departments have higher attrition?
- Can machine learning models accurately predict attrition?
- How do performance and satisfaction relate to retention?

---

## 📂 2. Dataset Description

- **Source:** Kaggle – IBM HR Analytics Employee Attrition & Performance  
- **Rows:** 1,470 employees  
- **Features:** 35 variables  
- **Target:** `Attrition` (Yes = left, No = stayed)  
- **Dropped Columns:** `EmployeeCount`, `StandardHours`, `EmployeeNumber` (non-informative)

---

## 🧹 3. Data Preparation & Encoding

- **Ordinal Encoding:** Applied to features like JobSatisfaction & EnvironmentSatisfaction.
  - Example: JobSatisfaction → Low=0, Medium=1, High=2
- **One-Hot Encoding:** Applied to nominal features (e.g., Gender, Department).
- **Scaling:** Standardized numerical features like MonthlyIncome and MonthlyRate.

---

## 📊 4. Exploratory Data Analysis (EDA)

### 4.1 Univariate Insights

- **Age:** Mean ~37; diverse workforce from 18–60
- **Job/Environment Satisfaction:** Avg ~1.7/3 — scope for improvement
- **Distance from Home:** Most <10 units; long commutes → attrition risk
- **Income:** Right-skewed; retention tied to fair compensation
- **Training:** Median = 3 sessions/year
- **Attrition Rate:** ~16% — moderate concern

📈 *Visuals included:* Histograms, boxplots, density plots

---

### 4.2 Bivariate Insights

- **Correlations:**
  - Age ↔ Total Working Years (0.68)
  - Total Working Years ↔ Monthly Income (0.77)
  - Distance from Home → linked with higher attrition
- **Weak relationships:** Job Satisfaction & Work-Life Balance had low correlation with numeric variables
- **Scatter/Pair Plots:**
  - Younger, lower-paid, and long-commuting employees → higher attrition
  - Longer tenure + higher income → lower attrition
  - Job satisfaction clusters distinguish attrition status

---

### 4.3 Multivariate Analysis

- **Heatmap:** Reinforced key correlation clusters
- **PCA:** First two PCs explain 38.75% variance; partial cluster separation
  - Suggests need for non-linear modeling for deeper insights

---

## 🤖 5. Regression and Classification Modeling

### 5.1 Regression Models (Numeric Target)

| Model                    | R²     | RMSE   | Conclusion                            |
|--------------------------|--------|--------|----------------------------------------|
| Simple Linear Regression | 0.022  | 0.3355 | Poor explanatory power                 |
| Multiple Linear Reg.     | 0.0602 | 0.3288 | Slightly better, still weak            |
| Polynomial Regression    | 0.0551 | 0.3575 | Inadequate for binary outcome          |

*Attrition is binary → regression models not suitable.*

---

### 5.2 Logistic Regression (Classification)

- **Accuracy:** 87.07%
- **Precision:** 54.55%
- **Recall:** 39.34%
- **ROC-AUC:** 0.8065

📌 *Insight:* Good discrimination, but recall low → churners missed.

---

## ⚙️ 6. Advanced Modeling & Regularization

| Model            | R² / Metric   | Insight                                                   |
|------------------|---------------|------------------------------------------------------------|
| Ridge Regression | R² ≈ 1        | Great fit, but overfitting risk                           |
| LASSO            | R² = 0.9278   | Strong performance + built-in feature selection           |
| Elastic Net      | R² = 0.9691   | Best balance of accuracy and generalization               |
| Cox Regression   | Concordance = 0.79 | Good predictor of attrition timing                  |
| Quantile / Poisson / Hurdle Models | – | Useful for count and zero-inflated modeling           |
| PLSR / PCR       | –             | Dimensionality reduction with latent factor insights       |

---

## ✅ 7. Model Evaluation Summary

| Model                  | Accuracy | ROC-AUC | Notes |
|------------------------|----------|---------|-------|
| Logistic Regression    | 83.3%    | 0.754   | baseline |
| ElasticNet (l1=0.5)    | 83.7%    | 0.754   | 29 features kept |

---

## 📌 8. Recommendations & Business Actions

### 🎯 Who to Target:
- Younger employees (high risk group)
- Low-income earners
- Long-distance commuters

### 🛠 How to Retain:
- Improve job satisfaction and work-life balance
- Offer role clarity and career advancement
- Increase access to training & development
- Explore hybrid/remote options for long-distance commuters

### 🔍 Modeling Strategy:
- Use classification models with class balancing
- Apply regularization (LASSO, ElasticNet) to prevent overfitting
- Include behavioral & qualitative data in future models

---

## 🧭 9. How to Use This Project

- Preprocessed and encoded dataset ready for ML workflows  
- Visual EDA and statistical findings  
- Model performance summaries for both regression and classification  
- Business interpretations at each modeling step  
- Suitable for HR teams, data analysts, or organizational development leads

---

## 📚 10. References

- IBM HR Analytics Dataset (Kaggle)  
- DataCamp & Medium tutorials on attrition modeling  
- Seaborn, Matplotlib for visualization  
- Logistic regression & regularization papers in HR analytics

---

📓 **Main Notebook:** [`IBM_HR_Attrition.ipynb`](IBM_HR_Attrition.ipynb) — fully runnable, no external data needed.

📄 **Full Report:** See `Report2.pdf`

