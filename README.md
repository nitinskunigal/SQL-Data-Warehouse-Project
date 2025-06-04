# SQL Data Warehouse & Analytics Project

Welcome to the **SQL Data Warehouse & Analytics Project** repository!

This project demonstrates the full cycle of a data-driven solution — from building a scalable data warehouse using SQL Server to performing exploratory and advanced analytics and finally delivering powerful business insights through interactive Power BI dashboards.

The project is structured into **three interconnected phases**, reflecting a full-stack analytics workflow:

1. **Data Engineering** — Design and implementation of a modern data warehouse using SQL Server and the Medallion Architecture
2. **Data Analytics** — SQL-based exploratory and advanced analytics to uncover customer, product, and sales insights
3. **Business Intelligence (BI)** — Visualization and storytelling using Power BI, including KPI dashboards, drillthrough reports, and dynamic filtering

This end-to-end approach mirrors real-world data projects — from raw data to insights that drive decisions. Although the dataset is historical (2011–2014), it provided a rich opportunity to simulate real-world warehouse design, business rule application, and dashboard delivery — the skills demonstrated here are timeless.

---

## 📚 Table of Contents

- [🏢 Business Overview](#-business-overview)
- [🎯 Problem Statement](#-problem-statement)
- [🎯 Objective](#-objective)
- [📋 Business Requirements Gathering (Best-Practice Driven)](#-business-requirements-gathering-best-practice-driven)
- [🚀 Project Overview](#-project-overview)
- [🧱 Phase 1: Building the Modern Data Warehouse in SQL Server](#-phase-1-building-the-modern-data-warehouse-in-sql-server)
- [📈 Phase 2: EDA and Advanced Data Analytics in SQL Server](#phase-2-eda-and-advanced-data-analytics-in-sql-server)
- [📊 Phase 3: Power BI Dashboards and Business Insights](#-phase-3-power-bi-dashboards-and-business-insights)
- [📌 Key Deliverables](#-key-deliverables)
- [📎 Future Enhancements](#-future-enhancements)

---

## 🏢 Business Overview

This project is set in a **hypothetical mid-sized retail company** that sells consumer goods across multiple channels (e.g., online and in-store). The company uses a **CRM system** to track sales transactions along with core details of products and customers, and an **ERP system** to manage extended/ additional details of customers and products.

Due to siloed systems and lack of integrated reporting, the company struggles with generating unified insights on product performance, customer behavior, and sales trends.

To address this, a **modern data warehouse** was built using the Medallion Architecture (Bronze, Silver, Gold) in SQL Server, enabling clean, integrated, and business-ready data for analytics.

---

## 🎯 Problem Statement

The company faced challenges such as:
- Fragmented data across ERP and CRM systems
- Manual reporting processes with inconsistent metrics
- Inability to track customer behavior or product sales holistically

This project solved these problems by:
- Consolidating data from both systems into a structured data warehouse
- Cleaning, transforming, and modeling the data for analytical use
- Enabling rich SQL-based exploratory analysis for business decision-making

---

## 🎯 Objective

Design and implement a complete **modern data warehousing and analytics pipeline** that:

- Ingests and transforms raw ERP/CRM data
- Follows best practices using Medallion Architecture
- Supports SQL-driven insights for product, sales, and customer analysis

The ultimate goal is to create a reusable, scalable data foundation that supports business intelligence, reporting, and data science use cases.

---

## 📋 Business Requirements Gathering (Best-Practice Driven)

Although this is a portfolio project based on hypothetical data and scenarios, it follows real-world best practices that are essential when building a modern data warehouse.

In actual industry projects, understanding the **source systems** and their business context is one of the most critical steps in the data warehousing lifecycle. Below is a curated list of key questions that data engineers and analysts should ask when capturing requirements from business and technical stakeholders.

These questions help define the data ingestion strategy, transformation logic, metadata, and the final analytical model.

### 🔍 Source System & Business Context Questions

- Who owns the data in each system (ERP, CRM, etc.)?
- What business processes do these systems support (e.g., Sales, Customer Relationship)?
- What are the data formats and storage mechanisms (CSV, SQL Server, Oracle, cloud storage)?
- What are the integration capabilities? (API, file extracts, direct DB access, streaming tools like Kafka?)
- What is the authentication or access control mechanism? (Tokens, VPN, SSH, whitelisting?)
- What are the peak load times or usage periods for these systems?
- What is the frequency of data refresh or updates (daily, hourly, real-time)?
- Do we require full loads or incremental (delta) loads?
- How large are the typical data extracts? Are there any volume constraints?
- Are there known issues with data quality or completeness?
- What fields are most critical for business reporting and KPIs?
- How do we validate the correctness of the data post-ingestion?
- What level of historization is required (if any)?
- What are the reporting pain points that a data warehouse is expected to solve?

📌 *These questions help ensure that the design of the Bronze, Silver, and Gold layers aligns with both business needs and technical feasibility.*

---

## 🚀 Project Overview

| Aspect | Description |
|--------|-------------|
| **Tech Stack** | SQL Server, T-SQL, Stored Procedures, Views |
| **Architecture** | Medallion Architecture (Bronze, Silver, Gold Layers) |
| **Data Sources** | ERP and CRM data in CSV format |
| **Objective** | Build a business-ready data warehouse in SQL Server, extract meaningful insights using SQL, and visualize those insights by building Power BI Dashboards |

---

## 🧱 Phase 1: Building the Modern Data Warehouse in SQL Server

### 📌 Objective
Design and implement a modern data warehouse using **SQL Server** to consolidate and model sales, customer, and product data from multiple source systems, enabling reliable analytical reporting.

### ⚙️ ETL Strategy Used in This Project

The project implements a simplified yet realistic ETL (Extract → Transform → Load) pipeline using **batch-based full extraction and full load** (`truncate & insert`), with transformation steps handled in SQL Server through multiple layers (Bronze → Silver → Gold).

✅ A detailed breakdown of **ETL types, methods, and which ones were used in this project** is available here → [`docs/etl_methods.md`](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/etl_methods.md)

![ETL Map Thumbnail](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/etl_methods_in_project.png)

### 🧭 Architecture: Medallion Approach

| Layer | Purpose | Transformations | Load Type | Object Type |
|-------|---------|-----------------|-----------|-------------|
| **Bronze** | Raw data storage | None (as-is) | Full load (Truncate & Insert) | Tables |
| **Silver** | Clean & standardized data | Cleansing, Normalization, Enrichment | Full load | Tables |
| **Gold** | Business-ready layer | Integrations, Aggregations, Business Logic | No Load (Views only) | Views |

### 🧱 Data Warehouse Architecture

![Data Warehouse Architecture Diagram](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_architecture.drawio.png)

📌 *This diagram illustrates the full Medallion Architecture (Bronze → Silver → Gold) and how data flows across layers in SQL Server.*

### 📊 Data Modeling
The Gold layer includes star schema views, flat tables, and aggregated objects for efficient reporting and ad hoc querying.

### 📁 Source Systems
- **ERP System** — Product and sales transactions
- **CRM System** — Customer data and engagement records

---

## 📈 Phase 2: SQL-Based EDA and Advanced Data Analytics in SQL Server

### 📌 Objective
Uncover key business insights using SQL by performing:
- **Exploratory Data Analysis (EDA)**
- **Advanced Business Analytics**
- **Segmentation, Performance Tracking, and Trend Detection**

And then **visualize these insights** using Power BI by building:
- Interactive, filterable dashboards
- Customer and product-specific drilldowns
- Dynamic Top-N analysis and What-if simulation controls

### 🔍 Analysis Topics Covered
- Customer segmentation and behavior
- Product performance analysis
- Sales and revenue trends
- Cumulative metrics and rolling calculations
- Time-based comparisons (MoM, QoQ)
- Part-to-whole analysis and contribution breakdowns

### 💡 Output
- Optimized SQL scripts for each theme
- Business questions addressed through metrics
- Reusable SQL templates for BI teams
- Power BI Dashboards

---

## 🗂️ Repository Structure

```
📁 data-warehouse-project/
├── 📁 datasets/                            # Raw datasets used for the project (ERP and CRM data)

├── 📁 docs/                                # Project documentation and architecture details
│   ├── 📄 data_architecture.drawio           # High-level project architecture (Bronze, Silver, Gold)
│   ├── 📄 data_catalog.md                    # Catalog of datasets, including field descriptions and metadata 
│   ├── 📄 data_flow.drawio                   # Visual representation of data flow across layers
│   ├── 📄 data_flow_tasks.drawio             # Flow of tasks for each layer — ingestion, cleaning, validation, documentation, etc.
│   ├── 📄 data_integration.drawio            # Visual representation that depicts how Source Tables are connected
│   ├── 📄 data_layer_specifications.drawio   # Summarizes the objectives, transformations, and targets of each layer
│   ├── 📄 data_model.drawio                  # Data model design (e.g., star schema)
│   ├── 📄 etl_methods.md                     # Brief explanation of ETL types, methods, and the ones that were used in this project
│   ├── 📄 etl_methods_in_project.png         # ETL mind map depicting types, methods, and the ones that were used in this project
│   └── 📄 naming_conventions.md              # Consistent Naming guidelines for tables, columns, and files

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

> ⚠️ **Note on Historical Data**:  
> While the dataset used in this project spans from 2011 to 2014, it was selected for its realistic structure and complexity. This allowed for a robust simulation of real-world business scenarios including data modeling, segmentation, and KPI analysis.  
> 
> The **recommendations provided** are not intended for tactical execution but to demonstrate how an analyst would draw insights and inform strategy in a production environment.

---

## 📊 Phase 3: Power BI Dashboards and Business Insights

This section demonstrates how the business-ready data from the Gold layer of the data warehouse is brought into Power BI to uncover high-impact insights. The dashboards were designed to reflect real-world business reporting needs and stakeholder storytelling.

---

<details>
<summary>🧭 <strong>Executive Dashboard</strong></summary>

### 🎯 Focus:
- Company-wide KPIs (Revenue, Profit, Orders, AOV)
- Trend analysis and YoY comparisons
- Category-level breakdowns
- Dynamic Top N product matrix (filterable by metric)

![Executive Dashboard Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Executive%20Dashboard.png)

### 🔍 Key Insights:
- **Revenue** grew to $16.3M (↑179.77%) and **Orders** surged 550% YoY — demand clearly exploded in 2013.
- However, **Avg Order Value** dropped 57% — indicating growth was volume-driven, not value-driven.
- Accessories led order volume, but high performers in Bikes contributed most to profit.
- Dynamic product matrix lets stakeholders view Top N products by Revenue, Orders, or AOV.

### ✅ Recommendations:
- Explore bundling or pricing strategies to improve AOV.
- Monitor inventory and fulfillment capacity to manage volume efficiently.

</details>

---

<details>
<summary>👥 <strong>Customer Dashboard</strong></summary>

### 🎯 Focus:
- Customer-level KPIs: Revenue per Customer, Monthly Spend, Order Frequency
- Top 100 customers by revenue and engagement
- Segment-wise donut charts: Revenue and Orders by Segment
- Time-series trends for Recency and Lifetime Value

![Customer Dashboard Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Customer%20Dashboard.png)

### 🔍 Key Insights:
- The company served **17.4K customers** in 2013 but most made **only 1.2 orders** on average.
- Revenue per Customer: **$938**, with Monthly Spend averaging **$171**.
- New Customers made up **76% of all orders**, but contributed less to revenue — pointing to a retention challenge.
- VIPs and Regulars are small in number but hold higher per-customer value.

### ✅ Recommendations:
- Launch loyalty or reactivation campaigns to increase order frequency.
- Segment-targeted promotions could convert New → Regular → VIP.

</details>

---

<details>
<summary>📦 <strong>Product Drillthrough Dashboard</strong></summary>

### 🎯 Focus:
- Deep-dive into performance of a selected product (via drillthrough)
- Key KPIs: Average Order Revenue and Average Monthly Revenue
- Price sensitivity simulation: Compare Adjusted vs Base Profit for different price points
- Dynamic product metric selection to analyze weekly and monthly trends in orders, revenue, or profit

![Product Drillthrough Screenshot](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/PBI%20-%20Product%20Drillthrough%20Dashboard.png)

### 🔍 Key Insights:
- Profit optimization scenarios allow decision-makers to simulate the financial impact of price changes.
- Weekly/ monthly metric trends help uncover seasonal dips or campaign performance, guiding better planning.

### ✅ Recommendations:
- Fine-tune product pricing using profit simulations to maximize margin without hurting volume.
- Schedule promotions around historically low-performing periods to boost sales.

</details>

---

### 📌 Dashboard Features & Highlights:
- **Slicer Panel with Bookmarks** to toggle filters by Year, Country, and Product Segment
- **Dynamic Top N Selector** (Revenue, Orders, AOV)
- **Product Drillthrough Navigation**
- **Conditional Formatting** and Trendlines to enhance storytelling
- **Parameter Controls** for simulation and deeper analysis

[Access Live Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDdlNTViNmItZDZkNC00N2FkLWE2N2EtYzdjOWZkOGIwNTRiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9)

---

## 📌 Key Deliverables

- A fully functional, SQL Server-based **modern data warehouse**

- Layered architecture following **industry-standard Medallion principles**

- Clean and reusable **SQL scripts** for analytics

- **Documentation** for the data model, transformations, and business use cases

- **Power BI Dashboards**, shared online through Power BI Service

---

## 📎 Future Enhancements

- Automating incremental loads via Change Data Capture (CDC)

- Introducing historical change tracking via SCD Type 2 for slowly changing dimensions (e.g., customer segment or product category shifts)
