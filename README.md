# SaaS Churn, Retention & Activation Analysis

## Why are SaaS customers leaving?

RavenStack had 500 accounts, 352 churned accounts and a 10.41% churn rate.

The goal of this project was not simply to measure churn, but to understand where customers were leaving, why they were leaving, when retention started declining and which product behaviours could be used to improve retention.

I used Python and SQL for the analysis and Looker Studio to turn the findings into an interactive retention dashboard.
<img width="1958" height="1480" alt="RavenStack SaaS Retention Dashboard" src="https://github.com/user-attachments/assets/935e13e1-09d3-4aa7-be49-9bf7930840b8" />
## Business Problem

RavenStack needed to understand the drivers of customer churn and identify where Product, Customer Success and Support should focus their retention efforts.

The analysis focused on five questions:

1. Where is churn concentrated?
2. Why are customers leaving?
3. Does product activation appear to influence retention?
4. When does retention begin to decline?
5. Can customer support provide an early signal of churn?

## Key Results

| Metric | Result |
|---|---:|
| Total Accounts | 500 |
| Churned Accounts | 352 |
| Churn Rate | 10.41% |
| MRR | $63.29M |
| NRR | 100% |
| Highest Industry Churn | 30.97% |
| Unrated Support Tickets | 41.3% |

### What stood out

- DevTools had the highest industry churn at 30.97%.
- Features, support and budget were among the largest recorded churn reasons.
- Feature-level retention varied considerably.
- Some cohorts declined below 90% retention as they matured.
- 41.3% of support tickets had no rating.
## Approach

The analysis followed five stages:

Raw Data
↓
Data Cleaning
↓
Exploratory Analysis
↓
Churn, Retention & Activation Analysis
↓
Looker Studio Dashboard
### 1. Data Preparation
Python was used to inspect the datasets, handle missing values, standardize fields and prepare the data for analysis.
### 2. SQL Analysis
SQL was used to structure the business analysis around churn, customer segments, cohorts, activation, revenue and support.
### 3. Python Analysis
Python was used for exploratory analysis, feature-level analysis and analytical validation.
### 4. Dashboard
Looker Studio was used to bring the findings together into an interactive dashboard focused on business decisions rather than simply displaying metrics.
# 1. Churn Analysis

## Business Question

Where is customer churn concentrated?

DevTools recorded the highest industry churn at 30.97%.

![Churn by Industry](visuals/churn_segments.png)

## Insight
Churn is not evenly distributed across the customer base. DevTools represents the clearest segment-level retention opportunity.
## Recommendation
Run a focused retention investigation for DevTools customers, looking at onboarding, product adoption, support interactions and renewal behaviour.




















