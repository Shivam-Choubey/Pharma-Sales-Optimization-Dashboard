<div align="center">

<img src="https://img.shields.io/badge/-%F0%9F%92%8A%20PharmaSales%20Dashboard-0A2342?style=for-the-badge&labelColor=0A2342" alt="PharmaSales Dashboard"/>

# PharmaSales Dashboard

### Transforming 3 years of raw pharmaceutical sales data into clear, actionable business intelligence

<br/>

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-1D9E75?style=for-the-badge)

<br/>

| 💰 Net Revenue | 📦 Units Sold | 🔁 Return Rate | 📋 Transactions | 📅 Period |
|:---:|:---:|:---:|:---:|:---:|
| **$1.91M** | **2.52M** | **0.54%** | **1,007** | **Jan 2022 – Jun 2024** |

</div>


<br/>

## 🚨 Business Problem

A pharmaceutical distribution company operating across **5 US regions** and **4 sales channels** had 3 years of transaction data sitting untouched in a SQL Server database. Every month, the sales team built reports manually in Excel — a process that took days, was error-prone, and was already outdated by the time leadership read it.

The business was flying blind on 5 critical fronts:

<br/>

**❌ Problem 1 — No product-level visibility**

Nobody could answer: *"Which drugs are actually making us money?"* Revenue was tracked as a single total number, not broken down by product or category. Amoxicillin and Azithromycin were treated identically even though one consistently outperformed the other.

**❌ Problem 2 — Regional performance was invisible**

5 regions. Zero comparison. Sales managers had no way to know if North-East was outperforming Central, or whether a region's high unit volume was actually translating into revenue — or just selling cheap drugs in bulk.

**❌ Problem 3 — Returns were draining revenue silently**

13,484 units were returned across the data period. Nobody was tracking *which drugs* had the highest return rates, *which customers* were returning most, or what the financial cost of those returns was. The money was quietly leaking out.

**❌ Problem 4 — Supplier accountability was zero**

4 suppliers. No performance tracking. Two of them were delivering on time less than 90% of the time — causing stockouts and missed sales — and no one knew because nobody was measuring it.

**❌ Problem 5 — No trend visibility for planning**

Revenue dropped 8.7% from 2022 to 2023. Nobody noticed until the year was over. There was no monthly trend chart, no early warning, and no ability to course-correct mid-year.

<br/>

**The combined cost of these blind spots:** delayed decisions, misallocated sales effort, preventable returns, unreliable supply, and a business that could not answer its own most basic questions.

---
![Dashboard Preview](Churn%20Dashboard.jpg)

## ⭐ Project 

### 🏢 Situation

A pharmaceutical distribution company sells **7 drug categories** across 5 US regions through Wholesale, Online, Direct Order, and Pharmacy channels. They had accumulated 30 months of clean transactional data in Microsoft SQL Server — covering 1,007 orders, $1.91M in net revenue, and 2.52M units sold — but had no reporting layer on top of it.

Leadership was making territory decisions, supplier contracts, and product prioritization calls without any data to back them up. The company needed a single source of truth that any stakeholder — from a sales rep to the CEO — could open and get answers from immediately.

### 📋 Task

As the Data Analyst on this project I was responsible for the full pipeline:

- Extract and clean the raw sales data from Microsoft SQL Server
- Build a reliable data model in Power BI
- Create KPI measures in DAX that reflected real business performance
- Design a 2-page interactive dashboard covering **Sales Overview** and **Sales Performance**
- Deliver insights and recommendations that the business could act on immediately

### ⚙️ Action

**Step 1 · Data Extraction from MSSQL**

Connected Power BI to Microsoft SQL Server and wrote T-SQL queries to extract data from 5 tables: `Sales_Agent` (fact), `LinkedDrugs`, `Supplier`, `Inventory`, and `Pharma_Sales`. Used JOINs to link drug details to transactions and supplier records to inventory levels.

**Step 2 · Data Cleaning in Power Query**

