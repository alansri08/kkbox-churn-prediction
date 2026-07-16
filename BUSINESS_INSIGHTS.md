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
* **Model Performance:** The model achieved an ROC AUC of 0.7357. While this provides meaningful lift over random targeting for proactive retention, future iterations will explore gradient-boosted decision trees and additional behavioral features—such as user skip rates and session length—which are often more predictive of churn.
* **Calibration:** To optimize for production latency, we addressed class imbalance during training by downsampling the majority class. In a live production deployment, we would recalibrate predicted probabilities to reflect the true population churn rate.

<br>

<img width="1185" height="384" alt="Customer Distribution by Retention Priority" src="https://github.com/user-attachments/assets/57184343-1288-49a9-bac5-ec4aa7578370" />
*Figure 1: Distribution of customers across risk-based retention tiers. The majority of the subscriber base exhibits low risk, allowing for hyper-targeted retention efforts on the high-value Tier 1 segment.*
