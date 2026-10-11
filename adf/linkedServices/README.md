# Azure Data Factory Linked Services

## ADLS Gen2 Connection

The GlobalMart project uses an Azure Data Factory linked service named `LS_ADLS_GlobalMart` to connect to Azure Data Lake Storage Gen2.

### Purpose
- Establish connectivity between Azure Data Factory and the GlobalMart storage account.
- Support source and destination datasets used by ingestion pipelines.
- Enable data movement between configured storage paths.

### Security
Authentication and credentials are configured in Azure Data Factory. Secrets, access keys, tokens, and sensitive connection details must not be committed to this repository.

### Dependencies
- Storage account: `globalmartpiyush`
- Container / filesystem: `globalmart`
- Linked service: `LS_ADLS_GlobalMart`

This document describes the project configuration; it is not an exported linked-service definition.
