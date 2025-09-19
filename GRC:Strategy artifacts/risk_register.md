\# Risk Register — WIWO-store

| ID | Risk                               | Prob | Impact | Level | Signal/Trigger                         | SQL Control/Rule                 | Owner       | Status |

|----|------------------------------------|------|--------|-------|----------------------------------------|----------------------------------|-------------|--------|

| R1 | Orphan fact→dim customer keys      | M    | H      | High  | OrphanCustomerKeys \> 0                 | 00\_data\_quality\_checks           | Data Eng    | Active |

| R2 | High 'Unknown' share in dimensions | M    | M      | Med   | Unknowns by dimension \> threshold      | 00\_data\_quality\_checks           | Data Stew.  | Active |

| R3 | Revenue volatility                 | M    | M      | Med   | Daily |z| ≥ 2                                | Daily outliers (z-score)         | Operations  | Active |

| R4 | Territory saturation/overlap       | L    | M      | Med   | Wingtip Toys \>3 per ZIP                | 02\_clusters                      | Sales       | Active |

| R5 | Unprofitable/incoherent bundles    | M    | L      | Med   | Lift ≤ 1 or low support                | 05\_basket                        | Sales       | Active |  
