# KPI Definitions — WIWO-store

\- Data exception rate \= (OrphanCustomerKeys \+ out-of-threshold Unknowns) / relevant total rows.

\- Profit YoY/MoM/YTD \= per 03\_time\_intelligence (defined windows and LAG/rolling).

\- Daily revenue volatility \= share of days with |z-score| ≥ 2\.

\- RFM: quintiles for Recency/Frequency/Monetary; segment \= CONCAT(R,F,M).

\- Bundle lift \= conf(A→B) / support(B).

### Notes:

\- Time standard: dimDate.Date (UTC if applicable).

\- Category/channel-specific thresholds documented.