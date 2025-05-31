# SQL Data Warehouse & Analytics Project

Welcome to the **SQL Data Warehouse & Analytics Project** repository!

This project demonstrates the full cycle of a data-driven solution—from building a scalable data warehouse (using SQL Server) to performing SQL-based exploratory and advanced analytics and visualizing business insights through Power BI dashboards. The project is organized into **two key parts**:

1. **Part 1: Data Engineering — Building the Data Warehouse**
2. **Part 2: Data Analytics — SQL-based EDA & Advanced Data Analytics (generate business insights) and visualizing insights by building Power BI Dashboards**

Designed as a portfolio project, this repository showcases real-world best practices in both **data engineering** and **data analytics** using SQL Server and the Medallion Architecture.

---

## 🏢 Business Overview

This project is set in a **hypothetical mid-sized retail company** that sells consumer goods across multiple channels (e.g., online and in-store). The company uses a **CRM system** to track sales transactions along with core details of products and customers, and an **ERP system** to manage extended/ additional details of customers and products.

Due to siloed systems and lack of integrated reporting, the company struggles with generating unified insights on product performance, customer behavior, and sales trends.

To address this, a **modern data warehouse** was built using the Medallion Architecture (Bronze, Silver, Gold) in SQL Server, enabling clean, integrated, and business-ready data for analytics.

---

## 🎯 Problem Statement

The company currently faces challenges such as:
- Fragmented data across ERP and CRM systems
- Manual reporting processes with inconsistent metrics
- Inability to track customer behavior or product sales holistically

This project solves these problems by:
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

## 🧱 Part 1: Building the Modern Data Warehouse

### 📌 Objective
Design and implement a modern data warehouse using **SQL Server** to consolidate and model sales, customer, and product data from multiple source systems, enabling reliable analytical reporting.

### 🧭 Architecture: Medallion Approach

| Layer | Purpose | Transformations | Load Type | Object Type |
|-------|---------|-----------------|-----------|-------------|
| **Bronze** | Raw data storage | None (as-is) | Full load (Truncate & Insert) | Tables |
| **Silver** | Clean & standardized data | Cleansing, Normalization, Enrichment | Full load | Tables |
| **Gold** | Business-ready layer | Integrations, Aggregations, Business Logic | No Load (Views only) | Views |

## 🧱 Data Warehouse Architecture

![Data Warehouse Architecture Diagram](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_architecture.drawio.png)

📌 *This diagram illustrates the full Medallion Architecture (Bronze → Silver → Gold) and how data flows across layers in SQL Server.*

### 📊 Data Modeling
The Gold layer includes star schema views, flat tables, and aggregated objects for efficient reporting and ad hoc querying.

### 📁 Source Systems
- **ERP System** — Product and sales transactions
- **CRM System** — Customer data and engagement records

---

## 📈 Part 2: SQL-Based Analytics & Reporting

### 📌 Objective
Deliver actionable insights using SQL by performing:
- **Exploratory Data Analysis (EDA)**
- **Advanced SQL Analytics**
- **Business Metric Computation**

Visualize actionable insights using Power BI by showcasing:
- **Important KPIs**
- **Revenue and Other Trends**

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

## 📌 Key Deliverables

- A fully functional, SQL Server-based **modern data warehouse**

- Layered architecture following **industry-standard Medallion principles**

- Clean and reusable **SQL scripts** for analytics

- **Documentation** for the data model, transformations, and business use cases

- **Power BI Dashboards**, shared online through Power BI Service

## 📎 Future Enhancements

- Automating incremental loads via Change Data Capture (CDC)

- Introducing historical data for time-trend tracking
