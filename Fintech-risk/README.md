# Fintech Risk Analytics

> Five-domain fraud detection pipeline covering transaction fraud, merchant risk, AML, credit application fraud, and chargeback & payout abuse.

**[Live Dashboard →](https://your-username.github.io/fraud-risk-portfolio/fintech-risk/fraud-analytics-dashboard.html)**  
**[Jupyter Notebook →](./risk_analytics.ipynb)**

---

## Overview

This project demonstrates the quantitative side of fraud and risk analysis — the counterpart to the [Scam Defense Copilot](../scam-defense/)'s qualitative reasoning.

Where the Copilot asks *"what psychological tactics is this scammer using?"*, this project asks *"across 10,000 transactions, which ones are statistically anomalous, and what does the portfolio-level risk look like?"*

Both questions matter in a mature fraud operation.

---

## Part 1 — Interactive Analytics Dashboard

Upload any transaction CSV and get instant analysis. The dashboard auto-detects your column schema and works with any dataset format.

**Supported dataset formats:**
- Kaggle Credit Card Fraud dataset
- PaySim Mobile Payments dataset  
- IEEE-CIS Fraud Detection dataset
- Any CSV with transaction amounts, timestamps, and optional fraud labels

**What it produces:**
- Portfolio-level KPIs (total volume, fraud rate, flagged transactions)
- Amount distribution chart (log scale, fraud vs legitimate overlay)
- 24-hour transaction pattern with fraud rate by hour
- Risk score distribution across the full portfolio
- Risk tier breakdown (LOW / MEDIUM / HIGH / CRITICAL)
- Top 15 highest-risk transactions with per-row explanation
- AI-generated investigation report (Executive Summary, Key Findings, Pattern Analysis, Recommended Actions)

**Scoring methodology:** Rule-based signals (amount vs median, late-night flag, high-risk merchant category, geographic anomaly) combined with behavioral features specific to each dataset type.

---

## Part 2 — Jupyter Notebook: Five-Domain Pipeline

Full analytical pipeline with code, visualizations, and business commentary across five fraud domains.

### Module 1 — Transaction Fraud (Credit Card / Payment)

**Business focus:** Managing the false positive rate alongside detection rate. Every legitimate transaction wrongly blocked has a cost in revenue and customer trust — not just the fraud that gets through.

Key outputs:
- Ensemble model (rule engine + Isolation Forest) with ROC-AUC ~0.87
- Threshold tradeoff analysis — FDR vs FPR across decision thresholds
- Dollar-weighted outcome matrix — what fraud value was blocked vs missed, and at what cost in legitimate volume

### Module 2 — Merchant Risk Scoring

**Business focus:** Portfolio-level risk management for payment facilitators and merchant acquirers.

Signals used: chargeback ratio (Visa/Mastercard threshold: 1%), refund velocity, shared bank account infrastructure, transaction volume spikes, geographic spread.

Key outputs:
- Risk scoring model with tier classification (LOW / MEDIUM / HIGH / CRITICAL)
- KMeans clustering of merchant behavioral profiles
- Portfolio volume at risk from CRITICAL-tier merchants
- Shared infrastructure analysis — merchants sharing bank accounts show 3× higher fraud rates

### Module 3 — AML Network Analysis

**Business focus:** SAR (Suspicious Activity Report) prioritization. Generating too many SARs wastes investigator resources; too few creates regulatory exposure.

Typologies detected:
- **Structuring:** Transaction amounts clustering just below $10,000 CTR threshold
- **Layering:** High pass-through ratio — funds in ≈ funds out, accounts acting as conduits
- **Shell account patterns:** Low transaction count, high value, rapid turnover

Key outputs:
- Account-level AML risk score
- Pass-through ratio analysis
- SAR trigger logic with precision/recall tradeoff

### Module 4 — Credit Application Fraud

**Business focus:** Explainability is a regulatory requirement. Under FCRA and ECOA, adverse action notices must cite specific, understandable reasons — a black-box model cannot comply.

Logistic regression scorecard (intentionally simpler than gradient boosting) with interpretable coefficients:
- Identity velocity (same identity in multiple recent applications)
- Debt-to-income ratio
- Email domain risk (disposable addresses)
- Application form timing (bot-speed vs human-speed)
- Address tenure

### Module 5 — Chargeback & Payout Fraud (Live Streaming / Digital Payments)

**Business focus:** Keeping platform chargeback rates below the Visa (0.9%) and Mastercard (1.0%) thresholds that trigger card network fines and remediation programmes. Equally, detecting payout abuse — fraudulent creators extracting funds through fabricated engagement.

Typologies detected:
- **Friendly fraud:** Real purchases disputed after goods are consumed
- **Chargeback fraud:** Coordinated dispute abuse to extract value
- **Bonus abuse:** Exploiting promotional credits and referral schemes
- **Payout fraud:** New accounts fabricating creator revenue to trigger withdrawals

Key outputs:
- Chargeback rate by country, user segment, account age, and transaction amount
- Seasonal trend analysis — August (promotion abuse) and December (holiday fraud) spike identification
- High-risk user scoring with automated investigation report
- Account age gate analysis — accounts under 30 days show 3–5× the chargeback rate of established users

---

## Design Principles

**Domain knowledge drives feature engineering.**  
The $10k structuring threshold, the 1% Visa/Mastercard chargeback limit, and the SAR pass-through ratio come from regulatory knowledge — not from data. Features grounded in operational expertise consistently outperform generic feature selection.

**False positives have a real cost.**  
Every module includes false positive rate analysis alongside detection rate. Risk analysis means thinking in dollar-weighted terms, not just counts.

**Explainability is not optional.**  
The logistic regression scorecard in Module 4 is simpler than a gradient boosting model by design. Regulatory compliance requires it.

**Unsupervised methods are operationally essential.**  
Fraud labels are scarce, delayed, and never complete. Both Isolation Forest and the AML network features operate without labels — making them deployable on day one.

**Proactive beats reactive.**  
Module 5 demonstrates that fraud spikes are predictable — seasonal patterns, new account windows, and high-risk geographies are known in advance. Tightening controls ahead of these windows, rather than in response to them, is the mark of a mature risk programme.

---

## Model Performance Summary

| Module | Domain | Method | ROC-AUC |
|--------|--------|--------|---------|
| 1. Transaction Fraud | Credit card / CNP | Rule Engine + Isolation Forest | ~0.87 |
| 2. Merchant Risk | Portfolio monitoring | Composite Score + KMeans | ~0.84 |
| 3. AML Detection | Compliance | Network Features + Rules | ~0.82 |
| 4. Credit Fraud | Loan origination | Logistic Regression Scorecard | ~0.83 |
| 5. Chargeback & Payout | Digital payments | Segmentation + Threshold Rules | ~0.81 |

> All results on synthetic data designed to reflect realistic fraud-to-legitimate ratios and behavioral distributions from published industry benchmarks (Nilson Report, FinCEN SAR statistics, Visa/Mastercard dispute data).

---

## About

**Dan Fang** | danfly8888@gmail.com | Ramat Gan, Israel  
Risk Intelligence Analyst (2016–2019) · M.Sc. Machine Learning, Reichman University (2025)

[← Back to Portfolio](../README.md)
