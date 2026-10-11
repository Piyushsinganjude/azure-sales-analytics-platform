# Azure Data Factory

This directory documents the Azure Data Factory ingestion component of the GlobalMart Enterprise Sales Analytics Data Platform.

## Pipeline

- `pipelines/PL_INGEST_CUSTOMERS.json` — Copy Activity definition for customer CSV ingestion using Azure Data Lake Storage Gen2 datasets.

## Dependencies

- Linked service: `LS_ADLS_GlobalMart`
- Source dataset: `DS_GENERIC_SOURCE`
- Sink dataset: `DS_GENERIC_SINK`

## Important

The pipeline JSON references existing dataset definitions. The dataset names, parameters, linked-service configuration, and source and sink paths must match the actual Azure Data Factory resources before deployment.

No credentials, access keys, or secrets should be committed to this repository.
