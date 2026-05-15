End-to-end mortgage analytics solution built in Power BI covering loan origination, borrower profiling, portfolio performance, delinquency trends, foreclosure analysis, and macroeconomic impact across 25,000 U.S. residential loans using a star schema data model and advanced DAX measures.# ![MortgageIQ Cover](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Cover%20Image%20US%20Mort.png)

# 🏠 U.S.A Mortgage Portfolio & Risk Analytics (2013–2024)
### **AI + Star Schema Dataset + Power BI | End-to-End Mortgage Portfolio Intelligence**

This repository contains my complete **U.S. Mortgage Portfolio & Risk Analytics** project, built using **Python (data generation)**, **Star Schema design**, and **Power BI**.  
It analyzes a synthetic but realistic mortgage portfolio covering **25,000 loans**, **30 loan types**, **10 years of data (2013–2024)**, across origination, servicing, delinquency, foreclosure, and macroeconomic impact.

---

## 📁 Project Overview

This project presents an interactive **8-page Power BI Dashboard** named **MortgageIQ**, analyzing the full residential mortgage lifecycle — from loan origination through to foreclosure and loss recovery.

The dashboard delivers deep insights into **origination trends**, **borrower credit profiles**, **portfolio delinquency**, **foreclosure pipelines**, and **macroeconomic impacts**, giving a realistic view of how a mortgage lender or servicer would monitor and manage a loan portfolio.

---

## 🖼️ Dashboard Preview

### 🏠 Title Page — Home & Navigation
![Title Page](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Title.png)

### 📊 Executive Summary
![Executive Summary](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Executive.png)

### 📈 Origination Analysis
![Origination Analysis](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Origination.png)

### 👤 Borrower & Property
![Borrower & Property](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Borrower.png)

### 📉 Portfolio Performance & Delinquency
![Portfolio Performance](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Delinquency.png)

### ⚠️ Foreclosure & Loss Analysis
![Foreclosure & Loss](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Foreclosure.png)

### 🌐 Macro & Rate Environment
![Macro & Rate](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Micro.png)

### 💡 Insights & Recommendations
![Insights](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Insights.png)

---

## 🔍 Key Features

- 🏦 **Origination Intelligence**: Volume trends, loan type mix, channel analysis, lender performance, LTV/DTI distribution
- 👤 **Borrower & Property Analytics**: Credit tier segmentation, geographic heatmap, property type analysis, first-time buyer profiling
- 📉 **Portfolio Performance**: Monthly delinquency tracking, vintage cohort curves, COVID forbearance impact, delinquency by loan category
- ⚠️ **Foreclosure Pipeline**: NOD → NTS → Auction → REO funnel, loss severity by state, recovery timeline analysis
- 🌐 **Macro Environment**: Fed funds rate vs origination volume, unemployment–delinquency correlation, HPI trend, refinance share cycle
- 💡 **Insights & Recommendations**: 8 key findings, 8 strategic recommendations, opportunity sizing, Top 3 actions
- 🎯 **Fully Interactive Slicers**: Year · Loan Category · State · Lender · Credit Tier · Delinquency Type · Foreclosure Status

---

## 📊 KPIs Included

- **Total Loan Volume** ($9.25B)
- **Total Loans Originated** (25,000)
- **Average Interest Rate** (5.17%)
- **Prepayment Rate / CPR** (17.43%)
- **Avg Lifetime LTV** (76.1%)
- **Avg Loan Amount** ($369.9K)
- **Avg Debt-to-Income Ratio** (33.97%)
- **Purchase vs Refinance Share** (59.42% / 43.67%)
- **Active Loans & Unpaid Principal Balance** ($228.2M)
- **Serious Delinquency Rate** (0.03%)
- **Avg Days Delinquent** (1.29)
- **Total Foreclosures** (875)
- **Avg Loss Severity %** (8.66%)
- **Total Estimated Loss** ($48.2M)
- **Avg Time to Foreclosure** (13.39 months)
- **Latest Fed Funds Rate** (4.97%)
- **National HPI Growth 2013–2024** (77.69%)

---

## 💻 Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** | Star schema dataset generation (25,000 loans, realistic patterns) |
| **Pandas / NumPy** | Data modeling, statistical distribution, time-series simulation |
| **OpenPyXL** | Multi-sheet Excel workbook creation with professional styling |
| **Power BI Desktop** | Data modeling, report design, interactive dashboards |
| **Power Query (M)** | ETL, data transformation, column profiling |
| **DAX** | KPI measures, time intelligence, YoY/MoM calculations |
| **Power BI Bookmarks** | Page navigation, drill-through, conditional formatting |

