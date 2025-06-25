# Data Cleaning & Transformation Approaches

This document outlines the key data cleaning and transformation techniques applied in this project prior to inserting data into the Silver Layer of the data warehouse.

## 💡 Purpose

To ensure data quality, consistency, and analytical readiness by addressing missing values, invalid formats, duplicates, standardization issues, and business logic gaps.

## 🔧 Transformations Applied

| Transformation Type | Description | Example |
|---------------------|-------------|---------|
| **Whitespace Trimming** | Removed leading and trailing spaces | `TRIM(ColumnName)` in SQL |
| **Standardizing Codes** | Replaced coded values with meaningful labels | `'M' → 'Male'`, `'DE' → 'Germany'` |
| **Handling NULLs** | Replaced missing values with defaults | `ISNULL(sales, 0)` or `ISNULL(gender, 'n/a')` |
| **Removing Duplicates** | Applied ROW_NUMBER() to isolate valid rows by primary key | Retained row with latest timestamp |
| **Derived Columns** | Created analytical columns using existing ones | `SUBSTRING(product_id, 1, 3) AS prd_key` |
| **Data Type Casting** | Ensured consistent formats across columns | `CAST(date_column AS DATE)` |
| **Business Rule Enforcement** | Applied rules to calculate missing sales or price | If price missing, then `Sales / Quantity` |
| **Data Enrichment** | Inferred values using window functions | Derived product end date using next start date |

## 🧠 Key Business Rules Applied

1. **Sales Backfill**: If sales is missing or 0 → derive as `Price * Quantity`
2. **Price Backfill**: If price is missing → derive as `Sales / Quantity`
3. **Negative Price Correction**: If price < 0 → convert to absolute value
4. **Date Enrichment**: Populate `prd_end_dt` using lead value of `prd_start_dt` from next row

## ✅ Outcome

- Improved data consistency and completeness across all Silver Layer tables
- Enabled accurate reporting and trend analysis in the Gold Layer
- Ensured business stakeholders could trust the output reflected real-world logic
