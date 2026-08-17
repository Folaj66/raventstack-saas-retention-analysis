# RavenStack: The SaaS Churn Problem Is Bigger Than the Churn Rate

## Finding Where Customers Leave, Why They Leave and What the Team Should Do About It
<img width="1408" height="768" alt="image_cf1b5df4" src="https://github.com/user-attachments/assets/e1c092a8-7de7-4a36-9d88-d63932193ebb" />

RavenStack keep acquiring customers and still struggle to grow if too many customers are leaving through the other side.

That was the problem I wanted to investigate with RavenStack.

## Data & Methodology
**Dataset:** The dataset was downloaded on Kaggle using the [Link](https://www.kaggle.com/datasets/rivalytics/saas-subscription-and-churn-analytics-dataset)

**Source tables:** accounts (500 rows), subscriptions (5,000 rows), feature_usage (25,000 rows), support_tickets (2,000 rows), churn_events (600 rows).

**Cleaning steps applied:**
- Converted all date fields to datetime, coercing invalid entries to null
- Flagged active vs. ended subscriptions based on missing end_date, then filled missing end_date with the analysis date (2024-12-31) to calculate duration
- Imputed missing satisfaction scores by priority-group median, and tracked which scores were originally missing as a separate flag rather than hiding the gap
- Filled missing churn feedback text with an explicit "No feedback provided" label and kept a missing-feedback flag for reporting
- Removed duplicate rows across all five tables (zero found on this pass)

**Key distinction that matters for interpretation:** account-level churn (accounts table, churn_flag) shows 110 of 500 accounts (22%) as churned. The churn_events table shows 352 unique accounts with at least one churn event, because subscriptions can churn and reactivate independently of the account's final status. Read "352 churned accounts" as subscription-level churn touches, not 352 lost customers. The 22% figure is the one to use for board-level churn reporting.

**Derived analysis tables:** plan-tier churn, industry churn, country churn, churn reason breakdown, support experience by account, 7-day activation behavior by account, feature-level activation and retention, cohort retention matrix (by subscription start month), monthly revenue trend, monthly churn trend, and a simplified NRR table using monthly active MRR against churned MRR.

**Known limitation:** the NRR table calculates gross revenue retention using aggregate monthly MRR, not upgrade/downgrade-adjusted net revenue per account. Treat NRR figures in this dataset as directional, not board-ready, until recalculated at the account level.


<img width="1946" height="1465" alt="Screenshot 2026-08-17 082008" src="https://github.com/user-attachments/assets/561806be-e9eb-4dce-9eab-0075af16b8bb" />

The company has 500 accounts, 352 churned accounts, a 10.41% churn rate, $63.29M in MRR and 100% NRR.

At first glance, the 10.41% churn rate is the obvious problem.
But the more useful question is:

**Where is that churn coming from?**

That is what this analysis was built to answer.

## The Task

I wanted to move beyond a single churn number and understand the customer journey behind it.

I looked at:

* Customer plans and industries
* Churn reasons
* Monthly churn
* Product activation
* Feature usage
* Cohort retention
* Customer support
* Revenue retention

The goal was simple.

Find the areas where the team can actually take action.

## The First Finding: Churn Is Not Evenly Distributed

The industry analysis immediately pointed to one segment.

DevTools had a 30.97% churn rate.

FinTech followed at 22.32%, HealthTech at 21.88%, EdTech at 16.46% and Cybersecurity at 16%.

That changes the question.

Instead of asking:

"How do we reduce churn?"

The team should be asking:

"Why are DevTools customers leaving at almost twice the rate of some other industries?"

That is a much more useful business question.

### What I would do

Start with DevTools.

Review their onboarding, feature adoption, support history and cancellation reasons.

Then build a retention intervention specifically for this segment.

A generic retention campaign across all customers is unlikely to be as useful as fixing the customer group where the problem is most visible.

## The Second Finding: Product Value Is Showing Up in the Churn Reasons

Features were the largest recorded churn reason at 114 cases.

Support and budget followed at 104 cases each.

Unknown reasons accounted for 95 cases, while competitor and pricing accounted for 92 and 91.

This is important because the largest problem is not simply price.

Customers are also leaving because they do not see enough value in the product.

That puts Product directly in the retention conversation.

### What I would do

Review the features customers were using before they churned.

Then compare those behaviours with customers who stayed.

If customers who adopt certain features retain better, those features should become part of the onboarding journey.

## The Product Usage Analysis Made This More Interesting

The activation analysis showed 22% churned customers versus 78% active or retained customers.

But the feature analysis showed that retention is not the same across features.

Feature_22 and feature_34 recorded 100% retention in the displayed sample.

Feature_38 was at 63.64%.

Feature_16 was at 66.67%.

Feature_26 was at 70%.

This does not prove that using a specific feature causes retention.

But it gives Product a clear experiment to run.

### What I would do

Take the strongest-retention features and test whether introducing them earlier in the customer journey improves retention.

Make it a first-seven-day onboarding experiment.

If the treatment group retains better than the control group, the company has a measurable activation lever.

## Then the Cohorts Tell Another Story

The cohort matrix starts strongly.

Many cohorts begin at 100% retention and gradually decline as they mature, with some eventually falling into the high 80% range.

The active subscription volume also rose from 607 in Q1 2023 to 3,917 in Q1 2024 before falling to 1,754 by Q4 2024.

This tells me the company needs to pay attention to what happens after the initial customer acquisition period.

Customers may be getting through the door, but some are losing value as they progress through the lifecycle.

### What I would do

Build a 30, 60, 90 and 180-day retention process.

At each stage, look at product activity, support tickets and customer engagement.

If activity starts falling, Customer Success should intervene before the customer reaches cancellation.

## Support Is Another Signal

One number caught my attention.

41.3% of support tickets were not rated.

Only 20.3% were rated Very Good, 19.8% Good and 18.7% Excellent.

That does not automatically mean support is poor.

It means there is a large part of the support experience that the company cannot properly evaluate.

The dashboard also shows customers with high ticket volumes and several unrated tickets.

That is useful.

A customer opening multiple tickets and giving no feedback should not be treated the same way as a customer with one resolved ticket.

### What I would do

Make post-ticket feedback easier to capture.

Then flag customers with repeated tickets and high unrated feedback for Customer Success follow-up.

That turns support activity into an early retention signal.

## There Is Also a Monthly Churn Problem

The monthly data becomes more concerning toward the end of 2024.

December recorded 117 churned accounts with a 19.2% churn rate.

November recorded 68 churned accounts at 12.63%.

October recorded 66 at 13.67%.

A jump like this needs an explanation.

Was it concentrated in one industry?

One plan?

One cohort?

A renewal period?

A product issue?

The dashboard gives us the starting point, but the next step is to break that spike down.

### What I would do

Make monthly churn reviews mandatory whenever churn moves materially above the normal range.

Break the change down by plan, industry, cohort and reason before deciding what action to take.

## What I Would Prioritise

If I were sitting with the RavenStack leadership team, these would be my first five actions:

1. Start with DevTools and investigate its 30.97% churn.
2. Fix the gaps around product value and feature adoption.
3. Test a first-seven-day activation flow using the strongest-retention features.
4. Introduce 30, 60, 90 and 180-day retention checkpoints.
5. Turn support activity and unrated feedback into an early-warning process.

I would also make one measurement change.

Reduce the 95 "unknown" churn reasons.

If the company cannot explain why customers are leaving, it becomes much harder to decide what to fix.

Check out the [DASHBOARD](https://datastudio.google.com/s/qyPfINw2DN4) and drop your feedback

## Final Thought

The biggest lesson from this project is that churn should not sit inside one Customer Success report.

It touches Product, Support, Revenue and Customer Success.

The useful question is not:

**"What is our churn rate?"**

It is:

**"Which customers are becoming risky, why are they becoming risky, and what can we do before they leave?"**

That is where the retention opportunity is.
