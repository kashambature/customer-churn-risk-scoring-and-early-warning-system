<h1 align="center">Customer Churn Risk Scoring and Early Warning System</h1>
<h3 align="center">SlackOff Churn Risk Analysis</h3>
<p align="center"><em>Identifying and scoring B2B SaaS customers at risk of cancellation</em></p>
<br>
<h2>Business Problem</h2>
<p>SlackOff Workspace Solutions is a fictional B2B SaaS company serving 300 business clients on a monthly subscription. From January 2024, revenue started declining month after month. Their most valuable Enterprise clients were quietly disengaging — some had already cancelled, others were heading in that direction.</p>
<p>The real problem was not the churn itself. It was the invisibility of it.</p>
<p>The Customer Success team had no early warning system. No way of knowing a client was thinking about leaving until the cancellation email had already arrived. By that point, the relationship was gone and so was the revenue.</p>
<p>This project was built to change that.</p>

<hr>

<h2>The Approach</h2>
<p>I analysed 18 months of client activity data — over 1 million rows across logins, feature usage, billing records, and support interactions — to find the behavioural patterns that consistently show up before a client cancels.</p>
<p>The output is a rule-based churn risk scoring engine built entirely in SQL. Every one of the 300 clients receives a score from 0 to 100 based on 8 behavioural signals, weighted by business impact. The results feed directly into a live Power BI dashboard connected to a MSSQL view.</p>
<p>No machine learning. No black box. Every score can be explained signal by signal to a non-technical stakeholder — which is exactly what a Customer Success team needs to act on it with confidence.</p>

<hr>

<h2>What the Data Revealed</h2>
<p><strong>Revenue fell 14.7% in just 6 months</strong> $245,227 MRR in January 2024 dropped to $209,084 by June. That is $36,143 lost every single month — or $433,716 annualised if the trend continues unchecked.</p>
<p><strong>Enterprise clients carry a disproportionate share of the risk</strong> They are only 24.7% of the client base but generate 58.3% of all platform activity. Losing one Enterprise account does not feel like losing one client — it feels like losing five.</p>
<p><strong>The most dangerous clients go quiet — not loud</strong> The highest risk accounts showed no complaints, no downgrade requests, no negotiation. They had already made their decision. The data identified them through behaviour, not communication.</p>
<p><strong>Logging in does not mean they are staying</strong> Several clients maintained steady login activity while their actual feature engagement collapsed entirely. Employees were opening the platform out of habit while the team had quietly migrated to a competing tool. This pattern — hollow engagement — is completely invisible if you only track logins.</p>
<p><strong>36% of all clients are frustrated with support</strong> Urgent tickets are going unresolved at a 31% rate against an industry benchmark of under 5%. This is not a handful of unhappy accounts. It is a systemic failure feeding directly into churn risk across the entire client base.</p>

<hr>

<h2>The Scoring System</h2>
<p>Each client is scored 0 to 100 across 8 signals. The score determines the intervention priority.</p>

<table>
  <thead>
    <tr>
      <th align="left">Signal</th>
      <th align="left">Points</th>
      <th align="left">What it catches</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>🔴 Cancellation page visited</td>
      <td>25</td>
      <td>Documented intent — they literally went to the exit</td>
    </tr>
    <tr>
      <td>🔵 Login drop 40–50%</td>
      <td>15</td>
      <td>People have stopped showing up</td>
    </tr>
    <tr>
      <td>🔵 Feature usage collapsed</td>
      <td>15</td>
      <td>Still logging in but no longer doing real work inside the product</td>
    </tr>
    <tr>
      <td>🟡 Seats below 60% utilised</td>
      <td>10</td>
      <td>Paying for seats nobody is using — finance will notice</td>
    </tr>
    <tr>
      <td>🟡 Support frustration</td>
      <td>10</td>
      <td>High ticket volume, low satisfaction, or unresolved critical issues</td>
    </tr>
    <tr>
      <td>🟡 Payment irregularity</td>
      <td>10</td>
      <td>Failed or late payments in the last 3 months</td>
    </tr>
    <tr>
      <td>🟡 Downgrade inquiry</td>
      <td>10</td>
      <td>Still talking to us — retention window still open</td>
    </tr>
    <tr>
      <td>🟢 No new invites + declining spend</td>
      <td>5</td>
      <td>A growing company adds people. A leaving one stops.</td>
    </tr>
  </tbody>
