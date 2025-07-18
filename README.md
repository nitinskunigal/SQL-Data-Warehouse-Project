# SQL Data Warehouse & Analytics Project

Welcome to the **SQL Data Warehouse & Analytics Project** repository!

This project demonstrates the full cycle of a data-driven solution — from building a scalable data warehouse using SQL Server to performing exploratory and advanced analytics and finally delivering powerful business insights through interactive Power BI dashboards.

The project is structured into **three interconnected phases**, reflecting a full-stack analytics workflow:

1. **Data Engineering** — Design and implementation of a scalable data warehouse using SQL Server and the Medallion Architecture
2. **Data Analytics** — SQL-based exploratory and advanced analytics to uncover customer, product, and sales insights
3. **Business Intelligence (BI)** — Visualization and storytelling using Power BI, including KPI dashboards, drillthrough reports, and dynamic filtering

This end-to-end approach mirrors real-world data projects — from raw data to insights that drive decisions. Although the dataset is historical (2011–2014), it provided a rich opportunity to simulate real-world warehouse design, business rule application, and dashboard delivery — the skills demonstrated here are timeless.

---

## Table of Contents

- [Problem Statement](#problem-statement)
- [Objective](#objective)
- [Project Overview](#project-overview)
- [Stakeholder Requirements and Source System Understanding](#stakeholder-requirements-and-source-system-understanding)
- [Phase 1: Building the scalable Data Warehouse in SQL Server](#phase-1-building-the-scalable-data-warehouse-in-sql-server)
- [Phase 2: EDA and Advanced Data Analytics in SQL Server](#phase-2-eda-and-advanced-data-analytics-in-sql-server)
- [Phase 3: Power BI Dashboards and Business Insights](#phase-3-power-bi-dashboards-and-business-insights)
- [Key Deliverables](#key-deliverables)
- [Future Enhancements](#future-enhancements)

---

## Problem Statement

This project is set in a **hypothetical mid-sized retail company** that sells consumer goods across multiple channels (e.g., online and in-store). The company uses a **CRM system** to track sales transactions along with core details of products and customers, and an **ERP system** to manage extended/ additional details of customers and products.

Due to siloed systems and lack of integrated reporting, the company struggles with generating unified insights on product performance, customer behavior, and sales trends.

To address this, a **scalable data warehouse** was built using the Medallion Architecture (Bronze, Silver, Gold) in SQL Server, enabling clean, integrated, and business-ready data for analytics.

---

## Objective

To address this challenge, a complete **scalable data warehousing and analytics pipeline** is designed and implemented using the Medallion Architecture (Bronze, Silver, Gold) in SQL Server, enabling clean, integrated, and business-ready data for analytics. The ultimate goal is to create a reusable, scalable data foundation that supports business intelligence, reporting, and data science use cases.

---

## Project Overview

| Aspect | Description |
|--------|-------------|
| **Tech Stack** | SQL Server, T-SQL, Stored Procedures, Views |
| **Architecture** | Medallion Architecture (Bronze, Silver, Gold Layers) |
| **Data Sources** | ERP and CRM data in CSV format |
| **Objective** | Build a business-ready data warehouse in SQL Server, extract meaningful insights using SQL, and visualize those insights in Power BI |

---

## Stakeholder Requirements and Source System Understanding

Although this is a portfolio project based on fictional data and simulated context, it closely mirrors how real-world analytics projects are initiated—by capturing stakeholder requirements and understanding the technical landscape of the source systems involved.

In real-world scenarios, designing a scalable data warehouse begins with two parallel tracks:

- **Stakeholder Collaboration**: Framing business questions and converting stakeholder needs into user stories (here simulated in JIRA) to define KPIs, reporting expectations, and pain points in existing workflows.

- **Source System Analysis**: Understanding the structure, limitations, and integration options of the systems holding the raw data (e.g., ERP, CRM).

To simulate this process, the project used a list of best-practice discovery questions that would typically be explored in stakeholder workshops and technical walkthroughs. These questions shape everything from ingestion and transformation logic to the architecture of reporting layers.

### Key questions used to drive requirement gathering:

- Who owns the data in each source system (ERP, CRM, etc.)?
- What business processes do these systems support (e.g., Sales, Customer Retention)?
- What data formats and storage mechanisms are in place (CSV, SQL Server, Oracle, cloud storage)?
- What are the integration capabilities? (API, file extracts, direct DB access, Kafka, etc.)
- What authentication/access controls are required? (Tokens, VPN, SSH, whitelisting)
- What are the peak load times or usage periods for these systems?
- What is the data refresh frequency — daily, hourly, or real-time?
- Should we implement full loads or delta (incremental) loads?
- How large are the typical data extracts? Are there any volume constraints?
- Are there known data quality, consistency, or completeness issues?
- Which fields are business-critical for KPIs and reporting?
- How will we validate data correctness post-ingestion?
- What level of historization (Type 1 vs. Type 2) is required?
- What are the reporting pain points that this data warehouse is expected to solve?

*Together, these stakeholder-driven stories and system-level insights informed the design of the Medallion Architecture (Bronze → Silver → Gold), ensuring technical feasibility and business relevance were aligned from the very beginning.*

### Sample User Stories & Acceptance Criteria

Here are a few example user stories created as part of the stakeholder requirement mapping process (simulated in JIRA):

| **User Story** | **Persona** | **Acceptance Criteria** |
|----------------|-------------|--------------------------|
| **As a COO**, I want to monitor YoY revenue and profit trends so that I can evaluate overall business performance and spot strategic inflection points. | Executive Leadership | The dashboard must:<br>• Display YoY Revenue, Profit, Orders, and AOV with % change<br>• Include monthly revenue trends and a dynamic Top N product matrix<br>• Allow filtering by product category and subcategory<br>• Include a slicer panel containing slicers for year, country, and product segment  |
| **As a Customer Success Analyst**, I want to identify top customers by revenue and analyze their spend behavior so that I can tailor retention campaigns. | Marketing / CS Team | The dashboard must:<br>• Show Top 100 customers with revenue, orders, and AOV<br>• Display KPIs: Revenue per Customer, Average Order per Customer, and Avg Monthly Spend<br>• Include a line chart switching between total customers and revenue per customer<br>• Include donut charts for segment-wise order and revenue distribution |
| **As a Product Manager**, I want to analyze individual product performance and simulate price changes so that I can make more informed pricing decisions. | Merchandising / Product Team | The dashboard must:<br>• Enable drillthrough to selected products<br>• Display metrics like Avg Order Revenue, Monthly Revenue, and Price Sensitivity<br>• Allow simulation of profit impact through What-If scenarios |

---

## Phase 1: Building the scalable Data Warehouse in SQL Server

### Objective
Design and implement a scalable data warehouse using **SQL Server** to consolidate and model sales, customer, and product data from multiple source systems, enabling reliable analytical reporting.

### ETL Strategy Used in This Project

The project implements a simplified yet realistic ETL (Extract → Transform → Load) pipeline using **batch-based full extraction and full load** (`truncate & insert`), with transformation steps handled in SQL Server through multiple layers (Bronze → Silver → Gold).

✅ A detailed breakdown of **ETL types, methods, and which ones were used in this project** is available here → [`docs/etl_methods.md`](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/etl_methods.md)

![ETL Mind Map](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/etl_mind_map.png)

### Architecture: Medallion Approach

| Layer | Purpose | Transformations | Load Type | Object Type |
|-------|---------|-----------------|-----------|-------------|
| **Bronze** | Raw data storage | None (as-is) | Full load (Truncate & Insert) | Tables |
| **Silver** | Clean & standardized data | Cleansing, Normalization, Enrichment | Full load | Tables |
| **Gold** | Business-ready layer | Integrations, Aggregations, Business Logic | No Load (Views only) | Views |

### Data Warehouse Architecture

![Data Warehouse Architecture Diagram](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_architecture.drawio.png)

*This diagram illustrates the full Medallion Architecture (Bronze → Silver → Gold) and how data flows across layers in SQL Server.*

### Data Modeling
The Gold layer includes star schema views, flat tables, and aggregated objects for efficient reporting and ad hoc querying.

### Source Systems
- **ERP System** — Product and sales transactions
- **CRM System** — Customer data and engagement records

### Why No SSIS?
SSIS (SQL Server Integration Services) is a powerful ETL tool commonly used in enterprise setups, but it wasn't needed in this project. Since the data sources were flat files (CSV), I opted for a lightweight SQL-based approach using stored procedures, views, and the Medallion Architecture (Bronze → Silver → Gold). This kept the ETL process transparent, flexible, and easier to track inside SQL Server without requiring additional tooling.

### Automating the ETL Process

To simulate a production-ready ETL pipeline, the stored procedures responsible for data ingestion (Bronze Layer) and data transformation (Silver Layer) were automated using .bat scripting and **Windows Task Scheduler**. Since SQL Server Express Edition doesn’t support SQL Server Agent, the scheduling was instead handled using .bat scripts and Windows Task Scheduler — a lightweight, low-overhead alternative commonly used for local development and proof-of-concept projects. This setup mimics how real-world ETL jobs are orchestrated, allowing the entire data refresh cycle — from loading raw CSV files to producing clean, analytics-ready tables — to run without manual intervention.

---

## Phase 2: SQL-Based EDA and Advanced Data Analytics in SQL Server

### Objective
Uncover key business insights using SQL by performing:
- **Exploratory Data Analysis (EDA)**
- **Advanced Business Analytics**
- **Segmentation, Performance Tracking, and Trend Detection**

### Analysis Topics Covered
- Customer segmentation and behavior
- Product performance analysis
- Sales and revenue trends
- Cumulative metrics and rolling calculations
- Time-based comparisons (MoM, QoQ)
- Part-to-whole analysis and contribution breakdowns

### Output
- Optimized SQL scripts for each theme
- Business questions addressed through metrics
- Reusable SQL templates for BI teams

---

## Repository Structure

```
📁 data-warehouse-and-analytics-project/
├── 📁 datasets/                            # Raw datasets used for the project (ERP and CRM data)

├── 📁 docs/                                # Project documentation and architecture details
│   ├── 📄 data_architecture.drawio           # High-level project architecture (Bronze, Silver, Gold)
│   ├── 📄 data_catalog_source_system.md      # Captures essential metadata of source systems
│   ├── 📄 data_catalog_source_system.xlx     # Data Catalog in Excel sheet format
│   ├── 📄 data_cleaning_transformation.md    # Outlines the key data cleaning and transformation techniques
│   ├── 📄 data_dictionary.md                 # Provides detailed metadata for each column in the business-ready tables
│   ├── 📄 data_flow.drawio                   # Visual representation of data flow across layers
│   ├── 📄 data_flow_tasks.drawio             # Flow of tasks in each layer — analyzing, coding, validating, documenting
│   ├── 📄 data_integration.drawio            # Visual representation that depicts how Source Tables are connected
│   ├── 📄 data_layer_specifications.drawio   # Summarizes the objectives, transformations, and targets of each layer
│   ├── 📄 data_model.drawio                  # Data model design (e.g., star schema)
│   ├── 📄 etl_methods.md                     # Brief explanation of ETL strategy and methods used in this project
│   ├── 📄 etl_mind_map.png                   # Mind map showing the holistic understanding of ETL
│   └── 📄 naming_conventions.md              # Consistent naming guidelines for tables, columns, and files
│   ├── 📄 project_presentation.pdf           # Presentation deck related to this project

├── 📁 scripts/                             # All SQL-based work divided into two main tracks
│
│   ├── 📁 data_warehouse/                  # Scripts for building the data warehouse
│   │   ├── 📁 bronze/                        # Scripts for extracting and loading (full load) raw data
│   │   ├── 📁 silver/                        # Scripts for cleaning and transforming data
│   │   └── 📁 gold/                          # Scipts for creating analytical models (views and data models)
│
│   └── 📁 eda_analytics/                   # Scripts for EDA and advanced data (business) analytics

├── 📁 tests/                               # QA scripts for verifying integrity and logic of gold and silver layers

├── 📄 README.md                            # Project overview and instructions
```

---

> **Note on Historical Data**:  
> While the dataset used in this project spans from 2011 to 2014, it was selected for its realistic structure and complexity. This allowed for a robust simulation of real-world business scenarios including data modeling, segmentation, and KPI analysis.  
> 
> The **recommendations provided** are not intended for tactical execution but to demonstrate how an analyst would draw insights and inform strategy in a production environment.

---

## Phase 3: Power BI Dashboards and Business Insights

This section demonstrates how business-ready data from the Gold layer of the SQL data warehouse was connected to Power BI to uncover high-impact insights. I designed three interactive dashboards — Executive Overview, Customer Analysis, and Product Drillthrough — to simulate real-world reporting use cases. These dashboards were built with self-service BI in mind: stakeholders can explore data using filters, slicers, and drillthrough actions without needing to write SQL or request custom reports. The goal was to enable insight delivery at scale while keeping the analytical model standardized and governed.

### Power BI Auto-Refresh Simulation

The automation pipeline was extended to the reporting layer by connecting the published Power BI dashboards to the **On-Premises Gateway** and enabling scheduled refresh. This ensured that any updates made at the source level were automatically reflected in the visuals — allowing stakeholders to always work with the most current data without triggering manual refreshes. 

Together with the backend automation, this project simulates an end-to-end production workflow — from source ingestion to real-time dashboard refresh — using industry-aligned best practices.

---

<details>
<summary> <strong>Executive Dashboard</strong></summary>

### Focus:
- Company-wide KPIs (Revenue, Profit, Orders, AOV)
- Trend analysis and YoY comparisons
- Category-level breakdowns
- Dynamic Top N product matrix (filterable by metric)

![Executive Dashboard Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Executive%20Dashboard.png)

### Key Insights:
- **Revenue** grew to $16.3M (↑179.77%) and **Orders** surged 550% YoY — demand clearly exploded in 2013.
- However, **Avg Order Value** dropped 57% — indicating growth was volume-driven, not value-driven.
- Accessories led order volume, but high performers in Bikes contributed most to profit.
- Dynamic product matrix lets stakeholders view Top N products by Revenue, Orders, or AOV.

### Recommendations:
- Explore bundling or pricing strategies to improve AOV.
- Monitor inventory and fulfillment capacity to manage volume efficiently.

</details>

---

<details>
<summary> <strong>Customer Dashboard</strong></summary>

### Focus:
- Customer-level KPIs: Revenue per Customer, Monthly Spend, Order Frequency
- Top 100 customers by revenue and engagement
- Segment-wise donut charts: Revenue and Orders by Segment
- Time-series trends for Recency and Lifetime Value

![Customer Dashboard Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Customer%20Dashboard.png)

### Key Insights:
- The company served **17.4K customers** in 2013 but most made **only 1.2 orders** on average.
- Revenue per Customer: **$938**, with Monthly Spend averaging **$171**.
- New Customers made up **76% of all orders**, but contributed less to revenue — pointing to a retention challenge.
- VIPs and Regulars are small in number but hold higher per-customer value.

### Recommendations:
- Launch loyalty or reactivation campaigns to increase order frequency.
- Segment-targeted promotions could convert New → Regular → VIP.

</details>

---

<details>
<summary> <strong>Product Drillthrough Dashboard</strong></summary>

### Focus:
- Deep-dive into performance of a selected product (via drillthrough)
- Key KPIs: Average Order Revenue and Average Monthly Revenue
- Price sensitivity simulation: Compare Adjusted vs Base Profit for different price points
- Dynamic product metric selection to analyze weekly and monthly trends in orders, revenue, or profit

![Product Drillthrough Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Product%20Drillthrough%20Dashboard.png)

### Key Insights:
- Profit optimization scenarios allow decision-makers to simulate the financial impact of price changes.
- Weekly/ monthly metric trends help uncover seasonal dips or campaign performance, guiding better planning.

### Recommendations:
- Fine-tune product pricing using profit simulations to maximize margin without hurting volume.
- Schedule promotions around historically low-performing periods to boost sales.

</details>

---

### Dashboard Features & Highlights:
- **Slicer Panel with Bookmarks** to toggle filters by Year, Country, and Product Segment
- **Dynamic Top N Selector** (Revenue, Orders, AOV)
- **Product Drillthrough Navigation**
- **Conditional Formatting** and Trendlines to enhance storytelling
- **Parameter Controls** for simulation and deeper analysis

[Access Live Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDdlNTViNmItZDZkNC00N2FkLWE2N2EtYzdjOWZkOGIwNTRiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9)

---

## Key Deliverables

- A fully functional, SQL Server-based **scalable data warehouse** following industry-standard **layered Medallion Architecture**

- Clean and reusable **[SQL scripts](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/scripts)** for analytics

- **[QA Scripts](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/tests)** for Silver and Gold Layers

- **[Documentation](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/docs)** for data architecture diagrams, ETL flow, data model, data catalog, data layer specifications, etc.

- **[Power BI Dashboards](https://app.powerbi.com/view?r=eyJrIjoiNDdlNTViNmItZDZkNC00N2FkLWE2N2EtYzdjOWZkOGIwNTRiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9)**, shared online through Power BI Service

- **[Video Walkthrough](https://www.youtube.com/watch?v=Kspob_lGIaA&t=429s)** of this Project

- **[Presentation Deck](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_warehouse_and_analytics_project_presentation.pdf)**

---

## Future Enhancements

- Automating incremental loads via Change Data Capture (CDC)

- Introducing historical change tracking via SCD Type 2 for slowly changing dimensions (e.g., customer segment or product category shifts)
