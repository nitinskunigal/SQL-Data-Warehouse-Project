# 📒 Source System Data Catalog

This catalog lists the raw source tables ingested into the data warehouse from simulated **ERP** and **CRM** systems. It captures essential metadata including the source system, table name, purpose, currency, and ownership — aligning with industry best practices in data governance.

| **Source System** | **Table Name (CSV)**         | **Description**                                                                 | **Currency** | **Granularity**     | **Data Owner (Contact)**     |
|-------------------|--------------------------|---------------------------------------------------------------------------------|--------------|-----------------------|-------------------------------|
| CRM               | crm_sales_details        | Transaction-level records of customer purchases and order activity              | USD          | Daily (Transactional) | David Lee (CRM Analyst)       |
| CRM               | crm_prd_info             | Current and historical product metadata including costs and other attributes    | USD          | Master Data           | David Lee (CRM Analyst)       |
| CRM               | crm_customer_info        | Core customer data such as name, gender, marital status, and customer ID        | N/A          | Master Data           | David Lee (CRM Analyst)       |
| ERP               | erp_px_cat_g1v2          | Product category mapping and hierarchy info (category, subcategory, line)       | N/A          | Reference Data        | Jane Smith (ERP Manager)      |
| ERP               | erp_cust_az12            | Additional customer information such as birthdate                               | N/A          | Reference Data        | Jane Smith (ERP Manager)      |
| ERP               | erp_loc_a101             | Customer location and geography (country-level granularity)                     | N/A          | Reference Data        | Jane Smith (ERP Manager)      |

📌 *Note: These files are simulated CSVs used for educational purposes. Contact names are fictional. This catalog is structured to reflect how metadata is captured in real-world data integration projects.*