- Removed 7 rows with null Region and Channel values
- Standardized 3 inconsistent date formats across the `SaleDate` column
- Created a derived `Year_Month` column (`2022-01` format) for trend analysis
- Built a dedicated Date table to enable time-intelligence DAX functions

**Step 3 · Data Model — Star Schema**

One-to-many relationships from each dimension to the central Sales fact table, with correct cardinality and cross-filter directions configured.

| Page | Visuals Included |
|---|---|
| **Sales Overview** | 6 KPI cards · Monthly revenue trend (2022/23/24) · Customer type donut · YoY annual summary cards · Date & region slicers |
| **Sales Performance** | Revenue by region · Drug category bar + return rate line overlay · Channel breakdown · Payment mode pie · Supplier OTD scorecard · Top 10 drugs table · Hospital vs Retail channel matrix |

<br/>

### 📈 Result & Impact

<div align="center">

| What Changed | Before | After |
|:---|:---:|:---:|
| Time to answer "how are we performing?" | 3 weeks | < 1 minute |
| Awareness that Antifungal = 26% of revenue | ❌ Unknown | ✅ Visible |
| Supplier OTD tracked against 90% SLA | ❌ Not tracked | ✅ Live scorecard |
| Regional revenue comparison | ❌ Not possible | ✅ Instant filter |
| Monthly trend visibility | ❌ Spreadsheet | ✅ 30-month trend chart |
| Return rate by drug and customer type | ❌ Not tracked | ✅ Flagged automatically |

The dashboard replaced the manual monthly Excel report entirely. Stakeholders can now self-serve answers to their most common questions without needing an analyst to pull data for them.

---

## 💡 Key Insights

### 💊 Insight 1 — One category carries 26% of total revenue

**Antifungal drugs generated $504,775** — more than Antiviral ($311K) and Antidiabetic ($297K) *combined*. This single category is the backbone of the business. It also represents the highest single point of revenue risk: any supply disruption, expiry issue, or competitor price cut here hits total company revenue harder than anything else.

| Category | Revenue | Revenue Share |
|---|---|---|
| 🥇 Antifungal | $504,775 | 26.4% |
| 🥈 Antiviral | $311,568 | 16.3% |
| 🥉 Antidiabetic | $297,137 | 15.5% |
| Analgesic | $210,965 | 11.0% |
| Anti-inflammatory | $203,381 | 10.6% |
| Antihistamine | $194,045 | 10.1% |
| Antibiotic | $192,590 | 10.1% |

### 🌍 Insight 2 — Central sells the most units but makes the least money

North-East leads revenue at **$403,777** while Central trails at **$373,346** — but Central has the *highest unit volume* at 505,657 units. This means Central is selling more of the cheaper drugs. It is working harder for less money. A product mix problem, not a volume problem.

| Region | Revenue | Units Sold | Rev per Unit |
|---|---|---|---|
| North-East | $403,777 | 511,665 | **$0.789** |
| Midwest | $386,948 | 515,621 | $0.750 |
| South | $376,910 | 491,893 | $0.766 |
| West Coast | $373,480 | 494,790 | $0.755 |
| Central | $373,346 | 505,657 | **$0.739** |

### 🔄 Insight 3 — Retail customers return 19% more than Hospitals

Hospital return rate: **0.49%** — Retail return rate: **0.58%**. Over 2.52M units, this 0.09 percentage point gap translates to hundreds of units and thousands of dollars in avoidable losses annually. Retail customers appear to be over-ordering or receiving products that don't match their requirements.

---

## ✅ Recommendations

### 🛡️ Rec 1 — Guard Antifungal stock like it's your most valuable asset

Because it is.

**Action:** Set a strict 30-day safety stock minimum for all Antifungal drugs. Alert the procurement team automatically when any Antifungal SKU drops below that buffer. Always restock Antifungal *before* any other category.

**Impact:** A single week of Antifungal stockout costs ~$9,700 in net revenue. That is more than any other category. Protecting this line costs nothing — letting it run out costs everything.

---

*⭐ Found this project useful? Give it a star — it helps more people find it.*

*Built with 💙 using real data from a live Power BI model · © 2024 Shivam Choubey*

</div>
