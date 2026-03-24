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

1. **Revenue declined sharply over a short period**  
   Monthly recurring revenue fell from **$245,227 in January 2024 to $209,084 in June 2024**, representing a **14.7% decline in just six months**. This showed that customer churn was already creating a measurable financial impact on the business.

2. **Enterprise clients carried a disproportionate share of the exposure**  
   Although Enterprise clients made up only **24.7%** of the customer base, they accounted for **58.3%** of total platform activity. This meant that losing even a small number of these accounts could have an outsized effect on both usage and recurring revenue.

3. **The highest-risk clients often showed silent disengagement**  
   The most vulnerable accounts did not always complain, request downgrades, or signal dissatisfaction directly. In many cases, the warning signs appeared first in their behaviour, not in their communication.

4. **Login activity alone was not a reliable measure of retention**  
   Some clients continued to log in regularly even while their deeper feature usage dropped significantly. This suggested that surface-level activity could hide underlying disengagement and possible migration to competing tools.

5. **Support issues were emerging as a major churn driver**  
   A total of **36%** of clients showed signs of support frustration, while urgent tickets remained unresolved at a rate of **31%**, far above normal expectations. This pointed to operational service quality as a meaningful contributor to churn risk.

6. **Cancellation-page activity reinforced the presence of active exit intent**  
   Beyond broader behavioural decline, some clients also showed more direct signs of churn intent by viewing the cancellation page. This strengthened the case for treating cancellation-page activity as one of the strongest warning signals in the scoring framework.
---

## The Scoring System

Each client is scored from 0 to 100 across 8 signals. The score determines the level of intervention required.

| Signal | Points | What it catches |
|---|---:|---|
| Cancellation page visited | 25 | Clear evidence of exit intent |
| Login drop of 40% to 50% | 15 | People have stopped showing up |
| Feature usage collapsed | 15 | They still log in, but no longer do meaningful work inside the product |
| Seats below 60% utilised | 10 | They are paying for seats that nobody is using |
| Support frustration | 10 | High ticket volume, low satisfaction, or unresolved critical issues |
| Payment irregularity | 10 | Failed or late payments within the last 3 months |
| Downgrade inquiry | 10 | They are still engaging, so there is still a retention window |
| No new invites and declining spend | 5 | Growing companies add people, while exiting companies stop |

## Churn Signals and Weights

- **Cancellation page visited** — **25 points**: Direct exit intent  
- **Login drop of 40% to 50%** — **15 points**: Reduced engagement  
- **Feature usage collapsed** — **15 points**: Low product dependence  
- **Seats below 60% utilised** — **10 points**: Underused subscription value  
- **Support frustration** — **10 points**: Service dissatisfaction  
- **Payment irregularity** — **10 points**: Billing instability  
- **Downgrade inquiry** — **10 points**: Reduced commitment  
- **No new invites and declining spend** — **5 points**: Slowing account growth  

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
