# QuickLoan Governance Review Card

| Section | Issue / Definition | Impact | Suggested Fix / Mitigation |
|---------|-------------------|--------|---------------------------|
| **1. Data Quality Risk** | Incomplete and inconsistent customer data (e.g., missing income fields, inconsistent formats for phone numbers). | Leads to inaccurate ML predictions and poor loan decisions. | Implement data validation rules at input stage, enforce required fields, and standardize formats using preprocessing pipelines. |
| **2. Legal & Compliance Risk** | No explicit user consent before collecting sensitive personal data. | Violates Ghana Data Protection Act (Act 843), risking legal penalties and loss of trust. | Implement clear consent management system with opt-in checkboxes and audit logs. Apply data minimization principles. |
| **Data Classification** | Sensitive | Exposure of personal and financial data can cause serious harm to users. | Encrypt sensitive data, restrict access, and apply strict role-based access control (RBAC). |
| **3. Bias & Fairness Risk** | Model trained on biased or incomplete demographic data. | Unfair loan approvals or rejections for certain groups. | Introduce fairness checks, monitor model outputs across demographics, and retrain with balanced datasets. |
| **Source of Bias** | Historical data reflecting socioeconomic inequalities. | Reinforces discrimination patterns. | Use bias detection tools and include fairness constraints in model training. |
| **4. Storytelling / Reporting Recommendation** | Metric: Approval Rate by Demographic Group (percentage of approved loans per group). | Helps detect unfair treatment across groups. | Use a grouped bar chart to compare approval rates across demographics. |
| **Visualization Type** | Grouped Bar Chart | Clearly shows disparities between groups. | Enables easy monitoring and reporting. |
| **Why It Matters** | Ensures transparency and fairness in automated decision-making. | Builds trust and ensures compliance. | Supports ethical AI governance. |

---

## Corrected Data Flow Diagram (Annotated Fixes)

**Corrections Applied:**

- **Limit Data Collection (Step 1)**
  - Only collect essential data (e.g., income, ID, credit history).
  - *Reason:* Applies **data minimization principle**.

- **Add Consent Management (Step 2 → Step 3)**
  - Introduce user consent verification before storing data.
  - *Reason:* Ensures compliance with **Ghana Data Protection Act (Act 843)**.

- **Data Classification & Retention Policy (Step 3)**
  - Classify data as Sensitive and define retention period.
  - *Reason:* Prevents unnecessary long-term storage of PII.

- **Preprocessing Standards (Step 4)**
  - Add data cleaning, validation, and normalization.
  - *Reason:* Improves data quality and model accuracy.

- **Decision Logging (Step 7)**
  - Log all ML decisions with explanation metadata.
  - *Reason:* Enables transparency and auditability.

- **Data Masking (Step 9 & 10)**
  - Mask/anonymize PII before analytics or sharing with third parties.
  - *Reason:* Protects user privacy and prevents misuse.

---

## Summary of Review Process

The review process focused on analyzing the QuickLoan data pipeline using core data governance principles, particularly the data lifecycle and data classification frameworks. By examining each stage—from data collection to processing, storage, and sharing—it became clear where risks were introduced. For instance, excessive data collection violated the principle of data minimization, while the absence of consent mechanisms highlighted a major compliance gap under Ghana's Data Protection Act (Act 843). Classifying the data as "Sensitive" helped prioritize stricter controls such as encryption, access restrictions, and masking.

Data quality issues were identified at the preprocessing stage, where inconsistent and incomplete inputs directly impacted the reliability of the machine learning model. Addressing this required enforcing validation rules and standardization processes. Additionally, fairness concerns were traced back to biased historical data used in training the model. Without intervention, this could perpetuate systemic inequalities in loan approvals.

To ensure ongoing ethical governance, the proposed metric—"Approval Rate by Demographic Group"—provides a practical and transparent way to monitor fairness. By visualizing this metric using a grouped bar chart, stakeholders can easily identify disparities and take corrective action. This approach not only improves accountability but also aligns the system with ethical AI practices, ensuring decisions are both fair and explainable.
