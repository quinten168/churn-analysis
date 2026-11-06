# Churn Analysis Project

You are a business analyst at a B2B SaaS company that sells project management software. The leadership team is preparing for a board meeting and needs a clear picture of revenue trends, customer retention, and churn drivers. In this project you will analyze subscription data, monthly recurring revenue (MRR), and customer behavior to identify what is causing churn and where the best opportunities for revenue growth are. This type of analysis is common at SaaS startups and is directly relevant to roles in finance, product analytics, and growth.

## Instructions

CloudTask Pro is a SaaS company that has grown from 0 to 600 customers since 2022. While revenue has been growing, the board has raised concerns about a high churn rate. The CFO wants to understand the monthly churn trends, which customer segments are most at risk, and what the company's unit economics look like (MRR per customer, customer acquisition cost vs. lifetime value). You have access to a subscription-level dataset with customer details, plan info, and churn status, as well as a monthly revenue summary.

## Questions to Answer

1. What is the overall churn rate, and how has the monthly churn rate trended over the past 4 years? Is churn improving or getting worse?
2. Which subscription plan (Starter, Professional, Business, Enterprise) has the highest churn rate? Does billing cycle (monthly vs. annual) significantly impact retention?
3. What are the top 3 reasons customers churn, and do these reasons differ by plan type or company size?
4. Calculate the average Customer Lifetime Value (CLV) by plan. Compare this to the Customer Acquisition Cost (CAC). Which plans are the most and least profitable?

## Recommended Tech Stack

- SQL
- Excel
- Power BI

## What You Should Do

### 1. Import and Explore
- Load both CSVs.
- Understand the structure, check for missing values, and get familiar with the fields.

### 2. Churn Analysis
- Calculate churn rate by plan, billing cycle, acquisition channel, and company size.
- Identify the highest-risk segments.

### 3. Revenue Trends
- Plot monthly MRR over time.
- Calculate net revenue retention (new MRR minus churned MRR). Identify months with unusual spikes or dips.

### 4. Unit Economics
- Compute average CLV per plan using average MRR and average customer lifespan.
- Compare CLV to CAC to determine the CLV:CAC ratio.

### 5. At-Risk Indicators
- Analyze the relationship between feature usage, NPS, and churn.
- Define a threshold (e.g., feature usage below X%) that flags at-risk customers, and estimate how many current customers fall into that bucket.
