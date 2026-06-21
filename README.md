# Enterprise Predictive Analytics: Bank Telemarketing Optimization 🏦📊

**An end-to-end Machine Learning pipeline built with SAS Enterprise Miner to optimize term deposit subscription campaigns.**

🔗 **[Read the Full Business Case Study & Strategy on Notion](https://app.notion.com/p/Enterprise-Predictive-Analytics-Optimizing-Bank-Telemarketing-Campaigns-with-SAS-386d0e8d0302802bb854e032d1346d2a?source=copy_link)**

---

## 📌 Project Overview
Telemarketing campaigns are often hindered by high operational costs and low conversion rates. This project leverages enterprise-grade predictive analytics to transition a bank from a "mass-calling" strategy to a precision-targeted approach. By predicting which customers are most likely to subscribe to a term deposit, the bank can optimize its marketing resources and significantly increase its Return on Investment (ROI).

*   **Objective:** Predict the binary outcome (`TargetBuy`) of whether a client will subscribe to a term deposit.
*   **Tool Used:** SAS Enterprise Miner.
*   **Techniques:** Data Preprocessing, Dimensionality Reduction, Logistic Regression, Decision Trees, Neural Networks.

---

## ⚙️ Data Engineering & Pipeline Architecture

<img width="1024" height="266" alt="image" src="https://github.com/user-attachments/assets/ee6d2926-f73f-4763-867b-593ffd00a985" />

To ensure model stability and prevent data leakage, a rigorous data preparation pipeline was implemented before modeling:
1.  **Metadata Configuration:** Rejected near-zero variance predictors (e.g., `default`) and assigned proper roles to prevent identity memorization.
2.  **Imputation:** Applied Median Imputation for the `pdays` variable (days since last contact) which contained >80% missing data, creating an imputation indicator to flag "New Prospects".
3.  **Outlier Scrubbing:** Utilized the Replacement Node to cap extreme right-skewed variables (e.g., `balance`, `duration`) at 3 Standard Deviations, preventing regression coefficients from being biased by extreme outliers.
4.  **Categorical Regrouping:** Collapsed sparse categories (e.g., `job`, `month`) into broader, stable segments to prevent model overfitting.

---

## 🤖 Model Training & Evaluation

The dataset was partitioned into Training (70%) and Validation (30%) sets. Three distinct algorithmic approaches were developed and rigorously compared:

### 1. Logistic Regression (Stepwise Selection)
*   Utilized Stepwise Selection based on Validation Error, retaining 12 critical predictors.
*   Provided high interpretability, revealing that longer call `duration`, higher `balance`, and the absence of a `housing` loan strongly increase subscription probability.

### 2. Decision Tree (Optimized via ASE)
*   Tuned using Average Squared Error (ASE) to prevent overfitting, resulting in a 23-leaf architecture.
*   Extracted actionable business thresholds, identifying "Hyper-Engaged Prospects" (calls > 827.5 seconds) and highlighting the critical "8-Minute Turning Point" (492.5 seconds).

### 3. Neural Network (Champion Model) 🏆
*   **Architecture:** Multilayer Perceptron (MLP) with 3 Hidden Units.
*   **Why it won:** Achieved the lowest Validation Misclassification Rate (9.76%) and the highest ROC Index (0.91), successfully capturing complex, non-linear interaction effects between variables.

---

## 🚀 Key Business Impact & Scoring

<img width="882" height="394" alt="Model Comparison ROC" src="https://github.com/user-attachments/assets/2e8c5d34-ae9e-48a3-8704-0912bb59b959" />

The champion Neural Network model was deployed to score 13,564 unseen prospects. 

*   **Cumulative Lift:** The model achieved a **Cumulative Lift of 5.79** at the top 5% depth. 
*   **ROI Translation:** This indicates that by focusing telesales resources exclusively on the top 5% of prospects identified by the Neural Network, the bank can capture nearly **6 times more subscribers** compared to a random calling approach.

### The "Hybrid" Implementation Strategy
To overcome the "Black-Box" nature of the Neural Network, a hybrid deployment strategy was recommended:
1.  Use the **Neural Network's Probability Score** to filter and prioritize the daily CRM call list.
2.  Use the **Decision Tree's explicit "If-Then" rules** (e.g., call duration thresholds) to train telesales agents on mid-call intervention strategies.

---

## 📁 Repository Contents
*   `/reports`: Contains the full technical documentation (`SAS_Predictive_Analytics_Report.pdf`).
*   `/sas_project`: Contains the exported `.spk` (SAS Package) file. To review the model flow, import this package directly into your SAS Enterprise Miner workspace.

---
*Developed by An (Ashley) Tran.*
