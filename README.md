# Azure Databricks Storage Access Configuration

To allow Azure Databricks to access data stored in Azure Blob Storage or Azure Data Lake Storage, role-based access control (RBAC) must be configured in Azure.

## Role Assignment

### The following role was assigned:

- Setting	Value
- Role	Storage Blob Data Contributor
- Assign access to	Managed Identity
- Member Name	databricks-access-connector
- Object ID	fba533a6-d61e-4322-b2fe-ab9f2a8109b1
- Type	Access Connector for Azure Databricks
- Description	Optional
- Purpose of the Role

The Storage Blob Data Contributor role allows Azure Databricks to:

- Read data from storage

- Write data to storage

- Modify blobs and files

- Process data pipelines

This role is required when Databricks needs to access data stored in Azure storage systems.

## Access Connector

The Access Connector for Azure Databricks provides a secure way for Databricks to authenticate with Azure storage using a managed identity instead of using secrets or access keys.

Benefits include:

Improved security

No need to store credentials in notebooks

Managed authentication through Azure identity services

Typical Architecture
Azure Data Lake Storage
        │
        │ (RBAC: Storage Blob Data Contributor)
        │
Access Connector for Azure Databricks
        │
        │
Azure Databricks Workspace
        │
        │
Spark Processing / Delta Tables
Key Notes

The role is assigned at the storage account or container level.

Databricks uses the managed identity of the access connector to authenticate.

This setup is commonly used when mounting storage or accessing data using ABFSS paths.

Example storage path:

abfss://container@storageaccount.dfs.core.windows.net/

