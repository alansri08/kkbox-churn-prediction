# Business Insights: Predictive Retention Strategy

### 1. The Core Objective
This project moves beyond descriptive reporting to proactive churn management. By utilizing the Beta-Geometric/Negative Binomial Distribution (BG-NBD) model, we transformed 21 million rows of raw transactional data into a prioritized recovery roadmap.

### 2. Strategic Methodology
Using a representative random sample of 10,000 records from the 21M+ transaction dataset, the model identifies churn patterns. This approach allowed for high-fidelity predictive modeling while optimizing for production-grade latency, ensuring the model could be iterated upon quickly without compromising the integrity of the insights.

### 3. Key Takeaway: Resource Allocation
The primary takeaway is that data science is about efficient resource allocation. My model identified the **"Red Tier" (Tier 1)**—high-value users at high risk—allowing the business to stop wasting marketing spend on loyal users who do not need intervention, and instead focus resources where they directly drive the bottom line.

### 4. Recommendation for Business Impact
To improve retention and maximize Customer Lifetime Value (CLV), I recommend a **Risk-Based Intervention Strategy**:
* **Triggered Retention**: Shift from mass-marketing to automated, personalized offers triggered specifically for Tier 1 users.
* **Cost Optimization**: Reallocate marketing budget away from "Tier 3: Standard Retention" users, as their churn risk is statistically negligible.
* **Revenue Protection**: Focus recovery efforts on Tier 1 to protect top-line revenue before these high-value customers churn completely.

### 5. Limitations & Future Refinement
* **Model Calibration:** The current model uses a downsampled training set; before deployment, a recalibration step is required to adjust raw probabilities to the true population churn rate.
* **Model Iteration:** The current Logistic Regression serves as a baseline. Future iterations will compare this against Gradient Boosted Trees (XGBoost/LightGBM) to capture non-linear behavioral patterns.
* **Evaluation:** Future work will involve validating BTYD model assumptions against a true holdout period to ensure long-term stability.
