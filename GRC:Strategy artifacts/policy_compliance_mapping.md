# Policy & Compliance Mapping — WIWO-store

| Policy/Standard                    | SQL Control (section)             | Rule/Threshold                                   | Evidence/Audit                           | Owner        |

|------------------------------------|-----------------------------------|--------------------------------------------------|------------------------------------------|-------------|

| Referential integrity              | 00\_data\_quality\_checks            | factSale without dimCustomer \= 0                 | OrphanCustomerKeys query \+ timestamp     | Data Eng     |

| Catalog quality (sentinel)         | 00\_data\_quality\_checks            | 'Unknown' in dims below tolerance (X%)           | Unknowns by dimension (counts)           | Data Stew.   |

| Revenue stability                  | 04\_drivers (daily z-score)        | |z| \< 2 (tunable)                               | Daily anomaly table                      | Operations   |

| Fairness/focus by territory        | 02\_clusters (Wingtip\>3 per ZIP)   | Review ZIPs with \>3 Wingtip stores               | ZIP/customer list                        | Sales        |

| Pricing/Markup                     | 01\_exploratory (markup)           | Markup within band by category                   | Markup calculation by SKU                | Sales        |

| Bundling / cross-sell              | 05\_basket                         | Prioritize A→B with lift \> 1.2 and min support   | Pair ranking with support/confidence     | Sales        |

