# 📊 Evaluating Production Bottlenecks Through Downtime Analysis

> A data-driven framework for identifying, tracking, and reducing production downtime through systematic bottleneck and root cause analysis — built for GreenTech Manufacturing.

![SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)

---

## 📌 Table of Contents

- [Company Overview](#company-overview)
- [Business Challenge](#business-challenge)
- [Project Rationale](#project-rationale)
- [Objectives](#objectives)
- [Dataset Description](#dataset-description)
- [Tech Stack](#tech-stack)
- [Project Scope](#project-scope)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)

---

## 🏭 Company Overview

**GreenTech Manufacturing** was founded in 2010 by a group of engineers and entrepreneurs with a shared vision to provide high-quality, sustainable consumer goods. Specializing in eco-friendly household products, GreenTech is a mid-sized manufacturer that has made a name for itself by producing biodegradable cleaning products, recyclable packaging solutions, and energy-efficient home appliances.

From its early years as a small startup, GreenTech Manufacturing has steadily grown to become a leader in the eco-friendly consumer goods space, reaching an **annual revenue of $100 million by 2023**. With a commitment to reducing environmental impact and enhancing product sustainability, the company prides itself on creating products that resonate with environmentally-conscious consumers.

### Core Products

| Product Category | Description |
|---|---|
| 🧴 Eco-Cleaning Supplies | Biodegradable detergents, cleaning wipes, and soaps |
| ♻️ Recyclable Packaging | Packaging materials made from post-consumer recycled content |
| ⚡ Energy-Efficient Appliances | Small home appliances like air purifiers and fans designed to minimize energy consumption |

### Key Differentiators

- **Sustainability** — Known for environmentally-friendly practices that set it apart from larger competitors
- **Local Manufacturing** — All manufacturing takes place in North Carolina, ensuring tight quality and supply chain control
- **Customer Loyalty** — Strong brand loyalty built on sustainable living values and high-quality product delivery

Despite its success, GreenTech has faced persistent challenges in optimizing production processes — particularly in maintaining efficient production schedules that minimize downtime and maximize throughput.

---

## ⚠️ Business Challenge

As GreenTech Manufacturing grows, it has encountered persistent challenges in its production schedules, which are often impacted by **unplanned downtime**. This downtime stems from a combination of factors:

- 🔧 **Machine Failures** — Equipment malfunctions or unexpected breakdowns that halt production
- 📦 **Material Shortages** — Delays in raw materials or inadequate inventory levels leading to stoppages
- 📅 **Inefficient Production Planning** — Poorly optimized schedules that lead to idle time or excessive machine changeovers
- 📝 **Manual Scheduling** — Heavy reliance on manual input, leading to errors, misalignments, and inefficiencies
- 👁️ **Limited Data Visibility** — Prevents proactive identification of bottlenecks before they escalate

### Key Impact Areas

| # | Impact Area | Description |
|---|---|---|
| 1 | Operational Inefficiency | Production lines experience downtime leading to wasted labor and unused machine time |
| 2 | Financial Costs | Estimated **$1.5 million annual loss** due to production delays and inefficiencies |
| 3 | Customer Delays | Failure to meet deadlines leads to delays in fulfilling orders, impacting customer satisfaction |
| 4 | Resource Wastage | Inefficient scheduling leads to overstocking of some materials while others run short |

---

## 💡 Project Rationale

Optimizing production schedules to minimize downtime is a critical initiative for GreenTech Manufacturing, especially as the company continues to grow and scale its operations. Efficient production scheduling is not just a matter of improving internal processes — it is an opportunity to enhance customer satisfaction, reduce costs, and improve overall operational efficiency.

### Top 5 Reasons for Initiating This Project

1. **Improved Decision-Making** — Data-driven insights will empower management to make better decisions and avoid costly mistakes
2. **Increased Production Efficiency** — Optimizing schedules will reduce idle time on production lines, leading to higher throughput and improved capacity utilization
3. **Cost Reduction** — Minimizing downtime reduces labor costs, avoids overstocking, and decreases wastage
4. **Enhanced Customer Satisfaction** — On-time deliveries will strengthen customer relationships and foster long-term loyalty
5. **Scalability** — Optimizing the production process enables GreenTech to scale its operations more efficiently as demand grows

---

## 🎯 Objectives

The main objective of this project is to optimize GreenTech Manufacturing's production schedules to **minimize downtime**, **reduce operational costs**, and **increase overall efficiency** through a data-driven approach.

### Specific Objectives

- 🔍 **Identify Root Causes of Downtime** — Analyze downtime records to determine key contributors (machine, material, operator error, etc.)
- 📅 **Optimize Production Scheduling** — Use production and downtime data to create efficient schedules that minimize overlaps and idle time
- 👷 **Improve Operator Allocation** — Ensure no operator runs overlapping shifts and optimize shift-to-product assignments
- 📊 **Enhance Reporting Transparency** — Develop Power BI dashboards for real-time monitoring of production performance and downtime metrics
- 🔄 **Enable Continuous Improvement** — Establish a data feedback loop that supports continuous optimization and strategic planning

---

## 🗄️ Dataset Description

Four datasets underpin the analysis:

### A. Products *(Dimension Table)*

| Column | Description |
|---|---|
| `Product_ID` | Unique product identifier |
| `Product_Name` | Product name (e.g., Ecowash, BioWipe, Packaging Film) |
| `Description` | Description of each product |
| `Category` | Category of each product (e.g., Eco-Cleaning Supplies) |
| `Size` | Product volume or weight |
| `Min_Batch_Time` | Expected production time per batch |

### B. Line Productivity *(Fact Table)*

| Column | Description |
|---|---|
| `Date` | Production date |
| `Product_ID` | Product reference |
| `Batch_ID` | Unique 6-digit batch number (prefixed by Product ID) |
| `Operator` | Responsible production line operator |
| `Start_Time` | Batch production start date and time |
| `End_Time` | Batch production end date and time |
| `Planned_Min_Batch_Hours` | Expected production time per batch in hours |

### C. Line Downtime *(Fact Table)*

| Column | Description |
|---|---|
| `Batch_ID` | Associated batch with downtime |
| `Factor_1` to `Factor_13` | Downtime minutes per contributing factor |

### D. Downtime Factors *(Dimension Table)*

| Column | Description |
|---|---|
| `Factor_ID` | Unique ID for downtime factors |
| `Factor_Name` | Name corresponding to each factor ID |
| `Description` | Description of factor IDs in text |
| `Operator_Error` | Boolean indicating whether downtime is caused by an operator |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| ![SQL Server](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=flat&logo=microsoft-sql-server&logoColor=white) | Centralized database storage, querying, and transformation |
| ![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=power-bi&logoColor=black) | Interactive dashboards and KPI visualization |

---

## 📐 Project Scope

The project follows a structured analytics pipeline across six key stages:

```
1. Data Integration        →   Restore database backup into SQL Server
        ↓
2. Data Cleaning           →   Validate completeness, timestamps, batch IDs
        ↓
3. Data Transformation     →   Normalize and reshape data for analysis
        ↓
4. KPI Development         →   SQL queries for downtime, operator, and batch metrics
        ↓
5. Power BI Dashboards     →   Visualize trends, distributions, and performance
        ↓
6. Optimization Insights   →   Recommendations to reduce downtime and improve throughput
```

### Dashboard Views (Power BI)

- 📉 Downtime distribution by factor and product
- 👷 Operator performance analysis
- 📆 Downtime trends over time
- ⚖️ Operator vs. non-operator error comparison

---

## 📁 Repository Structure

```
production-downtime-analysis/
│
├── README.md
│
├── data/
│   ├── raw/                        # Original database backup or CSV exports
│   └── cleaned/                    # Cleaned and validated datasets
│
├── sql/
│   ├── 01_data_cleaning.sql        # Null handling, type validation
│   ├── 02_data_transformation.sql  # Normalization and reshaping
│   └── 03_kpi_queries.sql          # KPI calculations and metrics
│
├── powerbi/
│   └── greentech_dashboard.pbix    # Power BI dashboard file
│
├── docs/
│   └── project_overview.md         # Full project documentation
│
└── assets/
    └── screenshots/                # Dashboard screenshots
```

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/production-downtime-analysis.git
   cd production-downtime-analysis
   ```

2. **Restore the database**
   - Open Microsoft SQL Server Management Studio (SSMS)
   - Restore the `.bak` backup file from the `data/raw/` folder

3. **Run SQL scripts in order**
   ```
   01_data_cleaning.sql → 02_data_transformation.sql → 03_kpi_queries.sql
   ```

4. **Open the Power BI dashboard**
   - Launch Power BI Desktop
   - Open `powerbi/greentech_dashboard.pbix`
   - Update the data source connection to your SQL Server instance

---

## 📬 Contact

For questions or contributions, feel free to open an issue or submit a pull request.

---

*This project was built as part of a data analytics initiative to support GreenTech Manufacturing's operational efficiency goals.*