---

## 🗄️ Star Schema Data Model

```text
                    Dim_Date ──────────────────────────────────┐
                    Dim_Borrower                               │
                    Dim_Property                               │
                    Dim_Lender                    ┌────────────▼──────────────┐
                    Dim_Loan_Product  ────────────►  Fact_Loan_Origination    │
                    Dim_Servicer                  │  (Central Fact · 25K rows)│
                    Dim_Investor                  └─────┬──────────┬──────────┘
                    Dim_Economic_Indicator               │          │
                                                         │          │
                                          ┌──────────────▼──┐  ┌───▼────────────────┐
                                          │ Fact_Monthly_    │  │  Fact_Foreclosure  │
                                          │ Performance      │  │  (875 rows)        │
                                          │ (227K rows)      │  └────────────────────┘
                                          └──────────────────┘
                                          ┌──────────────────┐
                                          │  Fact_Rate_Lock  │
                                          │  (15,000 rows)   │
                                          └──────────────────┘
```

### 📐 Table Summary

| Table | Type | Rows | Columns | Description |
|-------|------|------|---------|-------------|
| `Fact_Loan_Origination` | FACT | 25,000 | 55 | Central fact — one row per loan, 30 loan types, 2013–2024 |
| `Fact_Monthly_Performance` | FACT | 227,112 | 24 | Monthly balance, delinquency, HELOC draw/paydown, forbearance |
| `Fact_Foreclosure` | FACT | 875 | 25 | Full NOD→NTS→Auction→REO pipeline with loss severity |
| `Fact_Rate_Lock` | FACT | 15,000 | 18 | Rate lock commitments, extensions, float-down events |
| `Dim_Date` | DIM | 4,383 | 21 | Daily calendar 2013–2024, HPI index, COVID/rate-spike flags |
| `Dim_Borrower` | DIM | 25,000 | 22 | Credit tier, income band, employment, age group, vesting |
| `Dim_Property` | DIM | 25,000 | 26 | State, county, FIPS, MSA, flood zone, appraised value |
| `Dim_Lender` | DIM | 28 | 17 | Lender type (BK/MG/CU/IT), regulator, NMLS, FHA/VA approval |
| `Dim_Loan_Product` | DIM | 78 | 22 | 30 products: ARM caps, HELOC draw period, non-QM flags |
| `Dim_Servicer` | DIM | 15 | 12 | Portfolio size, CSAT score, delinquency rate |
| `Dim_Investor` | DIM | 7 | 12 | GSE/Ginnie/Portfolio/PLS flags, accepts HELOC/jumbo/non-QM |
| `Dim_Economic_Indicator` | DIM | 48 | 14 | Quarterly: Fed rate, 30yr MTG rate, HPI, unemployment, GDP |

---

## 🏦 30 Loan Types Covered

| Category | Loan Types |
|----------|-----------|
| **Conventional** | Purchase, Rate/Term Refinance, Cash-Out Refinance, 15-Year Fixed, 20-Year Fixed, Balloon 5-Year, Portfolio Fixed |
| **Government** | FHA Purchase, FHA Streamline Refi, FHA 203k Rehab, VA Purchase, VA IRRRL Refinance, USDA Rural Housing, Down Payment Assistance |
| **Jumbo** | Jumbo Purchase, Jumbo Refinance |
| **ARM** | 5/1 ARM Conventional, 7/1 ARM Conventional, 10/1 ARM Jumbo |
| **Home Equity** | HELOC (Revolving Credit Line), Home Equity Loan (Fixed), Credit Line 2nd Lien |
| **Construction** | Construction Loan, Construction-to-Permanent |
| **Non-QM** | Non-QM Stated Income, Non-QM Bank Statement, Investor DSCR Loan, Bridge Loan |
| **Specialty** | Reverse Mortgage (HECM), Co-op Loan |

---

## 🛠️ Technical Implementation

### 🐍 1. Python Dataset Generation

The entire dataset was generated using a custom Python script simulating realistic U.S. mortgage market behavior:

- **Rate Environment Simulation**: Each loan's interest rate is anchored to the actual historical average for its origination year (e.g., 2.96% in 2021, 6.81% in 2023) with credit score and LTV adjustments
- **HPI Modeling**: Property values scaled by a year-specific Housing Price Index multiplier (base 2013 = 1.0 → 2024 = 1.75), reflecting 77.69% national appreciation
- **Delinquency Simulation**: COVID period (Mar 2020–Sep 2021) carries elevated delinquency probability; Non-QM loans carry 2× base probability
- **HELOC Behavior**: Monthly draw and paydown amounts simulated independently with utilization tracking
- **Foreclosure Pipeline**: ~3.5% of loans enter foreclosure with realistic NOD→NTS→Auction→REO timeline

