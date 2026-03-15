# Student Risk Identification Model 

## Project Overview
This project aims to proactively identify students at risk of not completing their studies. By analyzing academic, attendance, and financial data, we developed a data-driven early intervention model to help academic and student-support teams create targeted action plans before students disengage or withdraw.

## Data Preparation & Quality Issues
The initial dataset contained several quality issues that required standardisation:
- **Inconsistency**: Standardised gender labels (e.g., 'Male' vs 'M') and unified date formats to `DD/MM/YYYY`.
- **Anomalies**: Removed duplicate records (e.g., Student 1006) and handled non-numeric values in the `CreditsCompleted` field.
- **Missing Values**: Treated null values in `AttendanceRate` and `LastAttendanceDate` as high-risk signals, since absence of data can indicate disengagement.

## Methodology: Weighted Scoring Model
To quantify risk, a weighted scoring model was designed based on three key pillars:

| Category             | Weight | Key Metrics                                   |
|----------------------|--------|-----------------------------------------------|
| **Engagement**       | 50%    | Attendance Rate, Last Attendance Date         |
| **Academic**         | 30%    | Credits Completed, Last Assessment Submission |
| **Financial & Status** | 20%  | Outstanding Fees, Scholarship, Enrolment Status |

**Rationale**: Engagement is treated as the strongest lead indicator because disengagement almost always precedes formal withdrawal.

## Key Findings
Lower score = higher risk.

- **Student 1003 – Critical Risk (1.25 / 10)**  
  - Status: Suspended  
  - Debt: £3,500  
  - No attendance since 2025  
  - **Action**: Immediate financial and academic intervention.

- **Student 1002 – High Risk (2.75 / 10)**  
  - Status: Active  
  - Attendance: 45%  
  - No recent logins / engagement  
  - **Action**: Proactive outreach to re-engage before withdrawal.

- **Student 1005 – Known Withdrawal (Validation Case)**  
  - Model correctly flagged as high risk prior to withdrawal.  
  - Used as a benchmark to validate the scoring logic.

Other students (1001, 1004, 1006) scored higher, indicating **lower relative risk** but still suitable for routine monitoring.

## Limitations
- **Small Sample Size** – Snapshot view, no long-term patterns or seasonality.
- **Static Snapshot** – Scores reflect a single point in time; student situations may already have changed.
- **Missing Behavioural Data** – No VLE (Virtual Learning Environment) login frequency or resource engagement depth.

## Future Improvements
- **Integrate VLE Behavioural Features** such as login frequency and content interaction.
- **Live Risk Dashboard** that automatically updates scores when lectures or assessments are missed.
- **Train Predictive Models on Larger Historical Cohorts** to calibrate thresholds and improve accuracy.

---

> This project was completed as part of the **Data Science Task – Jan 2026**.
