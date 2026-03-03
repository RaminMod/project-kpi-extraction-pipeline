# Azure Infrastructure Setup

This document explains how the Azure infrastructure for this project was created, step by step.

Everything described here reflects the exact setup used in `data_extraction_pipeline.ipynb`.  
Nothing more, nothing less.

The goal of this setup is to create a clean, simple, and cost-efficient environment to store project documents and generated KPI outputs.

---

## 1. Resource Group

First, a dedicated resource group was created:

`rg-kpi-pipeline-dev`

I created this resource group to keep everything related to this pipeline isolated and organized.

Using a separate resource group helps with:

- Keeping the project clean and separated from other environments  
- Tracking costs more easily  
- Deleting everything safely if needed  
- Maintaining a structured cloud setup  

At this stage, only the storage account is placed inside this resource group.

---

## 2. Storage Account

A storage account was created with the following configuration:

- Performance: **Standard**
- Redundancy: **Locally Redundant Storage (LRS)**
- Access Tier: **Hot**
- Hierarchical Namespace: **Enabled**
- Public access: **Disabled**

Enabling Hierarchical Namespace is important because it turns the storage into **Azure Data Lake Storage Gen2 (ADLS Gen2)**.

This allows:

- Folder-like directory structure  
- Compatibility with Spark and Databricks  
- Efficient file handling  
- A proper data lake structure  

This storage account acts as the central data lake for the pipeline.

---

## 3. Container

Inside the storage account, a container was created:

`kpi-pipeline`

You can think of the container as the main root directory of the project inside Azure.

All files processed by the notebook are stored inside this container.

---

## 4. Folder Structure

Inside the container, the following structure was created:
