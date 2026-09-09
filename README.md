# 🏥 Healthcare RCM: Prior-Authorization & Denial Analytics

<img width="1126" height="628" alt="18-43-16" src="https://github.com/user-attachments/assets/f3b2df91-6501-48c8-8bc9-858384fce253" />



## 📌 Executive Summary
This project delivers an end-to-end Healthcare Revenue Cycle Management (RCM) and Insurance Prior Authorization analysis. By simulating **3,000 patient authorization requests**, the project evaluates the financial impact of claim rejections on hospital revenue and measures insurance providers' compliance with Service Level Agreements (SLAs).

The solution features a relational database built in **SQL Server** and an interactive, executive-ready dashboard in **Power BI**, designed to help hospital executives reduce financial leakage and optimize operational workflows.

---

## 🎯 Business Problem & Objectives
Healthcare providers face significant revenue losses due to claim denials and delayed prior authorizations from insurance payers. This project addresses two primary operational challenges:

1. **Financial Leakage (Hospital View):** Identifying high-rejection specialties, financial loss metrics, and root causes for denied medical requests.
2. **Operational SLA Bottlenecks (Payer View):** Evaluating insurance turnaround times (TAT), identifying SLA breaches for Urgent vs. Routine cases, and benchmarking payer performance.

---

## 🛠️ Tech Stack & Tools
* **Database & Data Modeling:** SQL Server — DDL Scripts, Primary/Foreign Key Constraints, Complex Queries.
* **Business Intelligence & Visualization:** Power BI Desktop — DAX, Data Modeling (Star Schema), Custom Formatting & Interactive UI/UX.
* **ETL & Data Transformation:** Power Query.
* **Documentation & Portfolio:** Markdown, Git/GitHub.

---

## 🏗️ Data Architecture & Star Schema
The project is built on a robust **Star Schema** data model in SQL Server, imported into Power BI:

* **Fact Table:** `Fact_Insurance_Requests` (3,000 transactional records).
* **Dimension Tables:**
  * `Dim_Patient` (Demographics, Policy Details)
  * `Dim_Insurance` (Payer Details, SLA Targets for Urgent & Routine)
  * `Dim_Department` (Hospital Medical Specialties)
  * `Dim_Rejection_Reason` (Categorized Claim Denial Reasons)

---

## 💡 Key Business Insights (Project Results)

### 📄 Page 1: Hospital Performance (Revenue & Rejection Analysis)
* **Financial Overview:** Total Requested: **$22M** | Total Approved: **$16M** | Total Rejected (Revenue Loss): **$6M** (19% Rejection Rate).
* **Specialty Breakdown:** Highest rejection rates occur in **Cardiology** and **Radiology**, driven by high-cost procedures exceeding patient annual limits.
* **Root Causes:** Top denial reasons include **Exceeded Category Annual Limit** and **Non-Covered Service / Medication**.

### 📄 Page 2: Payer SLA & Operational Efficiency
* **Urgent Requests:** High compliance at **81%**, with an average TAT of **4.5 hours** (beating the 5.0-hour SLA target).
* **Routine Requests:** Sub-optimal compliance at **58%**, with an average TAT of **40 hours** (exceeding the 34-hour SLA target).
* **Payer Benchmarking:** **Novarex Global Assurance** and **Veltrix Health Plan** led compliance (>80%), while **Aetheria Care Protect** lagged significantly (55%).

---

## ⚠️ Challenges & Technical Solutions

| Challenge / Obstacle | Technical & Analytical Solution |
| :--- | :--- |
| **Dynamic SLA Targets:** Comparing turnaround times dynamically based on request priority (`Urgent` vs. `Routine`) across different payers. | Implemented dynamic DAX measures utilizing `SELECTEDVALUE` and conditional logic to adjust SLA targets dynamically per request context. |
| **Data Clutter (UI/UX Optimization):** Avoiding dense Matrix tables that hinder executive decision-making. | Replaced heavy data tables with clean **Clustered Bar Charts with Tooltips**, **Treemaps**, and **Combo Charts** for a seamless user experience. |
| **KPI Color Overload:** Bright colors on top KPI cards created visual fatigue. | Applied neutral dark tones for callout values with subtle accent indicators (soft green/red), matching modern corporate UI standards. |

---

## 🚀 Key Recommendations & Action Plan

1. **Implement Automated Pre-Eligibility Checks:** Deploy real-time limit tracking for high-cost departments (Cardiology & Radiology) to flag patients approaching their annual limits prior to service delivery.
2. **Formulary & Service Integration:** Integrate insurance-approved formularies directly into the hospital EHR to alert physicians when prescribing non-covered medications.
3. **Payer Contract Renegotiations:** Issue formal SLA breach notices to underperforming payers (e.g., Aetheria Care) regarding Routine request delays, using top performers (Novarex & Veltrix) as operational benchmarks.

---

## 📂 Repository Structure
```text
├── Database/
│   ├── Schema_DDL.sql          # SQL table creation scripts & constraints
│   └── Insert_Data.sql          # Sample transactional data (3,000 records)
├── PowerBI/
│   └── Healthcare_RCM_Analytics.pbix  # Interactive Power BI Dashboard
├── Screenshots/
│   ├── Hospital_Performance_Page1.png
│   └── Payer_SLA_Operations_Page2.png
└── README.md                    # Project Documentation
