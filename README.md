# 📊 Evaluating Production Bottlenecks Through Downtime Analysis

> **A business intelligence project analysing production downtime at GreenTech Manufacturing to uncover operational bottlenecks, reduce a $1.5M annual loss, and drive data-informed scheduling decisions — powered by Microsoft SQL Server and Power BI.**

![SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

---

## 👤 Author

**Collins Adegoke** — Mid-Level Data Analyst  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/collins-adegoke-21375b252)

---

## 📌 Table of Contents

- [Project Summary](#project-summary)
- [Business Impact](#business-impact)
- [Company Overview](#company-overview)
- [Business Challenge](#business-challenge)
- [Project Objectives](#project-objectives)
- [Dataset Description](#dataset-description)
- [Tech Stack](#tech-stack)
- [Project Workflow](#project-workflow)
- [Dashboards](#dashboards)
- [Key Insights & Recommendations](#key-insights--recommendations)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)

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

### Business Impact of Downtime

| Impact Area | Description |
|---|---|
| Operational Inefficiency | Wasted labour hours and unused machine capacity across production lines |
| Financial Loss | **$1.5 million estimated annual revenue loss** from production delays |
| Customer Delays | Missed production deadlines leading to late order fulfilment and damaged customer relationships |
| Resource Wastage | Overstocking of some materials while others run short, increasing inventory management costs |

---

## 🎯 Project Objectives

The primary goal of this project is to build a data-driven analytics solution that identifies the root causes of production downtime, optimises scheduling, and enables continuous performance monitoring.

### Specific Objectives

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

## 🛠️ Tech Stack

| Tool | Role in Project |
|---|---|
| **Microsoft SQL Server** | Database restoration, data cleaning, transformation, and KPI query development |
| **Power BI Desktop** | Interactive dashboard development, KPI visualisation, and real-time reporting |

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

### 2. ⏱️ Duration Analysis
A deep-dive dashboard analysing batch duration against planned production times. This page identifies where production is running over schedule, highlights the most time-consuming downtime factors using Pareto analysis, and breaks down downtime distribution by product and factor category.

### 3. 👷 Operator Scheduling
A workforce-focused dashboard evaluating operator performance, shift allocation, and scheduling efficiency. This page surfaces overlapping shifts, highlights operators with the highest downtime rates, and distinguishes between operator-error and non-operator-error downtime to support targeted training and scheduling improvements.

> 📁 Dashboard file: `powerbi/greentech_dashboard.pbix`

---

## 💡 Key Insights & Recommendations

> *(To be updated with findings upon project completion)*

Key areas the analysis targets:

- **Top downtime factors** responsible for the majority of production losses
- **Operators** with the highest error-related downtime rates
- **Products** with the widest gap between planned and actual batch duration
- **Shift scheduling conflicts** causing preventable idle time
- **Recommended scheduling adjustments** to improve capacity utilisation

---

## 📁 Repository Structure

```
production-downtime-analysis/
│
├── README.md                          # Project documentation
│
├── data/
│   ├── raw/                           # Original database backup or CSV exports
│   └── cleaned/                       # Cleaned and validated datasets
│
├── sql/
│   ├── 01_data_cleaning.sql           # Null handling and data validation
│   ├── 02_data_transformation.sql     # Normalisation and reshaping
│   └── 03_kpi_queries.sql             # KPI calculations and metrics
│
├── powerbi/
│   └── greentech_dashboard.pbix       # Power BI report (3 dashboard pages)
│
├── docs/
│   └── project_overview.md            # Extended project documentation
│
└── assets/
    └── screenshots/
        ├── greentech_visualization.png
        ├── duration_analysis.png
        └── operator_scheduling.png
```

---

## 🚀 Getting Started

### Prerequisites
- Microsoft SQL Server or SQL Server Express
- SQL Server Management Studio (SSMS)
- Power BI Desktop (free download from Microsoft)

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/collins-adegoke/production-downtime-analysis.git
cd production-downtime-analysis
```

**2. Restore the database**
- Open SSMS
- Right-click **Databases → Restore Database**
- Select the `.bak` backup file from the `data/raw/` folder
- Click OK to restore

**3. Run SQL scripts in order**
```
01_data_cleaning.sql  →  02_data_transformation.sql  →  03_kpi_queries.sql
```

**4. Open the Power BI dashboard**
- Launch Power BI Desktop
- Open `powerbi/greentech_dashboard.pbix`
- Update the data source connection to point to your SQL Server instance
- Refresh the data

---

## 📬 Contact

**Collins Adegoke**  
Mid-Level Data Analyst  
🔗 [LinkedIn](https://www.linkedin.com/in/collins-adegoke-21375b252)

---

*This project was developed as part of a data analytics portfolio to demonstrate end-to-end business intelligence capabilities — from raw data to actionable insights.*
