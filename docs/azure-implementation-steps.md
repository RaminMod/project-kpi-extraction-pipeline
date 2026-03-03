# Azure Implementation Steps

This document explains exactly how the Azure infrastructure for this project was created, step by step.

The goal was to create a clean, minimal, and cost-efficient environment to support the KPI extraction pipeline implemented in `data_extraction_pipeline.ipynb`.

All steps below reflect the actual configuration used in this project.

---

## Step 1 – Create a Resource Group

1. Log in to the Azure Portal.
2. Click **Create a resource**.
3. Search for **Resource group**.
4. Click **Create**.

Configuration used:

- Subscription: `Visual Studio Enterprise Subscription – MPN`
- Resource group name: `rg-kpi-pipeline-dev`
- Region: (same region used later for storage)

Click **Review + create**, then **Create**.

This resource group is used to logically isolate all resources related to this project.

---

## Step 2 – Create the Storage Account

1. In the Azure Portal, click **Create a resource**.
2. Search for **Storage account**.
3. Click **Create**.

### Basic Configuration

- Subscription: `Visual Studio Enterprise Subscription – MPN`
- Resource group: `rg-kpi-pipeline-dev`
- Storage account name: `stkpipipeline01`
- Region: Same as resource group
- Performance: **Standard**
- Redundancy: **Locally Redundant Storage (LRS)**

LRS was selected to keep costs minimal.

---

### Advanced Configuration

In the **Advanced** tab:

- Enable **Hierarchical namespace** → ✔ Enabled

Enabling hierarchical namespace converts the storage into Azure Data Lake Storage Gen2 (ADLS Gen2), which supports folder structures and works properly with Spark and Databricks.

Other settings were left as default.

---

### Networking

- Public endpoint: Default
- No private endpoints configured

---

### Data Protection

All optional features were left disabled.

---

### Review and Create

Click **Review + create**, then **Create**.

After deployment completes, open the storage account.

---

## Step 3 – Create the Container

1. Open the created storage account (`stkpipipeline01`).
2. In the left menu, go to **Data storage → Containers**.
3. Click **+ Container**.

Configuration used:

- Name: `kpi-pipeline`
- Public access level: **Private (no anonymous access)**

Click **Create**.

This container acts as the root directory for the project data.

---

## Step 4 – Create Folder Structure

Inside the `kpi-pipeline` container, create the following directories:

- `raw_documents`
- `intermediate`
- `outputs`

This structure reflects the logical stages of the pipeline:

- `raw_documents` → original input files (.docx, .xlsx, .pptx)
- `intermediate` → extracted combined text (e.g., `all_content.txt`)
- `outputs` → structured KPI JSON output (`output.json`)

---

## Step 5 – Storage Access from Databricks

Storage access is configured in the notebook using:

- A SAS token
- Databricks secret scope
- Spark configuration with ABFS protocol

The notebook constructs storage paths using:

abfss://<container>@<storage_account>.dfs.core.windows.net/<path>


This allows:

- Reading files from `raw_documents`
- Writing intermediate files
- Writing structured JSON outputs

No DBFS mounting is used in this implementation.

---

## Cost Considerations

The infrastructure was intentionally configured to remain cost-efficient:

- Standard storage (not Premium)
- LRS redundancy
- No advanced networking features
- No private endpoints
- No additional Azure services deployed

This keeps the environment minimal while fully supporting the KPI extraction pipeline.

---

This completes the Azure infrastructure setup required to run the project.