# ⚡ PowerCo Churn Analysis: BCG X Data Science Strategy

**Author:** Sushant Kumar Yadav  
**Domain:** Data Science, Predictive Modeling & Business Strategy  
**Client:** PowerCo (Gas & Electricity Utility)  

## 📑 Executive Summary
PowerCo, a major gas and electricity utility, was experiencing elevated customer churn within their SME (Small & Medium Enterprise) division. The working hypothesis at the executive level was that *price sensitivity* drove this churn. 

This repository encapsulates the end-to-end data science process I utilized to test this hypothesis, engineer custom price-variance features, and build a predictive model to guide proactive retention strategies.

> **💡 The Business Reality:** Price sensitivity alone is **not** the dominant driver of churn. The baseline churn rate was only ~9.72%, causing a severe class imbalance (1:9.3)[cite: 7]. While our Random Forest model achieved ~90% accuracy, a deeper dive revealed a low Recall (missing many actual churners)[cite: 7, 9]. This highlighted that a proactive retention program must rely on `predict_proba` risk rankings rather than binary thresholds alone[cite: 9].

---

## 📊 Project By The Numbers
* **Client Data Analyzed:** 14,606 unique SME customers[cite: 7]
* **Pricing Data Analyzed:** 193,002 historical price records[cite: 7]
* **Baseline Churn Rate:** 9.72% (1,419 actual churners)[cite: 7]
* **Features Engineered:** Expanded to a robust 63-feature matrix[cite: 8]
* **Model Performance:** 90.3% Accuracy | 81.0% Precision | 4.6% Recall[cite: 9]

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
* **Actions:** 
  * Ingested and merged the **14.6K client records** and **193K pricing records**[cite: 7].
  * Handled missing values, parsed datetimes, and evaluated churn distribution against key categorical features[cite: 7].
  * Identified the massive **1:9.3 class imbalance** (Not-Churned to Churned), setting the stage for strict model evaluation metrics[cite: 7].

### 2️⃣ Task 4: Advanced Feature Engineering
* **Goal:** Transform raw temporal price data into robust, predictive signals.
* **Actions:** 
  * Extracted the **Dec–Jan off-peak price difference** to capture sudden price shocks[cite: 8].
  * Engineered 6 **Mean Period Differences** (average spread across periods) and 6 **Max Monthly Differences** to quantify maximum peak exposure[cite: 8].
  * Successfully expanded the dataset into a **63-column feature matrix** ready for machine learning[cite: 8].

### 3️⃣ Task 5: Predictive Modeling & Evaluation
* **Goal:** Predict churn likelihood and interpret results in a business context.
* **Actions:** 
  * Trained a **Random Forest Classifier** utilizing 1,000 decision trees (`n_estimators=1000`) on a 75/25 Train-Test split[cite: 9].
  * Looked past surface-level metrics: While **Accuracy was 90.3%** and **Precision was strong at 81%**, the model only caught 17 out of 366 actual churners (**Recall: 4.6%**)[cite: 9].
  * **Strategic Conclusion:** The model struggles to definitively "flag" all churners due to data imbalance. Therefore, the business recommendation is to utilize the model's probability scores (`predict_proba`) to rank customers by risk, rather than relying on binary Yes/No flags[cite: 9].

---
*Completed as part of the BCG X Data Science Virtual Experience (Forage).*