```python
# Rate environment by origination year
RATE_ENVIRONMENT = {
    2013: 4.00,  2014: 4.20,  2015: 3.85,  2016: 3.65,
    2017: 3.99,  2018: 4.54,  2019: 3.94,  2020: 3.11,
    2021: 2.96,  2022: 5.34,  2023: 6.81,  2024: 6.72
}

# Interest rate calculation per loan
base_rate    = RATE_ENVIRONMENT[origination_year]
credit_adj   = max(0, (720 - credit_score) * 0.006)
ltv_adj      = max(0, (ltv_ratio - 80) * 0.01)
rate_premium = loan_product_rate_premium_bps / 100
final_rate   = base_rate + rate_premium + credit_adj + ltv_adj
```

### 📊 2. Power BI Data Model

- **Import Mode** for all 12 tables
- **Star schema** with single-direction filter flow (dim → fact)
- **Inactive relationships** on Dim_Date for sub-fact tables, activated via `USERELATIONSHIP()` in DAX
- **Custom date table** with fiscal year, COVID flag, rate-spike flag columns

### 📐 3. DAX Measures

```dax
-- Total Loan Volume
Total Loan Volume = SUM(Fact_Loan_Origination[loan_amount])

-- YoY Growth
YoY Volume Growth % =
DIVIDE(
    [Total Loan Volume] - CALCULATE([Total Loan Volume], SAMEPERIODLASTYEAR(Dim_Date[full_date])),
    CALCULATE([Total Loan Volume], SAMEPERIODLASTYEAR(Dim_Date[full_date]))
)

-- Serious Delinquency Rate (90+ days)
Serious Delinquency Rate =
DIVIDE(
    CALCULATE(COUNTROWS(Fact_Monthly_Performance), Fact_Monthly_Performance[delinquency_days] >= 90),
    COUNTROWS(Fact_Monthly_Performance)
)

-- Avg Loss Severity
Avg Loss Severity % = AVERAGE(Fact_Foreclosure[loss_severity_pct])

-- Delinquency Rate by Vintage (for cohort analysis)
Delinquency Rate by Month =
CALCULATE(
    DIVIDE(
        COUNTROWS(FILTER(Fact_Monthly_Performance, Fact_Monthly_Performance[is_delinquent] = 1)),
        COUNTROWS(Fact_Monthly_Performance)
    ),
    USERELATIONSHIP(Dim_Date[date_key], Fact_Monthly_Performance[report_date_key])
)
```

---

## 📋 Dashboard Pages

### 📌 Page 1 — Title Page / Home
![Title Page](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Title.png)

**Contains:**
- Project title, subtitle and welcome message
- 4 headline KPI cards: Total Volume, Portfolio Health Score, Avg Rate, Total Estimated Loss
- Left-panel page navigation buttons
- About This Dashboard description
- Mortgage lifecycle overview
- Key Focus Areas and Business Questions Answered

---

### 📌 Page 2 — Executive Summary
![Executive Summary](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Executive.png)

**Key Visuals:**
- 5 KPI cards: Total Loan Volume, Loans Originated, Avg Interest Rate, Prepayment Rate (CPR), Avg LTV
- Loan Origination Trend 2013–2024 (line chart with Fed Rate Hike annotation)
- Total Loan Volume by Loan Category (horizontal bar)
- Top 10 States by Avg Loan Volume (column chart)
- Loan Origination by Channel (donut chart)

---

### 📌 Page 3 — Origination Analysis
![Origination Analysis](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Origination.png)

**Key Visuals:**
- 4 KPI cards: Avg Loan Amount, Avg Interest Rate, Avg DTI Ratio, Purchase vs Refinance share
- Avg Interest Rate Trend by Loan Category 2013–2024 (multi-line)
- Top 10 Lenders by Loan Volume (bar chart)
- Avg LTV vs Avg Interest Rate by Loan Category (scatter plot)
- Top 10 Loan Types by Volume (treemap)

---

### 📌 Page 4 — Borrower & Property
![Borrower & Property](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Borrower.png)

**Key Visuals:**
- 4 KPI cards: Avg Credit Score, First-Time Buyer %, Avg Property Value, Investment Property %
- Number of Loans by Credit Tier (bar chart)
- US Geographic Distribution map (filled map by state)
- Credit Score vs Avg DTI Ratio by Occupancy (scatter plot)
- Number of Loans by Property Type (donut chart)