</table>

<br>

<table>
  <thead>
    <tr>
      <th align="left">Score</th>
      <th align="left">Category</th>
      <th align="left">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>61–100</td>
      <td>🔴 High Risk</td>
      <td>Executive escalation — immediately</td>
    </tr>
    <tr>
      <td>31–60</td>
      <td>🟡 At Risk</td>
      <td>Customer Success outreach within 2 weeks</td>
    </tr>
    <tr>
      <td>0–30</td>
      <td>🟢 Healthy</td>
      <td>Quarterly check-in</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>Results</h2>

<table>
  <thead>
    <tr>
      <th align="left">Metric</th>
      <th align="left">Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>High Risk clients requiring immediate intervention</td>
      <td>4</td>
    </tr>
    <tr>
      <td>At Risk clients needing outreach within 2 weeks</td>
      <td>52</td>
    </tr>
    <tr>
      <td>Monthly recurring revenue at immediate risk</td>
      <td>$44,000</td>
    </tr>
    <tr>
      <td>Clients who visited the cancellation page in the last 60 days</td>
      <td>47</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>Recommendations</h2>
<ul>
  <li>🚨 Escalate the 4 High Risk accounts to executive level immediately — before they cancel, not after.</li>
  <li>🚫 Do not offer discounts to silent exit mode clients. They have moved past negotiation. What they need is a relationship recovery conversation, not a pricing adjustment.</li>
  <li>🔍 Investigate hollow engagement accounts. Stable logins combined with collapsed feature usage is a sign of active competitor migration — not temporary inactivity.</li>
  <li>⚠️ Treat the 36% support frustration rate as a company-wide operational emergency. Fixing support quality alone would reduce churn risk for over a third of the entire client base.</li>
</ul>

<hr>

<h2>Dashboard</h2>
<p>The Power BI dashboard connects live to the <code>vw_churn_risk_scores</code> MSSQL view and gives the Customer Success team everything they need to prioritise their week — without running a single query.</p>

<table>
  <thead>
    <tr>
      <th align="left">Visual</th>
      <th align="left">Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>KPI Cards — High Risk / At Risk / Healthy counts</td>
      <td>Headline summary at a glance</td>
    </tr>
    <tr>
      <td>Revenue at risk KPI card</td>
      <td>Puts a dollar value on the urgency for leadership</td>
    </tr>
    <tr>
      <td>Risk distribution bar chart</td>
      <td>Overall breakdown across all 300 companies</td>
    </tr>
    <tr>
      <td>Stacked bar by plan tier</td>
      <td>Shows which tier carries the highest concentration of risk</td>
    </tr>
    <tr>
      <td>Colour-coded intervention priority table</td>
      <td>Sorted by risk score — CS team knows exactly who to call first</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>Technical Documentation</h2>
<p>The full SQL queries, analytical decisions, and methodology for each section are documented below. These are written for a technical audience — analysts, hiring managers, and senior colleagues who want to understand how the scoring system was built.</p>
<ul>
  <li>📄 Section 1 — Exploratory Data Analysis — Row counts · NULL analysis · referential integrity · monthly trend · business context</li>
  <li>📄 Section 2 — Customer Behaviour Analysis — Engagement baselines · seat utilisation · payment patterns · support frustration · cancellation intent</li>
  <li>📄 Section 3 — Churn Signal Engineering — 8 signals built individually · combined scoring query · risk categorisation · top at-risk accounts</li>
</ul>

<hr>

<p><strong>SlackOff Churn Analysis · SQL · Power BI · GitHub · Jan 2023 — Jun 2024</strong></p>
