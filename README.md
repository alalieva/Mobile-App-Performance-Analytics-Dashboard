# Mobile App Performance - Analytics Dashboard
<img width="493" height="480" alt="Screenshot 2026-03-09 at 18 21 43" src="https://github.com/user-attachments/assets/6c72d16a-8640-4808-815c-1b91eee19ce7" />

<img width="491" height="480" alt="Screenshot 2026-03-09 at 18 22 15" src="https://github.com/user-attachments/assets/ce3d52e6-6104-436c-9991-f91e9029866c" />

This project analyzes user behavior, retention, churn and revenue performance of a mobile application during 2025.

The analysis combines product analytics metrics, cohort retention analysis and revenue insights to understand how user engagement impacts business performance.

The dashboard was built using Tableau. 
[You can explore the interactive Tableau dashboard here](https://public.tableau.com/app/profile/alesia.alieva/viz/MobileAppPerformance/Users).

⚠️ The dataset used in this project is synthetic and generated for demonstration purposes.

## :dart: Project Goal

The goal of this project is to evaluate product health and monetization performance of a mobile application by analyzing:  
• user growth  
• user engagement  
• retention dynamics  
• churn patterns  
• revenue generation  

The analysis focuses on identifying key behavioral patterns that influence long-term product performance.

## :open_file_folder: Data Model 
The dashboard is built using a synthetic dataset that simulates the data architecture of a mobile application analytics system.
The dataset consists of four core tables representing users, sessions, subscriptions and payments.

<details>
<summary>View Data Model Diagram</summary>  
  
```mermaid
erDiagram

    USERS {
        string user_id PK
        date registration_date
        string gender
        int age
        string country
        string acquisition_channel
        string device_os
    }

    SESSIONS {
        string session_id PK
        string user_id FK
        date session_date
        int duration
    }

    SUBSCRIPTIONS {
        string subscription_id PK
        string user_id FK
        string subscription_type
        string billing_period
        date subscription_start_date
        date subscription_end_date
        string churn_reason
    }

    PAYMENTS {
        string payment_id PK
        string subscription_id FK
        string user_id FK
        float amount
        string payment_status
        date payment_date
    }

    USERS ||--o{ SESSIONS : activity
    USERS ||--o{ SUBSCRIPTIONS : subscriptions
    SUBSCRIPTIONS ||--o{ PAYMENTS : payments
 ```
</details> 

## :bar_chart: Dashboard Overview

The dashboard consists of two analytical sections.

###  User Analytics  
This section focuses on user growth, engagement and retention.  
<img width="1391" height="880" alt="Screenshot 2026-03-09 at 18 21 43" src="https://github.com/user-attachments/assets/594c3b1c-385d-454b-ae9f-42510d4ec8ec" />  
<ins>**Key KPIs:** </ins> 
- **Active Users** — Unique users who had at least one session during the selected period.
- **New Users** — Users who registered during the selected period.
- **Paying Users** — Users who had at least one successful payment during the selected period.
- **Churned Users / Churn Rate** — Users whose paid subscription ended during the selected period. 

<ins>**Additional analysis:** </ins> 
- Demographic distribution of users (gender, age, country) by users type.
- Monthly Churn Rate trend for 2025.
- Cohort Retention Heatmap.

### Revenue Analytics
This section evaluates monetization performance. These metrics help identify how effectively the product converts user activity into revenue.
<img width="1393" height="886" alt="Screenshot 2026-03-09 at 18 22 15" src="https://github.com/user-attachments/assets/a8fe647d-1637-4977-8c12-51bac73d996a" />  
<ins>**Key KPIs:** </ins>  
-**ARPU (Average Revenue Per User)** — The average revenue generated per active user per month. This metric reflects the monetization efficiency of the entire user base, including free users._(Values may appear inflated due to synthetic data where 40% of users are paying.)_   
-**ARPPU (Average Revenue Per Paying User**) — The average revenue generated per paying user per month. Unlike ARPU, this metric excludes free users.  
-**MRR (Monthly Recurring Revenue)** — Normalized monthly revenue.   
  > Revenue — Actual cash received in a given month.  
  Unlike Revenue MRR converts all subscription types to their monthly equivalent.  
  Annual subscriptions ($100/$200) are divided by 12 to reflect their monthly contribution.  
  Revenue in the month of a large annual payment will be higher than MRR; in the following months it will appear lower.
>      
-**Refund Rate(%)** — The percentage of refunded transactions out of the total number of payment transactions in a given month.  

<ins>**Additional analysis:** </ins>  
- Revenue distribution by Device OS (iOS / Android).
- Paid Subscriptions by Billing type. 
- Revenue by acquisition channel. 
- Analysis of user churn reasons. 
- Comparison of MRR vs Revenue. 

## :paperclip: Dashboard Interactivity  
The dashboard includes several interactive features that allow exploring the metrics across different time dimensions and user segments.  

### User Analytics Section  
The KPI cards support dynamic time selection and can be viewed for the following periods:
- Last 7 days  
- Month  
- Quarter  
- Year  

Demographic distributions **(gender, age, country)** can be filtered by **user type (active, new, paying, churned users)**.

### Revenue Analytics Section  
Revenue KPIs are displayed as **static metrics for the latest complete month (December 2025)**, representing the most recent snapshot of business performance.  
Additional charts allow monthly analysis throughout **2025**, including:  
- Revenue distribution by **Device OS** (iOS / Android)  
- Paid subscriptions by **Billing type** 
- Revenue by **Acquisition channel** 
- Analysis of user **Churn reasons**

### Time Coverage
The underlying dataset contains data for 2024–2025, while the dashboard focuses on 2025 as the primary analysis period.  
Data from 2024 is used as a reference period to calculate comparisons with previous periods (e.g., previous month, quarter or year).

### Previous Period Comparison for KPI metric
**Previous Last 7 days**  
**PM** — Previous Month  
**PQ**  — Previous Quarter  
**PY**   — Previous Year  
The change in pp means percentage points.  
>_For Churned Users the delta is interpreted inversely: a negative delta indicates an improvement (fewer users churned)._  
_For Refund Rate%  the delta is interpreted inversely: a negative delta indicates an improvement (fewer refunds)._
>

## :fountain_pen: Key Insights

The insights below represent examples of patterns observed in the dashboard.  
Since the dashboard is interactive, metrics can be analyzed across different time periods (last 7 days, month, quarter, year) and user segments. 

### Short-term Trends (Recent Performance)  
**Decline in New User Acquisition**  
New user registrations decreased by 22% week-over-week, indicating a slowdown in acquisition. This may be related to seasonal effects at the end of December or reduced marketing activity.

**Increase in User Churn**  
Churned users increased by 57% WoW, which is the most concerning short-term signal. Combined with lower acquisition this creates pressure on the total user base.

**Stable Active User Base**  
Despite acquisition and churn fluctuations, the number of active users remained almost unchanged (-0.99%), suggesting that the product maintains a stable core audience.

**Continued Growth of Paying Users**  
The number of paying users increased by 4.8% WoW, indicating that existing users continue converting to paid plans even during slower acquisition periods.

### Long-term Trends (Product & Revenue Performance)
**Early Retention Drop**  
Cohort analysis shows that the largest retention drop occurs after the first month, highlighting the importance of early user activation and onboarding.

**Formation of a Loyal User Core**  
After the initial decline retention stabilizes, suggesting the presence of a loyal user base that continues using the product over time.

**Steady Growth in Recurring Revenue**  
MRR increased by 7.9% month-over-month, showing consistent subscription revenue growth throughout 2025.

**High-Value Acquisition Channels**  
Users acquired through App Store search (ASO) and referral channels show the highest share of Premium subscriptions (over 63%), indicating stronger monetization potential from these sources.

**Churn Driven by Product Value Perception**  
Among Premium users the leading churn reason is "Not useful", suggesting that improving the perceived value or visibility of Premium features may help reduce churn.
