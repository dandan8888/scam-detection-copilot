# Fintech Risk Analytics — SQL + Five-Domain Detection Pipeline

**Dan Fang** · Risk Intelligence · M.Sc. Machine Learning, Reichman University  
danfly8888@gmail.com · Ramat Gan, Israel

**[Live Dashboard →](https://dandan8888.github.io/Fraud_Risk_Intelligence_Portfolio/Fintech-risk/risk-analytics-dashboard.html)**  
**[Jupyter Notebook →](./risk_analytics.ipynb)**
---
---

## Skills at a Glance

| Category | What's demonstrated |
|---|---|
| **SQL** | JOINs, GROUP BY, HAVING, CASE WHEN, window aggregations, subqueries (DuckDB) |
| **Data Analysis** | EDA, feature engineering, cohort-style segmentation, dollar-weighted metrics |
| **Machine Learning** | Isolation Forest, KMeans, Logistic Regression, ROC/PR analysis |
| **Dashboards** | Interactive HTML dashboard (Chart.js), matplotlib/seaborn multi-panel layouts |
| **Business Thinking** | Every module ends with a specific, actionable recommendation |
| **Domain Knowledge** | Visa/Mastercard thresholds, BSA/FATF typologies, FCRA/ECOA compliance |

---

## Part 1 — Interactive Analytics Dashboard

Upload any transaction CSV and get instant analysis. The dashboard auto-detects your column schema.

**Supported formats:** Kaggle Credit Card Fraud · PaySim Mobile Payments · IEEE-CIS · any CSV with transaction amounts and optional fraud labels

**What it produces:**
- Portfolio-level KPIs (total volume, fraud rate, flagged transactions)
- Amount distribution (log scale, fraud vs legitimate overlay)
- 24-hour transaction pattern with fraud rate by hour
- Risk tier breakdown (LOW / MEDIUM / HIGH / CRITICAL)
- Top 15 highest-risk transactions with per-row explanation
- AI-generated investigation report (Executive Summary, Key Findings, Recommended Actions)

---

## Part 2 — Jupyter Notebook: SQL + Five-Domain Pipeline

### Module 0 — SQL Exploratory Analysis

Before reaching for Python, a data analyst reaches for SQL. This module runs five analytical queries directly on the datasets using DuckDB — the same questions a DA would ask on day one of an investigation.

**Business questions answered:**

| Query | Question | Key technique |
|---|---|---|
| Q1 | Which merchant categories generate the most fraud *value* — not just count? | GROUP BY, CASE WHEN, NULLIF |
| Q2 | Which hours of day need tighter real-time controls? | Aggregation, percentile threshold |
| Q3 | Which customer segment has the highest dollar exposure? | Dollar-weighted metrics vs count-based |
| Q4 | Is HIGH/CRITICAL risk concentrated in specific merchant types? | Multi-condition HAVING, portfolio view |
| Q5 | Which accounts show velocity fraud signatures detectable with SQL alone? | HAVING, fraud rate filter, DISTINCT count |

Each query ends with a plain-English business recommendation.

---

### Module 1 — Transaction Fraud Detection

**Business question:** Which transactions should we block — and at what cost in legitimate volume?

The core trade-off in fraud detection is not accuracy. It is false positives. A rule that blocks 95% of fraud but also blocks 5% of legitimate customers costs more in lost revenue than the fraud it prevents. This module quantifies that trade-off explicitly.

Key outputs:
- Ensemble model (rule engine + Isolation Forest), ROC-AUC ~0.87
- Threshold tradeoff analysis — Fraud Detection Rate vs False Positive Rate across decision thresholds
- Dollar-weighted outcome matrix — fraud value blocked vs missed, cost in legitimate volume

---

### Module 2 — Merchant Risk Scoring

**Business question:** Which merchants in our portfolio are putting us at risk of card network fines?

Signals: chargeback ratio (Visa/Mastercard threshold: 1%), refund velocity, shared bank account infrastructure, transaction volume spikes, geographic spread.

Key outputs:
- Composite risk scoring with tier classification (LOW / MEDIUM / HIGH / CRITICAL)
- KMeans clustering of merchant behavioral profiles — 6 business types, 500 merchants
- Portfolio volume at risk from HIGH/CRITICAL-tier merchants
- Shared infrastructure finding: merchants sharing bank accounts show 3× higher fraud rates

---

### Module 3 — AML Network Analysis

**Business question:** Which accounts should we file a SAR on — and how do we prioritise when investigator capacity is limited?

Too many SARs waste investigator time. Too few creates regulatory exposure. This module builds a prioritisation score grounded in BSA/FATF typologies.

Typologies detected: structuring below the $10k CTR threshold · layering (high pass-through ratio) · shell account patterns

Key outputs:
- Account-level AML risk score with SAR trigger logic
- Pass-through ratio analysis
- Precision/recall tradeoff for SAR prioritisation

---

### Module 4 — Credit Application Fraud

**Business question:** Which loan applications are fraudulent — and can we explain *why* in terms a compliance officer can sign off on?

Under FCRA and ECOA, adverse action notices must cite specific, understandable reasons. A black-box model cannot comply. Logistic regression is the right tool here — not gradient boosting.

Key outputs:
- Interpretable scorecard with feature coefficients (identity velocity, DTI ratio, email domain risk, form timing, address tenure)
- Adverse action analysis
- ROC-AUC ~0.83 with full explainability

---

### Module 5 — Chargeback & Payout Fraud

**Business question:** Are we at risk of breaching Visa/Mastercard chargeback thresholds — and where do we intervene first?

Key outputs:
- Chargeback rate by country, user segment, account age, and transaction amount
- Seasonal trend analysis — August (promotion abuse) and December (holiday fraud) spikes
- Account age gate finding: accounts under 30 days show 3–5× the chargeback rate of established users
- High-risk user scoring with automated investigation report

---

## Design Principles

**SQL before models.** Analytical questions deserve SQL answers first. Module 0 demonstrates that a significant share of actionable fraud intelligence can be extracted with queries alone — before any ML is needed.

**Business recommendations, not just charts.** Every module ends with a specific recommendation framed in terms a product manager or compliance officer can act on.

**Dollar-weighted thinking.** Fraud rate (%) is a weak metric. Dollar value at risk is what the business cares about. Every module uses dollar-weighted metrics as the primary lens.

**Domain knowledge drives feature engineering.** The $10k structuring threshold, the 1% chargeback limit, and the SAR pass-through ratio come from operational experience — not from data. Features grounded in domain knowledge consistently outperform generic feature selection.

**Explainability is not optional.** Module 4 uses logistic regression by design. Regulatory compliance requires it.

---

## Results Summary

| Module | Domain | SQL / Method | AUC | Business Metric |
|---|---|---|---|---|
| 0. SQL Analysis | Cross-domain | DuckDB SQL | — | 5 business recommendations |
| 1. Transaction Fraud | Card / CNP | Rule Engine + Isolation Forest | ~0.87 | FDR vs FPR threshold curve |
| 2. Merchant Risk | Portfolio | Composite Score + KMeans | ~0.84 | % portfolio volume at risk |
| 3. AML Detection | Compliance | Network Features + Rules | ~0.82 | SAR precision/recall |
| 4. Credit Fraud | Loan origination | Logistic Regression Scorecard | ~0.83 | Adverse action explainability |
| 5. Chargeback & Payout | Digital payments | Segmentation + Rules | ~0.81 | Chargeback rate vs network threshold |

> All results on synthetic data modelled on published industry benchmarks: Nilson Report fraud rates, FinCEN SAR statistics, Visa/Mastercard dispute thresholds.

---
---
[⬅️ Back to Main Portfolio](https://github.com/dandan8888/Fraud_Risk_Intelligence_Portfolio/tree/main/Fintech-risk)
