# Databricks Notebooks

This directory contains the PySpark notebooks developed for the GlobalMart Enterprise Sales Analytics Data Platform.

## Notebooks

- `01_Bronze_Ingestion.ipynb` — Loads raw CSV datasets into Bronze Delta tables.
- `01_Silver_Customers.ipynb` — Cleans and standardizes customer data.
- `01_Customer_Data_Quality.ipynb` — Tests customer data quality and quarantines rejected records.
- `01_Incremental_Orders.ipynb` — Demonstrates watermark-based incremental order processing with Delta MERGE.
- `01_Customer_SCD_Type_2.ipynb` — Implements the initial customer history-tracking workflow; further validation is needed.
- `gold/01_Gold_Star_Schema.ipynb` — Builds the analytics-ready star schema, when placed in the Gold folder.

## Technology

Azure Databricks, PySpark, Delta Lake, and Azure Data Lake Storage Gen2.
