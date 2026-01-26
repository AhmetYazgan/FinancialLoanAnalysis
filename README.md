# Financial Loan Analysis (SQL + Tableau + Python)

## Overview
This project analyzes a financial loan portfolio to assess **portfolio health**, **risk segmentation**, and **funding/repayment performance**. It is structured as a BI-style deliverable with clearly defined KPIs, interactive Tableau dashboards, and supporting SQL + Python analysis.

**Primary goal:** enable stakeholders to monitor loan performance and drill into drivers across **loan status, geography, term, purpose, grade, employment length, and home ownership**.

---

## Deliverables
- **Tableau Workbook (`FinancialLoan.twb`)**  
  Includes 3 dashboards: **SUMMARY**, **OVERVIEW**, **DETAILS**
- **SQL Script (`FinancialLoan_Analysis.sql`)**  
  KPI definitions + portfolio breakdown queries (MSSQL / SQL Server)
- **Python Notebook (`FinancialLoanAnalysis.ipynb`)**  
  Data profiling, cleaning checks, and exploratory analysis

---

## Dataset
The analysis uses a loan-level dataset with **38,576 records** and **24 fields**, including:
- Loan attributes: `loan_amount`, `term`, `int_rate`, `installment`, `grade`, `sub_grade`
- Risk/affordability: `dti`, `annual_income`, `total_acc`
- Status/performance: `loan_status`, `total_payment`
- Customer attributes: `emp_length`, `emp_title`, `home_ownership`, `verification_status`
- Geography/time: `address_state`, `issue_date`, `last_payment_date`, `next_payment_date`, `last_credit_pull_date`

---

## KPI Framework (Portfolio Health)
The KPI layer is designed for executive monitoring and includes:

### Core KPIs
- **Total Loan Applications**
- **Total Funded Amount** (sum of `loan_amount`)
- **Total Amount Received** (sum of `total_payment`)
- **Average Interest Rate**
- **Average Debt-to-Income (DTI)**

### Time-Based KPIs (Trend Monitoring)
- **MTD / PMTD** (Month-to-Date / Previous-Month-to-Date)
- **MoM % change** (Month-over-Month rate)

### Good vs Bad Loan Segmentation
Loan status is grouped into:
- **Good Loans:** `Fully Paid`, `Current`
- **Bad Loans:** `Charged Off`

This segmentation is used to compute:
- Good/Bad loan **application share**
- Good/Bad loan **funded amount**
- Good/Bad loan **amount received**

---

## Tableau Dashboards
### 1) SUMMARY (Executive KPI View)
Focus: top-level portfolio health and Good vs Bad loan split  
Includes:
- Total KPIs + MTD/PMTD/MoM KPIs
- Good vs Bad loan indicators (e.g., donut-style visuals)
- High-level portfolio snapshot
  
# Summary Page 
![image](https://github.com/user-attachments/assets/6d67dfbe-4117-4fa1-b839-898a04f873f2)


### 2) OVERVIEW (Drivers & Breakdown)
Focus: understanding what drives funding and repayment patterns  
Includes:
- **Monthly trend** view (by `issue_date`)
- **State-level** portfolio distribution (geographic concentration)
- Breakdowns by:
  - `term` (36 vs 60 months)
  - `emp_length`
  - `purpose`
  - `home_ownership`
    
# Overview Page
![image](https://github.com/user-attachments/assets/277068fe-94dd-43f9-9112-592800074db4)


### 3) DETAILS (Drill-Down Table)
Focus: record-level exploration with filters  
Includes:
- Full dataset table view
- Interactive filtering for fast drill-down analysis (e.g., grade, state, status)
  
#Detail Page (contain data)
![image](https://github.com/user-attachments/assets/ed1e7cea-d950-4180-8d8f-41dde593314a)
---

## SQL (How KPIs Are Computed)
The SQL script provides reproducible queries for:
- Portfolio KPIs (applications, funded amount, amount received, avg interest rate, avg DTI)
- MTD / PMTD logic and MoM calculation
- Good vs Bad loan segmentation using `loan_status`
- Portfolio cuts by:
  - `loan_status`, `address_state`, `term`, `emp_length`, `purpose`, `home_ownership`

---

## Python (Data Profiling & Preparation)
The notebook supports BI reliability by:
- Profiling schema, missingness, and uniqueness
- Validating date parsing for time-based analysis
- Checking missing values (e.g., `emp_title`)
- Preparing fields used downstream in dashboards and SQL checks

---

## Repository Structure

---

## How to Run
### Tableau
1. Open `FinancialLoan.twb` in Tableau Desktop
2. Ensure the data source points to your dataset (CSV or SQL Server table)
3. Interact with filters to explore SUMMARY / OVERVIEW / DETAILS dashboards

### SQL (SQL Server / MSSQL)
1. Load data into a table (e.g., `financial_loan`)
2. Run `FinancialLoan_Analysis.sql` to reproduce KPIs and breakdowns

### Python
1. Open `FinancialLoanAnalysis.ipynb`
2. Ensure `financial_loan.csv` is in the same directory (or update the path)
3. Run cells top-to-bottom

---

## Notes / Assumptions
- “Good vs Bad loan” is defined by `loan_status` mapping (documented in SQL).
- KPI trends (MTD/PMTD/MoM) are intended for ongoing monitoring and can be adjusted to the reporting period required by stakeholders.

---

## Author
Ahmet Emin Yazgan — Data Analyst / BI portfolio project


