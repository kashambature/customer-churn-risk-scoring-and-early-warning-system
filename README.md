<h1 align="center">Customer Churn Risk Scoring and Early Warning System</h1>
<h3 align="center">SlackOff Churn Risk Analysis</h3>
<p align="center"><em>Identifying and scoring B2B SaaS customers at risk of cancellation</em></p>

## The Business Problem

SlackOff Workspace Solutions is a fictional B2B SaaS company serving 300 business clients on a monthly subscription. From January 2024, revenue started declining month after month. Their most valuable Enterprise clients were quietly disengaging. Some had already cancelled, while others were heading in that direction.

The real problem was not the churn itself. It was the invisibility of it.

The Customer Success team had no early warning system. They had no way of knowing a client was thinking about leaving until the cancellation email had already arrived. By that point, the relationship was gone, and so was the revenue.

This project was built to change that.

---

## The Approach

I analysed 18 months of client activity data, covering more than 1 million rows across logins, feature usage, billing records, and support interactions, to find the behavioural patterns that consistently appear before a client cancels.

The output is a rule-based churn risk scoring engine built entirely in SQL. Each of the 300 clients receives a score from 0 to 100 based on 8 behavioural signals weighted by business impact. The results feed directly into a live Power BI dashboard connected to an MSSQL view.

There is no machine learning and no black box. Every score can be explained signal by signal to a non-technical stakeholder, which is exactly what a Customer Success team needs in order to act with confidence.

---

## What the Data Revealed

1. **Revenue fell by 14.7% in just 6 months**  
   Monthly recurring revenue fell from $245,227 in January 2024 to $209,084 in June 2024. That means the business lost $36,143 every month. If the trend continues unchecked, the annualised impact is $433,716.

2. **Enterprise clients carry a disproportionate share of the risk**  
   Enterprise clients make up only 24.7% of the client base, yet they generate 58.3% of all platform activity. Losing one Enterprise account does not feel like losing one client. It feels like losing five.

3. **The most dangerous clients do not complain loudly**  
   The highest risk accounts showed no complaints, no downgrade requests, and no active negotiation. They had already made their decision. The data identified them through behaviour, not communication.

4. **Logging in does not mean they are staying**  
   Several clients maintained steady login activity while their actual feature engagement collapsed completely. Employees were opening the platform out of habit, while the wider team had quietly migrated to a competing tool. This pattern, which can be described as hollow engagement, is invisible if login activity is the only metric being tracked.

5. **Support frustration is widespread**  
   A total of 36% of all clients showed signs of support frustration. Urgent tickets were going unresolved at a rate of 31%, compared with an industry benchmark of less than 5%. This is not a small pocket of unhappy users. It is a systemic problem that feeds directly into churn risk.
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

### Risk Categories

| Score Range | Category | Action |
|---|---|---|
| 61 to 100 | High Risk | Immediate executive escalation |
| 31 to 60 | At Risk | Customer Success outreach within 2 weeks |
| 0 to 30 | Healthy | Quarterly check-in |

---

## Results

| Metric | Value |
|---|---:|
| High Risk clients requiring immediate intervention | 4 |
| At Risk clients needing outreach within 2 weeks | 52 |
| Monthly recurring revenue at immediate risk | $44,000 |
| Clients who visited the cancellation page in the last 60 days | 47 |

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
