# ⚙️ ETL Strategy & Methods in This Project

This document outlines the ETL (Extract, Transform, Load) strategy used in the SQL Data Warehouse & Analytics Project and maps each method to real-world industry practices.

The ETL pipeline was designed to reflect common enterprise data workflows while keeping things practical for a portfolio project.

---

## 📥 Extraction

### 🔹 Extraction Methods
- ✅ **Pull Extraction**: The data warehouse actively pulls the data from source systems (via CSV files).
- ❌ Push Extraction: Not used in this project.

### 🔹 Extraction Types
- ✅ **Full Extraction**: All records are reloaded from source every time.
- ❌ Incremental Extraction: Not applicable (source files don't support deltas).

### 🔹 Extraction Techniques
- ✅ **File Parsing**: Extracting structured data from CSV files.
- ✅ Manual extraction: Simulated for the portfolio setting.
- ❌ Database Querying, API Calls, Web Scraping, CDC, Event Streaming: Not used.

---

## 🔄 Transformation

All the following transformation techniques were applied during the project, aligning with best practices in data engineering and analytics.

### 🔹 Data Enrichment
- Enhancing datasets with derived KPIs and business logic.

### 🔹 Data Integration
- Merged ERP and CRM data sources into a unified analytical model.

### 🔹 Derived Columns
- Created meaningful attributes like Age Group, Product Segment, and Lifespan etc.

### 🔹 Data Normalization & Standardization
- Standardized naming conventions, codes, and categories.

### 🔹 Business Rules & Logic
- Calculated columns like Total Orders, Monthly Spend, Customer Segmentation (New, Regular, VIP), Product Tiering, etc., based on stakeholder use cases.

### 🔹 Data Aggregations
- Performed in the Gold layer to generate summary metrics by customer/product.

### 🔹 Data Cleansing
- Removing duplicates
- Filtering invalid data
- Handling missing values
- Casting data types
- Removing unwanted spaces
- Outlier detection where applicable

---

## 📤 Load

### 🔹 Processing Types
- ✅ **Batch Processing**: Full-batch loads scheduled using SQL scripts and procedures.
- ❌ Stream Processing: Not used.

### 🔹 Load Methods
- ✅ **Full Load**: Target tables are truncated before fresh data is inserted.
- 🔹 Methods used:
  - **Truncate & Insert**
- ❌ Upsert, Drop/Create/Insert, Incremental Merge: Not applied.

### 🔹 Slowly Changing Dimensions (SCD)
- ✅ **SCD Type 1 (Overwrite)**:
  - SCD 1 updates dimension records with new values, overwriting older data (no historical tracking).
- ❌ SCD Type 2 (Historization): Not implemented in this project.

---

## 🧪 Summary of ETL Methods Used in This Project

| ETL Phase     | Method Used                          |
|--------------|---------------------------------------|
| Extraction    | Pull, Full Load, File Parsing         |
| Transformation| Enrichment, Integration, Cleansing, Business Logic |
| Load          | Batch Processing, Truncate & Insert, SCD1 Overwrite |

---

## 🧭 Visual: ETL Strategy Map

To reinforce understanding, here’s the high-level visual map of ETL methods — with checkmarks indicating the techniques used in this project.

![ETL Methods Visual](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/etl_methods_in_project.png)

---

📌 This ETL flow is flexible, modular, and aligned with foundational concepts used in industry-level data warehousing projects. While designed as a portfolio project, it simulates real-world decisions around extraction strategy, load cycles, and transformation logic.
