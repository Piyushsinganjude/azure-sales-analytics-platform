# GlobalMart Architecture

This folder documents the end-to-end architecture of the GlobalMart Enterprise Sales Analytics Data Platform.

The architecture covers:

- **Source:** Simulated GlobalMart retail CSV datasets.
- **Ingestion:** Azure Data Factory (ADF).
- **Storage:** Azure Data Lake Storage Gen2 (ADLS Gen2).
- **Processing:** Azure Databricks and PySpark.
- **Data layers:** Bronze, Silver, and Gold using Delta tables.
- **Advanced engineering:** Incremental order processing, customer SCD Type 2, and data quality validation.
- **Reporting:** Power BI sales analytics dashboard.

## Architecture Diagram

See `globalmart_architecture.png` for the architecture overview.

**Note:** The diagram illustrates the intended end-to-end design. Some ADF pipeline definitions are reconstructed documentation and should not be considered deployed or verified until tested in Azure Data Factory.

## Architecture

![GlobalMart Architecture](docs/architecture/globalmart_architecture.png)
