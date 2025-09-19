# **WIWO-store: Steering a Wholesale Business with Auditable SQL Insights**

### **Project Overview**

For any wholesale distributor, growth isn't just about selling more; it's about selling *smarter*. This project moves beyond surface-level sales reports to build a durable, auditable analytics framework in SQL. Using the WideWorldImporters dataset, it demonstrates how to transform raw transactional data into a decision-support engine that answers critical questions about profitability, operational risk, and commercial strategy.

The core philosophy is "explainability-by-design." Every query is not just an answer, but a measurable, traceable control that can inform executive decisions and satisfy compliance requirements.

### **The Strategic Challenge**

The central challenge was to create a single source of truth that could reliably diagnose business performance and guide future strategy. This meant answering layered questions that standard dashboards often miss:

* **Trust & Integrity:** Can we trust our data? Are there integrity gaps that could lead to flawed conclusions or compliance issues?  
* **Performance Diagnosis:** When profit drops, can we pinpoint *why*? Was it a decrease in volume, a change in pricing, a shift in product mix, or underperformance in specific territories or by certain customers?  
* **Strategic Focus:** Where should we focus our limited resources? Which customers are most valuable? Which territories have the most potential versus those that are saturated?  
* **Operational Risk:** Are there hidden risks in our daily operations, like anomalous revenue spikes, that could signal fraud, data entry errors, or logistical bottlenecks?  
* **Growth Opportunities:** What products are frequently bought together? How can we use this insight to create smarter bundles, promotions, and pricing strategies?

  ### **My Approach: A "Control-First" Analytics Framework**

I tackled this by building the analysis in logical, auditable layers, moving from foundational data quality to advanced strategic insights.

1. **Building a Foundation of Trust (`00_data_quality_checks`):** Before any analysis, you need to trust your data. I started by implementing foundational integrity controls to check for orphan keys (sales that can't be tied to a valid customer) and the prevalence of "Unknown" sentinel values in our core dimensions. This isn't just data cleaning; it's a compliance and governance baseline that ensures the integrity of every subsequent insight.

2. **Mapping the Business Landscape (`01_exploratory_analysis` & `02_clusters`):** With a reliable dataset, the next step was to map the commercial and operational landscape. This involved analyzing pricing structures and markups, understanding the demographic footprint of our sales territories, and identifying areas of customer concentration—such as postal codes with more than three "Wingtip Toys" clients, signaling potential market saturation or a need for a dedicated territory strategy.

3. **Analyzing Performance Over Time (`03_time_intelligence_analysis`):** To understand trends, I used SQL window functions to build a robust time-intelligence layer. This provided clear, period-over-period metrics (YoY, MoM) and a rolling Year-to-Date (YTD) view of sales and profit. This layer is crucial for setting realistic targets and understanding business seasonality.

4. **Diagnosing Drivers and Managing Risk (`04_drivers`):** This is the core of the strategic analysis. To understand *why* performance changed (specifically, the profit drop between 2015 and 2016), I used contribution analysis to isolate the impact of individual customers, products, and cities. I also implemented two key proactive frameworks:

   * **RFM Segmentation:** To move from reactive to strategic customer management, I segmented the entire customer base by Recency, Frequency, and Monetary value. This allows for targeted strategies: rewarding loyal champions, re-engaging those at risk, and nurturing new customers.  
   * **Anomaly Detection:** Using z-scores on daily revenue, I built a control to automatically flag days with statistically significant revenue spikes or dips. This serves as an early-warning system for operational issues or commercial events that require investigation.  
5. **Uncovering Hidden Growth Opportunities (`05_basket_analysis`):** Finally, I looked for organic growth levers within the existing sales data. A market-basket analysis revealed which products are most frequently purchased together, using metrics like support, confidence, and lift to identify the strongest pairings. This provides a data-driven basis for creating bundles, targeted cross-sell campaigns, and smarter pricing policies.

   ### **Strategic Outcomes & Decisions Enabled**

This SQL framework wasn't just an academic exercise; it was designed to directly enable key business decisions with auditable evidence:

* **Data Governance:** The quality checks provide a clear, ongoing metric for data integrity, enabling the creation of data contracts with source system owners to reduce errors.  
* **Commercial Focus:** Instead of treating all customers equally, the RFM analysis allows the sales team to prioritize efforts on high-value segments, while contribution analysis shows exactly which products and clients are driving profitability.  
* **Territory Management:** The cluster analysis provides a clear, data-backed reason to review territory assignments, potentially creating specialized roles for high-density areas or reallocating resources from saturated ones.  
* **Operational Control:** The anomaly detection system turns the analytics team into a proactive partner for Operations and Finance, helping to ensure revenue stability and investigate incidents before they escalate.  
* **Pricing & Promotions:** The market-basket analysis provides a scientific foundation for the marketing and pricing teams to design bundles that are statistically more likely to succeed.

  ### **From Queries to Governance: Why This Matters for Strategy & Policy**

The true value of this project lies not in the individual queries, but in the cohesive, auditable system they create. By building controls directly into the SQL, we establish a framework where:

* **Every KPI is Traceable:** The logic is clear, documented, and reproducible, providing an "audit trail" for any metric.  
* **Controls are Measurable:** Instead of vague policies, we have specific, query-able controls (e.g., "orphan keys must be 0," "daily revenue z-score must be \< 2").  
* **Decisions are Defensible:** When recommending a strategic shift, we can point to the specific analysis, data, and rules that support it.

This approach is documented in the accompanying GRC (Governance, Risk & Compliance) artifacts, including the `POLICY_COMPLIANCE_MAPPING.md` and `RISK_REGISTER.md`, which formalize the connection between the code and the business's strategic objectives.

### **Technical Snapshot**

* **Language/Environment:** T-SQL (CTEs, window functions, percentiles, NTILE, LAG/ROLLUP) in a relational database environment.  
* **Reproducibility:** The entire analysis is contained in the `-- SQL WIWO Analysis.sql` script. It is designed to be run sequentially on the standard WideWorldImporters database schema.  
- 