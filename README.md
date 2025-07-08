# 🚗 Car Sales End-to-End Data Engineering Project using Azure & Databricks

This project presents a scalable end-to-end data pipeline designed for processing and analyzing car sales data using the **Azure Cloud** and **Databricks** ecosystem.

---

## 🧭 Project Overview

The pipeline ingests car sales data from a github repository into **Azure SQL Database**, processes it through a multi-layered transformation pipeline in **Databricks**, and outputs a structured **star schema** suitable for downstream reporting.

It automates:

- Data ingestion from GitHub → Azure SQL DB
- ETL transformations using Delta Lake (Bronze → Silver → Gold)
- Dimensional modeling with fact and dimension tables
- Visualization/reporting via Power BI

---

## 🗺️ Architecture

The architecture follows a modern **lakehouse pattern**, enabling scalable and secure data engineering.



---

## ⚙️ Azure Data Factory Pipeline

![Azure Data Factory Pipeline](https://github.com/jotstolu/Car-Sales-End-to-End-Data-Engineering-Project-using-Azure-Databricks/blob/main/asset/Azure%20Data%20factory%20pipeline.png?raw=true)

This pipeline automates the **ingestion phase**, pulling data from GitHub and loading it into Azure SQL Database.

- **Lastload** and **current_load** lookups help manage incremental load logic.
- Data is copied into the **Bronze Layer** (raw zone).
- A **stored procedure** updates the watermark after successful ingestion.



---

## 🔁 Databricks Workflow & Data Model

![Databricks Data Model Pipeline](./assets/databricks_data_model_pipeline.png)

The Databricks pipeline implements the **medallion architecture** using Delta Live Tables:

| Layer    | Description |
|----------|-------------|
| **Silver** | Cleaned and normalized data from the bronze layer |
| **Gold**   | Dimension and fact tables ready for analytics/reporting |



---

## 🧱 Notebook Structure

The project consists of the following transformation notebooks:

```
cars_sales_project/
├── Silver_Notebook.python         # Initial silver layer transformations
├── Gold DimBranch.python          # Branch dimension table
├── Gold DimDate.python            # Date dimension table
├── Gold DimDealer.python          # Dealer dimension table
├── Gold DimModel.python           # Model dimension table
├── Gold_fact_sales.python         # Fact table for car sales
```

Each notebook processes data from the silver layer and applies business logic for gold layer generation.

---

## 🛠️ Technologies Used

- **Azure Data Factory** – Orchestrates data movement and ingestion
- **Azure SQL Database** – Temporary data storage post-ingestion
- **Azure Data Lake Gen2** – Scalable and secure data storage layer
- **Databricks (Delta Live Tables)** – Data transformation & processing
- **Delta Lake Format** – Supports ACID transactions & versioning
- **Power BI** – Reporting and visualization layer
- **GitHub** – Source control for dataset and notebooks

---

## 📊 Output: Star Schema

The **Gold Layer** produces a **Star Schema**:

- Central `Fact_Sales` table
- Dimensions: `Dim_Branch`, `Dim_Dealer`, `Dim_Model`, `Dim_Date`


