# 📒 Source System Data Catalog

> ⚙️ **Note on Catalog Scope and Format**

This data catalog is designed from a data engineering perspective — specifically to document the structure, origin, and usage of source data files ingested into the SQL Server-based data warehouse.

In real-world projects, data analysts are often provided a **consumer-facing data catalog**, which includes connection info (e.g., database server names), access owners, and table-level descriptions tailored for querying and reporting. However, since this is a **portfolio project** with a **single SQL Server instance**, **limited source files**, and **only a few final Gold Layer virtual tables (views)**, such a consumer-facing catalog would be redundant.

To help clarify the distinction, here’s a quick snapshot:

| Aspect | This Data Catalog (Project-Specific) | Consumer-Facing Catalog (Real-World) |
|--------|--------------------------------------|--------------------------------------|
| Audience | Data Engineer / Project Author | Data Analysts, Report Developers |
| Focus | Traceability from raw CSVs to warehouse | Table availability, ownership, and usage |
| Tables Included | Bronze & Silver layer inputs | Gold or curated reporting layer |
| Owners Listed | Yes — includes original system owners (e.g., ERP/CRM managers) | Yes — includes Data Engineers, Data Stewards |
| Format | Markdown + Excel | Often internal web apps or metadata tools |

The Excel version of this catalog (included in the [`docs/data_catalog_source_system.xlsx`](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_catalog_source_system.xlsx)) provides the same structure in spreadsheet form for quick navigation and sharing.

The source system data catalog lists the raw source tables ingested into the data warehouse from simulated **ERP** and **CRM** systems. It captures essential metadata including the source system, table name, purpose, currency, and ownership — aligning with industry best practices in data governance.

| **Source System** | **Table Name (CSV)**         | **Description**                                                                 | **Currency** | **Granularity**     | **Data Owner (Contact)**     |
|-------------------|--------------------------|---------------------------------------------------------------------------------|--------------|-----------------------|-------------------------------|
| CRM               | crm_sales_details        | Transaction-level records of customer purchases and order activity              | USD          | Daily (Transactional) | David Lee (CRM Manager)       |
| CRM               | crm_prd_info             | Current and historical product metadata including costs and other attributes    | USD          | Master Data           | David Lee (CRM Manager)       |
| CRM               | crm_customer_info        | Core customer data such as name, gender, marital status, and customer ID        | N/A          | Master Data           | David Lee (CRM Manager)       |
| ERP               | erp_px_cat_g1v2          | Product category mapping and hierarchy info (category, subcategory, line)       | N/A          | Reference Data        | Jane Smith (ERP Manager)      |
| ERP               | erp_cust_az12            | Additional customer information such as birthdate                               | N/A          | Reference Data        | Jane Smith (ERP Manager)      |
| ERP               | erp_loc_a101             | Customer location and geography (country-level granularity)                     | N/A          | Reference Data        | Jane Smith (ERP Manager)      |

📌 *Note: These files are simulated CSVs used for educational purposes. Contact names are fictional. This catalog is structured to reflect how metadata is captured in real-world data integration projects.*