---

### 📌 Page 5 — Portfolio Performance & Delinquency
![Portfolio Performance](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Delinquency.png)

**Key Visuals:**
- 5 KPI cards: Active Loans, Avg Days Delinquent, Serious Delinquency Rate, Current Loan %, Total Unpaid Balance
- Delinquency Type Trend by No. of Loans and Year (stacked area)
- Delinquency Trend by Year — COVID Effect (line with forbearance period annotations)
- Monthly Delinquency Trend by Vintage — Last 5 Years (multi-line)
- Delinquency Rate by Loan Category (horizontal bar)

---

### 📌 Page 6 — Foreclosure & Loss Analysis
![Foreclosure & Loss](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Foreclosure.png)

**Key Visuals:**
- 4 KPI cards: Total Foreclosures, Avg Loss Severity %, Avg Time to Foreclosure, Total Estimated Loss
- Foreclosure Trend by Year (line with COVID start/end markers)
- Top 10 States by Avg Loss Severity % (bar chart)
- Foreclosure Pipeline Status (horizontal bar: REO Acquired → NOD Filed → NTS → Pre-foreclosure)
- Recovery Timeline by Loan Category and Amount (bubble chart)

---

### 📌 Page 7 — Macro & Rate Environment
![Macro & Rate](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Micro.png)

**Key Visuals:**
- 5 KPI cards: Latest Fed Funds Rate, Latest Mortgage Rate, HPI Growth 2013–2024, Refinance vs Purchase Share, Total Origination in Billions
- Unemployment vs Delinquency Rate scatter (bubble chart by year)
- Mortgage Rate vs Origination Volume by Year (dual-axis bar + line)
- Refinance Share Trend 2013–2024 (line with COVID period annotation)
- Housing Price Growth Index Trend (line with trend line)

---

