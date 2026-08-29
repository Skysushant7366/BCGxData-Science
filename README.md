# ⚡ PowerCo Churn Analysis: BCG X Data Science Strategy

**Author:** Sushant Kumar Yadav  
**Domain:** Data Science, Feature Engineering, & Business Strategy  
**Client:** PowerCo (Gas & Electricity Utility)

## 📑 Executive Summary
PowerCo, a major gas and electricity utility, was experiencing elevated customer churn within their SME (Small & Medium Enterprise) division. The working hypothesis at the executive level was that *price sensitivity* drove this churn. 

This repository encapsulates the end-to-end data science process I utilized to test this hypothesis, engineer custom price-variance features, and build a predictive model to guide proactive retention strategies.

### 💡 Core Findings & Model Reality:
* **The Hypothesis Test:** Price sensitivity alone is **not** the dominant driver of churn. Customers are more influenced by long-term contracts and margin variations.
* **The Imbalance Challenge:** The baseline churn rate was only ~9.72%, causing severe class imbalance (approx. 1:9). 
* **The "Accuracy" Trap:** Our baseline Random Forest achieved ~90% accuracy, but a deeper dive into the Confusion Matrix revealed a low **Recall** (missing many actual churners). This highlighted that a proactive retention program must rely on `predict_proba` risk rankings (and further tuning with SMOTE/class weights) rather than binary thresholds alone.

---

## 📂 Repository Architecture
* `/Raw-data`: Contains the foundational datasets (`client_data.csv` and `price_data.csv`).
* `/View`: HTML exports of Jupyter Notebooks for easy viewing (`Task_3_EDA.html`, `Task_4_FEATURE_ENGINEERING.html`, `Task_5_PREDICTIVE_MODELLING.html`).
* `clean_data_after_eda.csv`: The scrubbed dataset prepped for feature synthesis.
* `*.ipynb files`: The core Python engine handling the logic from ingestion to evaluation.

---

## 🛠️ The Data Science Pipeline

### 1️⃣ Task 3: Exploratory Data Analysis (EDA)
* **Goal:** Understand client demographics and test the underlying "price sensitivity" assumption.
* **Actions:** Cleaned data (handling NA values and datetime parsing), assessed feature skewness, and evaluated churn distribution against key categorical features.

### 2️⃣ Task 4: Advanced Feature Engineering
* **Goal:** Transform raw temporal price data into robust, predictive signals.
* **Actions:** 
  * Calculated the **Dec–Jan off-peak price difference** to capture sudden price shocks.
  * Extracted the **Mean Period Differences** (average spread across periods).
  * Calculated **Max Monthly Differences** to quantify maximum peak exposure.

### 3️⃣ Task 5: Predictive Modeling & Evaluation
* **Goal:** Predict churn likelihood and interpret results in a business context.
* **Actions:** 
  * Trained a **Random Forest Classifier**.
  * Looked past surface-level "Accuracy" to analyze **Precision, Recall, and Feature Importance**.
  * Concluded that while the model struggled to definitively "flag" all churners (due to imbalance), it succeeded in identifying the most critical variables driving future customer spend.

---
*Completed as part of the BCG X Data Science Virtual Experience (Forage).*
