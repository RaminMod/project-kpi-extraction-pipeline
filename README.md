# 📊 Project Manager Assistant – Data Extraction Pipeline

## Overview

This project aims to **automate the extraction, structuring, and summarization of project information** from multiple document types (Word, PowerPoint, Excel) using **Large Language Models (LLMs)**.

The goal is to help **project managers and decision-makers** quickly understand project status, KPIs, risks, and progress without manually reading long and scattered documents.

---

## 🚩 Business Problem

Project-related information is often:
- Spread across multiple documents and formats
- Time-consuming to read and understand
- Difficult to summarize consistently
- Not available as a structured dataset

Managers spend a significant amount of time reviewing documents instead of focusing on decision-making.

---

## 🎯 Project Objectives

- Create a **unified and structured dataset** from unstructured project documents
- Reduce manual reading and interpretation time
- Enable **automated insights, summaries, and dashboards**
- Improve visibility of project status and KPIs
- Support management with data-driven decisions

---

## 🧠 Solution Approach

The project implements an **automated data extraction pipeline** using modern data and AI technologies.

### High-level Steps

1. **Document Ingestion**
   - Input formats: Word, PowerPoint, Excel
   - Centralized storage

2. **Data Processing & Cleaning**
   - Text extraction
   - Standardization and validation

3. **LLM-based Extraction**
   - Prompt engineering for structured outputs
   - Key fields: objectives, milestones, risks, KPIs, timelines

4. **Structured Output**
   - Clean datasets ready for analysis
   - Dashboard and reporting support

---

## 🏗️ Architecture & Technology Stack

- Python  
- Azure Data Lake Gen2  
- Azure Databricks (Spark)  
- Azure OpenAI  
- Prompt Engineering  
- Structured Data Storage  

---

## 📈 Expected Benefits

- ⏱️ Save **10–12 hours per month** per manager
- 📉 Reduce manual errors and inconsistencies
- 📊 Enable faster reporting and dashboards
- 🔍 Improve project transparency and control
- ♻️ Support sustainability and efficiency goals

---

## 📂 Repository Structure (Example)

```text
├── data/
│   ├── raw_documents/
│   └── processed_data/
├── notebooks/
│   └── data_extraction_pipeline.ipynb
├── prompts/
│   └── extraction_prompts.md
├── outputs/
│   └── structured_results/
├── README.md
```

*(Structure may evolve as the project progresses)*

---

## 🚀 How to Use

1. Upload project documents to the input directory
2. Run the data extraction pipeline
3. Review structured outputs
4. Use results for dashboards, summaries, or further analysis

---

## 🔮 Future Improvements

- Support for additional document formats
- Improved prompt optimization
- Automated KPI comparison across projects
- Integration with BI tools
- Advanced dashboarding

---

## 👥 Stakeholders

- Project Managers  
- Business & Operations Teams  
- Data Analysts  
- Management & Decision Makers  

---

## 📌 Project Status

**Phase:** Active development  
**Focus:** Data extraction, structuring, and LLM optimization
