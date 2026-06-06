# SaaS Customer Churn Prediction & Retention Analytics

End-to-end churn analytics on a SaaS subscription dataset: **16 production SQL
queries**, a **Python ML pipeline** (Logistic Regression, Random Forest, XGBoost),
and a **4-page Tableau dashboard** — identifying which accounts will churn and why.

**🔗 [Live Tableau dashboard](https://public.tableau.com/app/profile/poorna.venkat.neelakantam/viz/SaaSCustomerChurnAnalyticsDashboard/Homepage)**

---

## TL;DR

| | |
|---|---|
| **Domain** | SaaS / subscription analytics |
| **Dataset** | RavenStack SaaS Churn (Kaggle, synthetic) — 500 accounts, 33K+ records, 5 relational tables |
| **Stack** | PostgreSQL, Python (Pandas, Scikit-learn, XGBoost), Tableau |
| **Best model** | Random Forest — 85.73% AUC-ROC |
| **Headline result** | $1.1M+ MRR at risk identified; product error rate (not support) is the #1 churn driver |

---

## What this demonstrates
- **Advanced SQL** — 16 queries with multi-table JOINs, CTEs, and window functions (NTILE).
- **Feature engineering** — 10 behavioral features from raw event/usage/support data.
- **Supervised ML** — three models compared with class-imbalance handling and stratified CV.
- **Insight over accuracy** — surfacing a counter-intuitive business driver, not just a score.

## Approach
1. **Model the data** — loaded 5 relational tables into PostgreSQL with a PK/FK schema.
2. **Query** — wrote 16 SQL queries across 5 business categories (churn overview, revenue impact, behavioral patterns, segmentation, advanced cohort/survival analysis).
3. **Engineer features** — built 10 behavioral signals (error rate, engagement score, support resolution rate, onboarding completion, usage trend, etc.).
4. **Train & compare** — Logistic Regression, Random Forest, XGBoost with `class_weight='balanced'` for the 22%/78% imbalance; 5-fold stratified cross-validation.
5. **Rank risk** — produced a ranked at-risk account list (Low / Medium / High).
6. **Visualize** — 4-page Tableau dashboard (Executive Overview, Segmentation, Behavioral Deep Dive, ML Predictions).

## Model results
| Model | Accuracy | Precision | Recall | AUC |
|---|---|---|---|---|
| Logistic Regression | 66.7% | 35.7% | 58.8% | 64.9% |
| **Random Forest** | **84.7%** | **92.3%** | 35.3% | **85.7%** |
| XGBoost | 80.7% | 60.9% | 41.2% | 83.0% |

## Key findings
- **22%** overall churn (110 of 500 accounts); **$1.2M** MRR lost to churn.
- **$1.1M+** MRR at risk from 123 medium-risk active accounts (~$11.7M annualized).
- **Product error rate is the #1 churn driver** — not support quality, which was nearly identical for churned vs retained accounts (contradicted the business assumption).
- DevTools + Enterprise is the worst segment (45.5% churn); event-sourced accounts churn ~3× more than partner-sourced.

> Figures describe what the analysis demonstrates on this synthetic dataset.

## Business questions this answers
- **Which accounts are about to churn, and how much revenue is exposed?** → 123 medium-risk active accounts representing $1.1M+ MRR ($11.7M annualized).
- **What actually drives churn — is it bad support?** → No. **Product error rate** is the #1 driver; support quality was nearly identical for churned vs retained accounts.
- **Which segments are bleeding?** → DevTools + Enterprise (45.5% churn) and event-sourced accounts (~3× the churn of partner-sourced).

## Recommendations
1. **Fix product reliability before adding support headcount.** The data contradicts the assumption that support drives churn — error rate does. Engineering effort on reliability will move churn more than support investment.
2. **Trigger proactive outreach on the 123 medium-risk accounts now** — that's where the $1.1M MRR is recoverable while the accounts are still active, not after they've churned.
3. **Audit the DevTools+Enterprise segment and the event-sourced acquisition channel** — both churn far above average; reassess onboarding/fit for these cohorts and rebalance acquisition spend toward partner-sourced channels.
4. **Deploy the Random Forest at-risk score** (85.7% AUC) as a recurring health signal feeding the CS team's queue.



## Tech stack
PostgreSQL · Python (Pandas, Scikit-learn, XGBoost, Matplotlib, Seaborn) · Tableau Public

## Dataset
RavenStack SaaS Subscription & Churn Analytics (Kaggle, synthetic, MIT License).

## Author
**Poorna Venkat Neelakantam** — [GitHub](https://github.com/poornavenkatn08) · [Tableau Public](https://public.tableau.com/app/profile/poorna.venkat.neelakantam)
