# Mobile App Performance - Analytics Dashboard
<img width="493" height="480" alt="Screenshot 2026-03-09 at 18 21 43" src="https://github.com/user-attachments/assets/6c72d16a-8640-4808-815c-1b91eee19ce7" />

<img width="491" height="480" alt="Screenshot 2026-03-09 at 18 22 15" src="https://github.com/user-attachments/assets/ce3d52e6-6104-436c-9991-f91e9029866c" />

This project analyzes user behavior, retention, churn and revenue performance of a mobile application during 2025.

The analysis combines product analytics metrics, cohort retention analysis and revenue insights to understand how user engagement impacts business performance.

The dashboard was built using Tableau.

⚠️ The dataset used in this project is synthetic and generated for demonstration purposes.

## Project Goal

The goal of this project is to evaluate product health and monetization performance of a mobile application by analyzing:
• user growth  
• user engagement  
• retention dynamics  
• churn patterns  
• revenue generation  

The analysis focuses on identifying key behavioral patterns that influence long-term product performance.

## Data Model 
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

## Dashboard Overview

The dashboard consists of two analytical sections.

###  User Analytics  
This section focuses on user growth, engagement and retention.  
<img width="1391" height="880" alt="Screenshot 2026-03-09 at 18 21 43" src="https://github.com/user-attachments/assets/594c3b1c-385d-454b-ae9f-42510d4ec8ec" />
This section focuses on user growth, engagement and retention.  
<ins>**Key KPIs:** </ins> 
- **Active Users** — Unique users who had at least one session during the selected period.
- **New Users** — Users who registered during the selected period.
- **Paying Users** — Users who had at least one successful payment during the selected period.
- **Churned Users / Churn Rate** — Users whose paid subscription ended during the selected period. 

<ins>**Previous Period Comparison**</ins>  
For each KPI metric the value of the previous period is calculated:  
**Previous Last 7 days**  
**PM** — Previous Month  
**PQ**  — Previous Quarter  
**PY**   — Previous Year  
The change in pp means percentage points.  
_For Churned Users the delta is interpreted inversely: a negative delta indicates an improvement (fewer users churned)._

<ins>**Additional analysis:** </ins> 
- Demographic distribution of users (gender, age, country) by users type
- Monthly Churn Rate trend for 2025
- Cohort Retention Heatmap

        
