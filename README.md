# SaaS Subscription Churn Analysis

A B2B SaaS project management company has grown to 600 customers since 2022, and the board is concerned about churn. This project analyzes subscription-level data and monthly revenue to answer: what's driving churn, which segments are highest-risk, how revenue has trended, and how unit economics (CLV vs. CAC) look across plans.

## Analysis

| Notebook | Question | Key Finding |
|---|---|---|
| [`1. churn_analysis.ipynb`](1.%20churn_analysis.ipynb) | What drives churn, and how has it trended? | `plan`, `billing_cycle`, and `acquisition_channel` all have genuine, independent associations with churn (confirmed via chi-square, logistic regression, and likelihood-ratio tests); `company_size` does not. Highest-risk profile: Starter + Monthly + Referral/Partner (~84% predicted churn probability vs. ~10% for Enterprise + Annual + Organic Search). |
| [`2. revenue_trends.ipynb`](2.%20revenue_trends.ipynb) | How has MRR moved, and what explains the dips? | 5 months had negative net-new MRR. In those months, churn skewed toward Budget Cuts, No Longer Needed, Poor Support, and Missing Features — but standard engagement metrics (support tickets, NPS, feature usage) don't explain the Poor Support / Missing Features spike, pointing to a need for qualitative follow-up. |
| [`3. unit_economics.ipynb`](3.%20unit_economics.ipynb) | What do CLV and CAC look like by plan? | CLV computed per plan from average MRR and average customer lifespan; compared against company-wide CAC (only available at the aggregate monthly level) to rank plans by CLV:CAC ratio, including the trend over time on a trailing 3-month basis. |
| [`4. at_risk_indicators.ipynb`](4.%20at_risk_indicators.ipynb) | Which active customers are at risk today? | A decision tree finds the risk threshold: `feature_usage_pct ≤ 50.5%` AND `nps_score ≤ 6.5` (cross-validated accuracy 88.5%, vs. 77.0% for usage alone). Applied to active customers, **69 of 287 (24.0%)** are currently flagged at-risk. |

All findings are observational, not causal — they identify correlations worth prioritizing for retention efforts, not proven causal levers.

## Tech Stack

- DuckDB + jupysql (SQL against the CSVs)
- pandas
- matplotlib, seaborn (visualization)
- statsmodels, scipy (chi-square tests, logistic regression, likelihood-ratio tests)
- scikit-learn (decision tree, cross-validation)
- JupyterLab

## How to Run

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Run the notebooks in order (`1.` through `4.`) — later notebooks assume the `subscriptions` and `monthly_revenue` tables are loaded the same way as in notebook 1.

## Repo Structure

```
.
├── 1. churn_analysis.ipynb        # Churn rate, drivers, and highest-risk segment
├── 2. revenue_trends.ipynb        # MRR trend, net new MRR, drop-off month analysis
├── 3. unit_economics.ipynb        # CLV by plan vs. CAC, CLV:CAC trend over time
├── 4. at_risk_indicators.ipynb    # Feature usage / NPS at-risk threshold and bucket sizing
├── data/
│   ├── subscriptions.csv
│   └── monthly_revenue.csv
├── figures/                       # Exported chart images
├── requirements.txt
├── .gitignore
└── README.md
```
