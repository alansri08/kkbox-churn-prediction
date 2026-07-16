# KKBox Subscriber Churn & Retention Strategy 🎧

## Executive Summary
This project architects an end-to-end churn prediction and customer retention pipeline for KKBox, a leading music streaming service. By processing over 21 million transaction records in a distributed Databricks/PySpark environment, I developed a dual-model approach: a machine learning classifier to identify high-risk users, and a Buy Till You Die (BTYD) survival model to translate that risk into a dollar-value prioritization framework for targeted marketing spend.

Key Outcomes:

Business Impact: Identified a "Tier 1" segment representing [Insert Tier 1 Count] high-value users at risk of churn. Based on an average spend of $[Insert Avg Spend], a 10% reduction in churn within this segment protects approximately $[Insert Estimated Revenue] in monthly recurring revenue.

Predictive Lift: Achieved an ROC AUC of 0.7357, providing meaningful lift over random targeting for proactive retention intervention.

Operational Efficiency: Developed a scalable pipeline that balances production-grade latency with high-fidelity predictive modeling by leveraging representative statistical sampling on 21M+ transaction records.
<img width="1185" height="384" alt="image" src="https://github.com/user-attachments/assets/b2146996-23fd-49c2-ae73-c5b6c71498cd" />


## The Business Problem
In the subscription economy, Customer Acquisition Cost (CAC) heavily outweighs retention costs. Identifying *which* users are likely to churn is only half the battle; the business must also know *who is actually worth saving*. A user who spends $5 a year and churns requires a different intervention strategy than a power-user who spends $500. This project bridges the gap between raw predictive analytics and operational product strategy.

## Methodology & Architecture

### 1. Data Engineering & Aggregation (PySpark)
* Ingested multi-gigabyte raw datasets containing user demographic logs, daily streaming activity, and historical financial transactions.
* Aggregated 21.5 million transaction rows down to user-level RFM (Recency, Frequency, Monetary) metrics, utilizing PySpark for distributed memory management.

### 2. Handling Class Imbalance
* The raw dataset contained a severe class imbalance (929K active users vs. 63K churned users).
* Applied rigorous 50/50 downsampling to the majority class to prevent the model from overfitting to the baseline "active" state, resulting in a bias-free analytical dataset of ~115,000 users.

### 3. Baseline Classification (Spark MLlib)
* Standardized features and deployed a Logistic Regression classifier to maximize interpretability for product stakeholders.
* Extracted model weights to prove the negative correlation between transaction frequency and churn probability.

### 4. Stakeholder Prioritization Matrix (BTYD / BG-NBD)
* Applied the `lifetimes` library to calculate $P(Alive)$ (the probability a user is still an active subscriber).
* Calculated a `risk_value_score` by multiplying the probability of churn by historical customer spend, segmenting users into Tier 1 (Immediate Recovery), Tier 2 (Proactive Engagement), and Tier 3 (Standard Retention).

## Technology Stack
* **Platform:** Databricks
* **Big Data Processing:** PySpark, SQL
* **Machine Learning:** Spark MLlib (Logistic Regression), `lifetimes` (BG/NBD Survival Modeling)
* **Languages:** Python

[Click here to read my Strategic Business Insights](BUSINESS_INSIGHTS.md)
