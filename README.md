# OTT Subscription Churn Analysis & Customer Intelligence

## 📌 Project Overview

In the hyper-competitive OTT landscape, customer retention dictates survival. This project builds a multi-dimensional data analytics pipeline to identify high-risk subscribers, uncover behaviors driving cancellation, and quantify the direct revenue impact of customer churn. 

By extracting multi-table relational data and implementing advanced feature engineering, this analysis translates raw metrics into data-backed retention strategies to maximize long-term platform yield.

---

## 🛠️ Tech Stack & Key Concepts
* **Database Management:** SQLite (`sqlite3`) 
* **Data Manipulation & Cleaning:** Python (`pandas`, `numpy`)
* **Data Visualization:** `matplotlib`, `seaborn` 
* **Analytics Framework:** Exploratory Data Analysis (EDA), Advanced Feature Engineering, Risk Segmentation

---

## 🗺️ Project Roadmap & Workflow
1. **Relational Data Extraction:** Connected an SQLite database to Python using `pandas` and `sqlite3` to pull multi-table datasets.
2. **Data Cleaning:** Managed data types, handled missing/null values, performed quality control (QCs), and renamed columns for standard consistency.
3. **Feature Engineering:** Built custom KPI calculations, evaluated customer tenure, and implemented data filters.
4. **Exploratory Data Analysis (EDA):** Leveraged data aggregations, `groupby` operations, and pivot tables to identify behavioral patterns.
5. **Data Visualization:** Built behavioral visual trends using `seaborn` and `matplotlib`.

---

## 📊 Core Relational Schema
The analytics architecture integrates across three key tables inside the `customer_churn` database:

* **`db_customer`**: Core subscriber demographics (ID, Name, Country, State, Gender, DOB, Interests, Pincode).
* **`db_subscription`**: Financial and contract history (Start/Renewal/Cancellation Dates, Plan Type, Contract Structure, Monthly Charges, CLTV, Churn Score).
* **`db_support`**: Support engagement history (Complaint Date, Escalation Flags, CSAT Scores, Comments).

---

## 📈 Key Metrics & Analytical Formulas Evaluated
The performance pipeline evaluates **20+ KPIs**, highlighted by the following core business logic:

| KPI | Analytical Formulation / Logic |
| :--- | :--- |
| **Churn Rate** | `churned_customers / total_customers`  |
| **Average Customer Tenure** | `AVG(DATEDIFF(cancellation_date OR NOW(), subscription_start_date))` |
| **ARPU (Avg Revenue Per User)** | `SUM(monthly_charges) / COUNT(active_customerid)`  |
| **Revenue at Risk** | `SUM(monthly_charges) WHERE churn_score > 70`  |
| **Escalation Rate** | `(SUM(escalations) / COUNT(complaints)) * 100`  |
| **Support-Churn Correlation** | `churn_rate WHERE escalations >= 1` vs `escalations == 0`  |

---

## 💡 Key Business Insights
* **The Churn Profile:** The platform experiences an overall **28.6% churn rate** (retaining 71.4%). 
* **Contract Vulnerability:** A stark contract disparity exists—monthly-contract subscribers churn at a massive **55.6%**, which is **6.7 times higher** than the **8.3% annual-contract rate**.
* **Revenue Impact:** Quantified an immediate **$73.94/mo in MRR leakage** and **$2,047 in CLTV erosion** directly concentrated within six specific high-risk customers. Total revenue lost due to churn stands at 18% ($74 lost out of $395 total).
* **Geographic & Plan Risk:** The vast majority of churn is concentrated in the **Basic subscription plan** and spiked intensely during **September 2024** in the state of **Karnataka**.
* **Support Signals:** Support escalations correlate heavily with involuntary churn, pointing to competitor switching, pricing sensitivities, and content gaps.

---

## 🚀 Strategic Recommendations & Action Items
* **Implement Contract-Migration:** Deploy targeted promotions and outreach to shift volatile monthly-contract cohorts into stable annual agreements.
* **Prioritize Value Over Volume:** Prioritize the retention of Premium annual plans over high-churn Basic monthly customer acquisition to shield maximum revenue yield.
* **Targeted Outreach Loop:** Build a priority retention matrix focusing heavily on "High" & "Medium" churn risk tiers; proactively resolve support complaints via direct emails and customer success loops.
* **Investigate Local Anomalies:** Conduct a targeted assessment into the September 2024 regional failure in Karnataka to identify if competitors ran localized campaigns or if platform pricing changes triggered the loss.

---
Project credit and inspiration: Rishabh Mishra (Senior Data Analyst)
