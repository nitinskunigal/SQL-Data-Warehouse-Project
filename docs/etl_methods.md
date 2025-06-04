# ⚙️ ETL Strategy & Methods in This Project

This document outlines the ETL (Extract, Transform, Load) strategy used in the SQL Data Warehouse & Analytics Project and maps each method to real-world industry practices.

The ETL pipeline was designed to reflect common enterprise data workflows while keeping things practical for a portfolio project.

---

## 📥 Extraction

### 🔹 Extraction Methods
- ✅ **Pull Extraction**: The data warehouse pulls the data from source systems (via files).
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
- Merging CRM and ERP data into unified customer and product dimensions.

### 🔹 Derived Columns
- Examples include: Age Group, Customer Segment, Product Segment, Recency, Lifespan, AOV, etc.

### 🔹 Data Normalization & Standardization
- Mapping and standardizing values (e.g., segment codes to labels).

### 🔹 Business Rules & Logic
- Calculated columns like Total Orders, Monthly Spend, etc., based on stakeholder use cases.

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
- ✅ **Batch Processing**: Data loaded in scheduled batches (manual full-load simulation).
- ❌ Stream Processing: Not used.

### 🔹 Load Methods
- ✅ **Full Load**: All tables are truncated and reloaded.
- 🔹 Methods used:
  - **Truncate & Insert**
- ❌ Upsert, Drop/Create/Insert, Incremental Merge: Not applied.

### 🔹 Slowly Changing Dimensions (SCD)
- ✅ **SCD Type 1 (Overwrite)**:
  - Latest changes overwrite existing records (no historical tracking).
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
