<h1 align="center">Customer Churn Risk Scoring and Early Warning System</h1>
<h3 align="center">SlackOff Churn Risk Analysis</h3>
<p align="center"><em>Identifying and scoring B2B SaaS customers at risk of cancellation</em></p>

## The Business Problem

SlackOff Workspace Solutions is a fictional B2B SaaS company serving 300 business clients through seat-based monthly subscriptions across Starter, Growth, and Enterprise plans. In 2024, the business began to experience declining recurring revenue as high-value clients quietly reduced engagement and in some cases, cancelled without warning. The main challenge was the lack of visibility into early churn behaviour. Customer Success could only react after cancellation had already happened, when both the relationship and the revenue were already lost. The purpose of this analysis was to uncover early warning signs of churn, measure the revenue at risk, and create a practical basis for proactive retention action.

---
## The Approach

To solve the problem, I analysed 18 months of client activity data, covering more than 1 million records across logins, feature usage, billing behaviour, and support interactions. The goal was to identify the behavioural signals that consistently appear before cancellation. Using these patterns, I built a rule-based churn risk scoring model in SQL that assigned each of the 300 clients a score from 0 to 100 based on 8 weighted indicators. The final output was connected to a live Power BI dashboard through an MSSQL view, making the results easy to monitor and act on. This gave the Customer Success team a practical way to spot early churn risk, understand the revenue at stake, and prioritise intervention before customers were lost.

---
## What the Data Revealed

1. **Revenue declined sharply:** Monthly recurring revenue fell from **$245,227 in January 2024 to $209,084 in June 2024**, showing that churn was already creating a measurable financial impact.

2. **Enterprise clients carried outsized exposure:** Although they made up only **24.7%** of the customer base, they accounted for **58.3%** of total platform activity, meaning a small number of losses could have a major revenue effect.

3. **High-risk clients often disengaged silently:** The most vulnerable accounts did not always complain or request downgrades, as the warning signs appeared first in their behaviour rather than in direct communication.

4. **Login activity alone was misleading:** Some clients continued logging in regularly even as deeper feature usage dropped significantly, suggesting hidden disengagement and possible migration to competitors.

5. **Support issues emerged as a major churn driver:** About **36%** of clients showed signs of support frustration, while urgent tickets remained unresolved at a rate of **31%**, far above normal expectations.

6. **Cancellation-page activity confirmed exit intent:** Some clients went beyond passive disengagement and directly viewed the cancellation page, reinforcing its value as a strong churn signal.
---

## Churn Risk Signals

- **Cancellation page visited** (**25 points**): Direct exit intent  
- **Login drop of 40% to 50%** (**15 points**): Reduced engagement  
- **Feature usage collapsed** (**15 points**): Low product dependence  
- **Seats below 60% utilised** (**10 points**): Underused subscription value  
- **Support frustration** (**10 points**): Service dissatisfaction  
- **Payment irregularity** (**10 points**): Billing instability  
- **Downgrade inquiry** (**10 points**): Reduced commitment  
- **No new invites and declining spend** (**5 points**): Slowing account growth
---

### Risk Categories

The churn risk scores were grouped into three categories to guide action. Clients with scores between **61 and 100** were classified as **High Risk** and required immediate executive escalation. Clients with scores between **31 and 60** were classified as **At Risk** and were marked for Customer Success outreach within two weeks. Clients with scores between **0 and 30** were classified as **Healthy** and only required a routine quarterly check-in.

---

## Results

The final scoring model identified **4 High Risk clients** that required immediate intervention and **52 At Risk clients** that needed Customer Success outreach within two weeks. It also revealed that **$44,000 in monthly recurring revenue** was exposed to immediate churn risk. In addition, **47 clients** had visited the cancellation page within the last 60 days, signalling a notable level of active cancellation intent.

---

## Recommendations

- Escalate the 4 High Risk accounts to executive level immediately, before they cancel rather than after.
- Do not offer discounts to silent exit mode clients. They have moved beyond negotiation. What they need is a relationship recovery conversation, not a pricing adjustment.
- Investigate hollow engagement accounts. Stable logins combined with collapsed feature usage suggest active migration to a competitor, not temporary inactivity.
- Treat the 36% support frustration rate as a company-wide operational emergency. Improving support quality alone could reduce churn risk across more than one-third of the client base.

---

## Dashboard


---

## Technical Documentation

The full SQL queries, analytical decisions, and methodology for each section are documented below. These materials are intended for a technical audience, including analysts, hiring managers, and senior colleagues who want to understand how the scoring system was built.

- **Section 1: Exploratory Data Analysis**  
  Row counts, NULL analysis, referential integrity, monthly trend, and business context.

- **Section 2: Customer Behaviour Analysis**  
  Engagement baselines, seat utilisation, payment patterns, support frustration, and cancellation intent.

- **Section 3: Churn Signal Engineering**  
  The 8 signals built individually, the combined scoring query, risk categorisation, and the top at-risk accounts.

---

**SlackOff Churn Analysis | SQL | Power BI | GitHub | Jan 2023 to Jun 2024**