### 📌 Page 8 — Insights & Recommendations
![Insights & Recommendations](https://github.com/saheb1999/U-S-Mortgage-Analysis-/blob/main/Insights.png)

**Contains:**
- Macro & Market Insights (4 key observations)
- Credit & Risk Findings (5 key findings)
- Portfolio Insights (4 portfolio-level conclusions)
- What the Data Tells Us (checkmark summary)
- Key Risks to Monitor (alert summary)
- Top 3 Actions — Next 90 Days (prioritized action plan)
- Portfolio Conclusion
- Strategic Recommendations

---

## 💡 Key Business Insights

- 💰 **$9.25B Total Loan Volume** across 25,000 loans, 2013–2024 · ▲ 9.4% vs prior year
- 🏠 **Government loans dominate** at $2.22B (FHA/VA/USDA) — driven by 38.28% first-time buyer rate
- 📈 **2021 was the peak origination year** — record-low 2.96% rate drove purchase and refi surge
- 📉 **2022–2023 rate shock** pushed 30yr rate to 6.72–6.81%, dropping refi share from 57% → 39%
- ⚠️ **Non-QM delinquency is 2× higher** (0.63%) than conventional (0.45%) — concentration risk at $1.67B
- 🦠 **COVID forbearance peak resolved cleanly** — 99.95% of active loans returned to current status
- 🗺️ **Rhode Island (18.1%) and Nebraska (17.06%)** show highest loss severity — judicial foreclosure states
- 🏡 **HPI grew 77.69% since 2013** — significantly strengthening collateral values across the portfolio
- 🔗 **Unemployment above 5.5%** historically triggers nonlinear delinquency spikes (per macro scatter)
- 💳 **HELOC opportunity**: $671M currently in book vs ~$85–120M untapped cross-sell potential in sub-60% LTV loans

---

## 📌 Learning Outcomes

✅ **End-to-end mortgage analytics pipeline** from Python data generation to Power BI insights  
✅ **Star schema design** — 4 fact tables + 8 conformed dimension tables  
✅ **Realistic financial data simulation** — rate environments, HPI, COVID effects, credit tiers  
✅ **Advanced Power BI modeling** — inactive relationships, USERELATIONSHIP(), cross-filter direction  
✅ **DAX time intelligence** — YoY, MoM, vintage cohort, SAMEPERIODLASTYEAR  
✅ **Mortgage domain knowledge** — LTV, DTI, CPR, loss severity, judicial foreclosure, DSCR, HELOC  
✅ **Business storytelling** — 8 dashboard pages each answering a distinct business question  
✅ **Macro-financial analytics** — Fed rate, HPI, unemployment correlation with portfolio metrics  

---

## 🔑 Key DAX Patterns Used

```dax
-- Activate inactive Dim_Date → Fact_Monthly_Performance relationship
Delinquency Rate (Monthly) =
CALCULATE(
    [Delinquency Rate],
    USERELATIONSHIP(Dim_Date[date_key], Fact_Monthly_Performance[report_date_key])
)

-- Vintage cohort: delinquency rate by origination year, month on book
Vintage Delinquency Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS(Fact_Monthly_Performance),
        Fact_Monthly_Performance[is_delinquent] = 1
    ),
    COUNTROWS(Fact_Monthly_Performance)
)

-- Portfolio health: % of loans currently active and current
Current Loan % =
DIVIDE(
    CALCULATE(
        COUNTROWS(Fact_Monthly_Performance),
        Fact_Monthly_Performance[delinquency_days] = 0,
        Fact_Monthly_Performance[is_prepaid] = 0
    ),
    COUNTROWS(Fact_Monthly_Performance)
)

-- Loss severity weighted by UPB
Weighted Loss Severity =
DIVIDE(
    SUMX(Fact_Foreclosure, Fact_Foreclosure[estimated_loss]),
    SUMX(Fact_Foreclosure, Fact_Foreclosure[unpaid_principal_balance])
)
```

---

## 🎯 Project Structure

```
US-Mortgage-Portfolio-Risk-Analytics/
│
├── python_dataset/
│   ├── generate_star_schema.py        ← Full star schema generator
│   ├── generate_facts.py              ← Fact table builders
│   └── reference_data.py             ← Loan types, lenders, states etc.
│
├── data/
│   ├── US_Mortgage_StarSchema_Large.xlsx   ← 12-sheet workbook (all tables)
│   ├── Fact_Loan_Origination.xlsx
│   ├── Fact_Monthly_Performance.xlsx
│   ├── Fact_Foreclosure.xlsx
│   └── Fact_Rate_Lock.xlsx
│
├── power_bi/
│   └── MortgageIQ_Dashboard.pbix     ← Power BI report file
│
├── screenshots/
│   ├── Title_Page.png
│   ├── Executive_Summary.png
│   ├── Origination_Analysis.png
│   ├── Borrower_Property.png
│   ├── Portfolio_Performance.png
│   ├── Foreclosure_Loss.png
│   ├── Macro_Rate.png
│   └── Insights_Recommendations.png
│
├── dax_measures/
│   └── all_measures.dax              ← All DAX measures documented
│
└── README.md
```

---

## 🔄 Data Pipeline Architecture

```text
Python Script (Data Generation)
    ├── Rate environment simulation (2013–2024)
    ├── HPI-adjusted property values
    ├── Credit score / LTV / DTI distributions
    ├── COVID delinquency simulation
    └── HELOC draw/paydown behavior
              ↓
  Excel Workbook (12 Sheets — Star Schema)
  ├── 4 Fact Tables (268K+ total rows)
  └── 8 Dimension Tables (conformed dims)
              ↓
    Power BI Desktop (Import Mode)
    ├── Power Query ETL & column typing
    ├── Star schema relationships
    ├── DAX measures & calculated columns
    └── 8-page interactive report
              ↓
U.S. Mortgage Portfolio & Risk Analytics Dashboard (2013–2024)
  (Origination → Borrower → Performance → Foreclosure → Macro → Insights)
```

---

## ⚠️ Disclaimer

This project is created for **learning and portfolio demonstration purposes**.
- All loan data is synthetically generated using AI — no real borrower information is used
- Rate environments and HPI values are based on publicly available historical U.S. mortgage market data
- Foreclosure and loss figures are simulated based on realistic market patterns
- This dashboard does not constitute financial or investment advice

---

## 🙌 Author

**Saheb Rafique**  
Data Analytics | Power BI | SQL | Python | BI Analytics

🔗 **LinkedIn:** [linkedin.com/in/saheb-rafique-87b2b9186](https://www.linkedin.com/in/saheb-rafique-87b2b9186)  
🔗 **GitHub:** [github.com/saheb1999](https://github.com/saheb1999)  
🔗 **Website:** [saheb-rafique.netlify.app](https://saheb-rafique.netlify.app)

📬 **Open to Data Analytics, BI Developer, Credit Risk Analytics & Mortgage Analytics roles** **#OpenToWork**

---

## ⭐ If you found this project useful, please give it a star!

---

*Have questions or want to collaborate? Feel free to reach out via LinkedIn!*
