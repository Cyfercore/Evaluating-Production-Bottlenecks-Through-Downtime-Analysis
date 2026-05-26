# 📊 Evaluating Production Bottlenecks Through Downtime Analysis

> **A business intelligence project analysing production downtime at GreenTech Manufacturing to uncover operational bottlenecks, reduce a $1.5M annual loss, and drive data-informed scheduling decisions — powered by Microsoft SQL Server and Power BI.**

![SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

---

## 📌 Table of Contents

- [Project Summary](#project-summary)
- [Business Impact](#business-impact)
- [Company Overview](#company-overview)
- [Business Challenge](#business-challenge)
- [Project Objectives](#project-objectives)
- [Dataset Description](#dataset-description)
- [Project Workflow](#project-workflow)
- [Dashboards & Key Insights](#dashboards-KeyInsights)
- [Role & Responsibilities](#Role-Responsibilities)
- [Tech Stack](#tech-stack)

---

## 🧭 Project Summary

This project delivers a full end-to-end production analytics solution for **GreenTech Manufacturing**, a North Carolina-based eco-friendly consumer goods company generating $100 million in annual revenue. The company was losing an estimated **$1.5 million per year** to unplanned production downtime — caused by machine failures, material shortages, manual scheduling errors, and limited data visibility.

Using **Microsoft SQL Server** for data cleaning, transformation, and KPI development, and **Power BI** for interactive dashboard reporting, this project identifies the root causes of downtime across 13 contributing factors, evaluates operator scheduling efficiency, and provides actionable recommendations to reduce losses and improve throughput.

The analysis covers three dashboards: **GreenTech Visualization**, **Duration Analysis**, and **Operator Scheduling** — giving stakeholders a complete, real-time view of production performance from floor level to management.

---

## 💼 Business Impact

This project directly addresses a **$1.5 million annual production loss** by:

| Impact Area | Outcome |
|---|---|
| 🔍 Root Cause Identification | Pinpointed the top downtime factors driving the majority of production losses using Pareto analysis |
| 📅 Scheduling Optimisation | Identified scheduling gaps and operator conflicts causing idle time and production delays |
| 👷 Operator Accountability | Separated operator-error downtime from equipment and material failures for targeted intervention |
| 📊 Real-Time Visibility | Replaced manual reporting with live Power BI dashboards accessible to operations and management teams |
| 💰 Cost Reduction Pathway | Provided data-backed recommendations to reduce unnecessary labour costs, inventory wastage, and machine idle time |
| 🚚 Customer Satisfaction | Identified delivery bottlenecks that, when resolved, will improve on-time order fulfilment rates |

---

## 🏭 Company Overview

**GreenTech Manufacturing** was founded in 2010 by a group of engineers and entrepreneurs with a shared vision to provide high-quality, sustainable consumer goods. Specialising in eco-friendly household products, GreenTech is a mid-sized manufacturer producing biodegradable cleaning products, recyclable packaging solutions, and energy-efficient home appliances.

From its early years as a small startup, GreenTech Manufacturing steadily grew to become a leader in the eco-friendly consumer goods space, reaching an **annual revenue of $100 million by 2023**.

### Core Products

| Category | Products |
|---|---|
| 🧴 Eco-Cleaning Supplies | Biodegradable detergents, cleaning wipes, and soaps |
| ♻️ Recyclable Packaging | Packaging materials made from post-consumer recycled content |
| ⚡ Energy-Efficient Appliances | Air purifiers and fans designed to minimise energy consumption |

### Key Differentiators

- **Sustainability** — Environmentally-friendly practices that set GreenTech apart from larger competitors
- **Local Manufacturing** — All production takes place in North Carolina, ensuring tight quality and supply chain control
- **Customer Loyalty** — Strong brand loyalty built on sustainable living values and consistently high product quality

---

## ⚠️ Business Challenge

As GreenTech Manufacturing scales, it has encountered persistent challenges in its production schedules driven by **unplanned downtime**. Key contributing factors include:

- 🔧 **Machine Failures** — Unexpected equipment breakdowns that halt production lines
- 📦 **Material Shortages** — Raw material delays and inadequate inventory levels causing stoppages
- 📅 **Inefficient Production Planning** — Poorly optimised schedules leading to idle time and excessive changeovers
- 📝 **Manual Scheduling** — Heavy reliance on manual input causing errors, misalignments, and inefficiencies
- 👁️ **Limited Data Visibility** — Lack of real-time data preventing proactive identification of bottlenecks

---

## 🎯 Project Objectives

The primary goal of this project is to build a data-driven analytics solution that identifies the root causes of production downtime, optimises scheduling, and enables continuous performance monitoring. the core Objectives include

- 🔍 **Identify Root Causes of Downtime** — Analyse downtime records to determine key contributors across machine, material, and operator dimensions
- 📅 **Optimise Production Scheduling** — Use batch-level production data to identify scheduling inefficiencies and idle time patterns
- 👷 **Improve Operator Allocation** — Detect overlapping shifts, underutilised operators, and misaligned shift-to-product assignments
- 📊 **Enhance Reporting Transparency** — Deliver Power BI dashboards for real-time monitoring of production performance and downtime KPIs
- 🔄 **Enable Continuous Improvement** — Establish a data feedback loop that supports ongoing optimisation and strategic planning

---

## 🗄️ Dataset Description

Four relational datasets form the foundation of this analysis:

### A. Products *(Dimension Table)*

| Column | Description |
|---|---|
| `Product_ID` | Unique product identifier |
| `Product_Name` | Product name (e.g., Ecowash, BioWipe, Packaging Film) |
| `Description` | Full product description |
| `Category` | Product category (e.g., Eco-Cleaning Supplies) |
| `Size` | Product volume or weight |
| `Min_Batch_Time` | Expected minimum production time per batch |

### B. Line Productivity *(Fact Table)*

| Column | Description |
|---|---|
| `Date` | Production date |
| `Product_ID` | Foreign key referencing the Products table |
| `Batch_ID` | Unique 6-digit batch number prefixed by Product ID |
| `Operator` | Responsible production line operator |
| `Start_Time` | Batch production start date and time |
| `End_Time` | Batch production end date and time |
| `Planned_Min_Batch_Hours` | Expected production duration per batch in hours |

### C. Line Downtime *(Fact Table)*

| Column | Description |
|---|---|
| `Batch_ID` | Associated batch reference |
| `Factor_1` to `Factor_13` | Downtime minutes recorded per contributing factor |

### D. Downtime Factors *(Dimension Table)*

| Column | Description |
|---|---|
| `Factor_ID` | Unique identifier for each downtime factor |
| `Factor_Name` | Name of the downtime factor |
| `Description` | Detailed description of the factor |
| `Operator_Error` | Boolean flag — TRUE if downtime is caused by operator error |

---

## 🔄 Project Workflow

The project follows a structured six-stage analytics pipeline:

```
┌─────────────────────────────────────────────────────────────────┐
│                        PROJECT PIPELINE                         │
├──────────────────────┬──────────────────────────────────────────┤
│  Stage 1             │  Data Integration                        │
│                      │  Restore database backup into SQL Server  │
├──────────────────────┼──────────────────────────────────────────┤
│  Stage 2             │  Data Cleaning                           │
│                      │  Validate nulls, timestamps, batch IDs   │
├──────────────────────┼──────────────────────────────────────────┤
│  Stage 3             │  Data Transformation                     │
│                      │  Normalise and reshape for analysis       │
├──────────────────────┼──────────────────────────────────────────┤
│  Stage 4             │  KPI Development                         │
│                      │  SQL queries for downtime and efficiency  │
├──────────────────────┼──────────────────────────────────────────┤
│  Stage 5             │  Power BI Dashboards                     │
│                      │  Build 3 interactive dashboard pages      │
├──────────────────────┼──────────────────────────────────────────┤
│  Stage 6             │  Insights & Recommendations              │
│                      │  Data-backed actions to reduce downtime   │
└──────────────────────┴──────────────────────────────────────────┘
```

---

## 📊 Dashboards

This project delivers three interactive Power BI dashboards:

### 1. 🟢 GreenTech Visualization
The executive-level overview dashboard providing a high-level summary of production performance across all product lines. Designed for management to quickly assess overall operational health, track total downtime, and monitor production output trends over time.

<img width="2285" height="1167" alt="Greentech visualisation" src="https://github.com/user-attachments/assets/1b03d57e-3ee8-4c1b-9324-cefbef74ad69" />

## 📊 Downtime Factor Analysis — Key Insights

- Identified **885 downtime factors**, resulting in **22 full days of lost production**, highlighting a major opportunity for operational recovery.
- Found that **363 out of 645 batches were delayed**, showing downtime is directly impacting more than half of all production runs.
- Highlighted **GreenFoam Hand Soap** as the most affected product with **323 downtime events**, indicating a high‑risk SKU requiring process optimisation.
- Revealed that **operator‑related issues account for 68.93%** of all downtime, demonstrating the need for targeted training and stronger SOP compliance.
- Pinpointed **Paul** as the operator with the highest downtime count (**164 events**), showing where coaching or workflow redesign could deliver immediate impact.
- Identified **Linda’s 70.73% delayed batch rate**, linking operator scheduling to batch performance and highlighting a key optimisation area.
- Exposed **Cleaning & Sanitisation (86 events)** as the top downtime cause, suggesting inefficiencies in changeover and hygiene procedures.
- Found recurring issues such as **Raw Material Shortage (77)** and **Scheduling/Coordination delays (76)**, indicating cross‑departmental bottlenecks.
- Detected **Machine Breakdown (75)** as a major contributor, supporting the case for improved preventive maintenance strategies.
- Observed consistently high downtime across months, with **April (157)** and **August (156)** showing peak disruption, suggesting cyclical or seasonal operational stress.

These insights demonstrate how data‑driven analysis can uncover operational bottlenecks, reduce delays, and improve overall production efficiency.


### 2. ⏱️ Duration Analysis
A deep-dive dashboard analysing batch duration against planned production times. This page identifies where production is running over schedule, highlights the most time-consuming downtime factors using Pareto analysis, and breaks down downtime distribution by product and factor category.

<img width="2286" height="1163" alt="duration analysis" src="https://github.com/user-attachments/assets/77390fa0-9821-4fba-83b3-c6884985adab" />

### 3. 👷 Operator Scheduling
A workforce-focused dashboard evaluating operator performance, shift allocation, and scheduling efficiency. This page surfaces overlapping shifts, highlights operators with the highest downtime rates, and distinguishes between operator-error and non-operator-error downtime to support targeted training and scheduling improvements.

<img width="2287" height="1163" alt="operator schedulling" src="https://github.com/user-attachments/assets/ab7e4ea8-79a1-49d3-ae1e-d4cdfd311050" />

> 📁 Dashboard file: `powerbi/greentech_dashboard.pbix`

---
### Business Impact of Downtime

| Impact Area | Description |
|---|---|
| Operational Inefficiency | Wasted labour hours and unused machine capacity across production lines |
| Financial Loss | **$1.5 million estimated annual revenue loss** from production delays |
| Customer Delays | Missed production deadlines leading to late order fulfilment and damaged customer relationships |
| Resource Wastage | Overstocking of some materials while others run short, increasing inventory management costs |


---
## 👨‍💻 Role & Responsibilities

As the Data Analyst on this project, I was responsible for delivering the full end‑to‑end analytics workflow — from restoring and exploring the SQL Server database to building the final Power BI dashboards. My work included data assessment, cleaning, transformation, and writing optimized T‑SQL queries to support four core analytical objectives:

- Cumulative downtime ranking across all products  
- Operator fault attribution and performance analysis  
- Schedule overrun and batch delay investigation  
- Downtime factor diversity and root‑cause analysis per product  

This end‑to‑end ownership ensured that the insights produced were accurate, actionable, and aligned with real operational challenges within the manufacturing environment.


---

## 🛠️ Tech Stack

| Tool | Role in Project |
|---|---|
| **Microsoft SQL Server** | Database restoration, data cleaning, transformation, and KPI query development |
| **Power BI Desktop** | Interactive dashboard development, KPI visualisation, and real-time reporting |


---

## 📬 Contact

**Collins Adegoke**  
**Collins@cyfercore.com **

🔗 [LinkedIn](https://www.linkedin.com/in/collins-adegoke-21375b252)

---

*This project was developed as part of a data analytics portfolio to demonstrate end-to-end business intelligence capabilities — from raw data to actionable insights.*
