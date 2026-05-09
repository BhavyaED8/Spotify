
# Spotify End-to-End Data Engineering Pipeline (Azure & Databricks)

## 📌 Project Overview
This project demonstrates a production-grade data engineering workflow using the **Medallion Architecture**. It automates the ingestion, transformation, and modeling of music streaming data from an on-premise source (simulated via Azure SQL) into a governed **Delta Lake** using the latest Databricks and Azure features.

## 🏗 Architecture Diagram
*Source (Azure SQL) -> Ingestion (ADF) -> Landing (Bronze) -> Transformation (Silver/Databricks) -> Analytics (Gold/Delta Lake)*

## 🚀 Key Technical Features

### 1. Dynamic Ingestion (Bronze Layer)
- **Azure Data Factory (ADF):** Developed a fully parameterized pipeline to migrate data from Azure SQL to ADLS Gen2.
- **Incremental Loading:** Implemented a watermark-based logic to handle delta loads and backfilling, ensuring only new transaction data is processed.

### 2. Streamlined Transformation (Silver Layer)
- **Databricks Autoloader:** Utilized for high-performance, incremental ingestion into the Silver layer with built-in schema evolution support.
- **PySpark Processing:** Performed data cleaning, deduplication, and standardization using PySpark DataFrames.
- **Custom Utilities:** Created a modular Python utility class to handle repetitive transformations (e.g., column dropping, case formatting).

### 3. Advanced Data Modeling (Gold Layer)
- **Metadata-Driven Views:** Leveraged **Jinja2** templating to dynamically generate SQL business views, enabling a scalable "write-once, run-anywhere" code pattern.
- **SCD Type 2:** Implemented Slowly Changing Dimensions (Type 2) to track historical changes in artist and user metadata over time.
- **Delta Live Tables (DLT):** Used DLT to manage the pipeline lifecycle and ensure data quality through **DLT Expectations** (data validation rules).

### 4. Governance & DevOps
- **Unity Catalog:** Centralized access control, lineage tracking, and data discovery.
- **Databricks Asset Bundles (DABs):** Managed the project lifecycle with a professional CI/CD approach, deploying resources via YAML-based configurations.
- **Logic Apps:** Integrated automated alerts for pipeline failures via HTTP webhooks.

## 🛠 Tech Stack
* **Orchestration:** Azure Data Factory
* **Compute:** Azure Databricks (Serverless)
* **Storage:** Azure Data Lake Storage Gen2 (ADLS)
* **Database:** Azure SQL (Source)
* **Governance:** Unity Catalog
* **Language:** PySpark (Python), Spark SQL
* **DevOps:** GitHub, Databricks Asset Bundles, Jinja2

ADF Pipeline Structure:

<img width="924" height="239" alt="image" src="https://github.com/user-attachments/assets/72da0d26-fe65-447b-88d7-c125b117b675" />
