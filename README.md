# Enterprise Sales Analytics Data Platform

An end-to-end Azure Data Engineering portfolio project that transforms GlobalMart retail data into analytics-ready datasets and a Power BI sales dashboard.

## Project Overview

GlobalMart is a retail business project used to simulate a data platform that integrates customer, product, order, payment, store, and regional data. The platform demonstrates data ingestion, lakehouse transformations, data quality checks, incremental processing, dimensional modeling, and business reporting.

## Architecture

```text
GlobalMart CSV Source Data
          |
          v
Azure Data Factory
          |
          v
Azure Data Lake Storage Gen2
       (Raw Layer)
          |
          v
Azure Databricks + PySpark
          |
          v
     Bronze Delta
          |
          v
     Silver Delta
          |
          v
 Gold Star Schema / Delta
          |
          v
       Power BI
```

## Technology Stack

- **Azure Data Factory (ADF):** Data ingestion and pipeline experimentation
- **Azure Data Lake Storage Gen2 (ADLS Gen2):** Cloud storage for raw and transformed datasets
- **Azure Databricks:** Distributed data processing
- **PySpark:** Data cleansing, transformation, joins, and validation
- **Delta Lake:** Delta tables and incremental `MERGE` processing
- **Power BI:** Sales analytics and interactive reporting
- **GitHub:** Version control and project documentation

## Data Sources

The project uses custom-created CSV datasets:

- Customers
- Products
- Orders
- Order items
- Payments
- Stores
- Regions

An additional deliberately corrupted customer dataset is used to test data quality rules.

## Data Engineering Implementation

### 1. Raw Layer

CSV source datasets are stored in ADLS Gen2 to preserve the incoming data before transformation.

### 2. Bronze Layer

Loaded source datasets into Delta format using PySpark. The Bronze layer provides a structured starting point for downstream processing.

### 3. Silver Layer

Applied data cleansing and validation, including:

- Trimming and standardizing text fields
- Normalizing email addresses
- Removing duplicate business keys
- Validating customer segments and business rules
- Checking primary-key uniqueness and referential integrity

### 4. Data Quality and Quarantine

Created a separate data quality test using intentionally corrupted customer records.

The test checks for duplicate customer IDs, missing email addresses, and invalid customer segments. Invalid records are separated into a quarantine output with rejection reasons.

### 5. Incremental Processing

Implemented incremental order processing using an `updated_date` watermark and Delta Lake `MERGE`.

The workflow demonstrates inserting new orders, updating existing orders, tracking processing progress, and testing replay behavior.

### 6. SCD Type 2 — In Progress

Implemented an initial Slowly Changing Dimension Type 2 workflow for customer history. The core version-expiration and new-version insertion logic was tested, but timestamp consistency and additional validation still require hardening.

### 7. Gold Star Schema

Built analytics-oriented dimension and fact tables:

**Dimensions**
- `dim_customer`
- `dim_product`
- `dim_store`
- `dim_date`

**Fact**
- `fact_sales`

The sales fact table uses one row per order item and includes quantity, unit price, discount, gross sales, and net sales.

Validated row counts, dimension-key uniqueness, source-key uniqueness, and fact-to-dimension key relationships.

### 8. Power BI Dashboard

Connected the Gold tables to Power BI and created interactive reporting with:

- Total Net Sales
- Total Orders
- Units Sold
- Average Order Value
- Sales Trend Over Time
- Sales by Product Category
- Sales by Region
- Monthly Sales Trend

Slicers support filtering by year, product category, and region.

## Repository Structure

The repository will contain the exported notebooks, pipeline artifacts where available, documentation, and dashboard screenshots.

```text
azure-sales-analytics-platform/
├── README.md
├── notebooks/
│   ├── bronze/
│   ├── silver/
│   ├── data_quality/
│   ├── incremental/
│   ├── scd_type_2/
│   └── gold/
├── adf/
├── powerbi/
│   └── screenshots/
└── docs/
    └── architecture/
```

*This structure is a proposed organization; folders and artifacts should be added as they are exported from the working environment.*

## Validation Highlights

- Loaded seven core business datasets into the lakehouse workflow.
- Tested customer data quality rules using a separate corrupted dataset.
- Demonstrated incremental order inserts and updates using Delta `MERGE`.
- Built a Gold star schema with 1,298 order-item fact rows in the validated dataset.
- Checked for duplicate dimension keys and missing fact-to-dimension references.
- Built a Power BI report with measures and interactive slicers.

Dataset counts and results reflect the current development data and may change as the project evolves.

## Current Limitations and Future Improvements

- Harden SCD Type 2 effective-date handling and test multiple changes and reruns.
- Use stable surrogate keys across dimension rebuilds.
- Expand incremental processing to handle late-arriving records and watermark boundaries safely.
- Generate a continuous calendar dimension and verify monthly sorting in Power BI.
- Add automated tests, orchestration monitoring, logging, and failure recovery.
- Export and document the relevant ADF pipeline artifacts.
- Add screenshots and a reproducible setup guide.

## Learning Objectives

This project is designed to develop practical skills in Azure Data Engineering, including lakehouse architecture, PySpark transformations, Delta Lake, data quality, incremental loads, dimensional modeling, and analytics delivery.

