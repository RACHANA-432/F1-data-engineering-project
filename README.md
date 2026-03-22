# 🏎️ F1 Data Engineering Project (Azure + Databricks)

## 📌 Overview

This project demonstrates a complete **end-to-end data engineering pipeline** built on Azure, designed using industry-standard best practices like **Medallion Architecture**, **Delta Lake**, and **Unity Catalog**.

The goal is to ingest raw Formula 1 data, process and transform it into structured, high-quality datasets, and make it analytics-ready for reporting and visualization.

---

## 🏗️ Architecture

**Flow:**

GitHub (CSV Data)
→ Azure Data Factory (Ingestion)
→ Azure Data Lake Storage (Bronze Layer)
→ Azure Databricks (Transformation using PySpark)
→ Delta Tables (Silver & Gold Layers)
→ Power BI (Visualization)

---

## 🧱 Medallion Architecture

This project follows the **Medallion Architecture**, which organizes data into three layers:

### 🥉 Bronze Layer (Raw Data)

* Stores raw ingested data from source
* Data is stored in **Parquet format**
* No transformations applied
* Acts as a historical source of truth

👉 Example:

* Raw CSV data ingested via ADF into ADLS

---

### 🥈 Silver Layer (Cleaned Data)

* Data is cleaned, standardized, and transformed
* Handles:

  * Null values
  * Data type casting
  * Deduplication
  * Column renaming

👉 Output:

* Stored as **Delta Tables**
* Optimized for querying and further transformations

---

### 🥇 Gold Layer (Business-Level Data)

* Aggregated and business-ready datasets
* Used for analytics and reporting

👉 Examples:

* Driver standings
* Constructor performance
* Race results summary

---

## ⚙️ Core Technologies & Concepts

### 🔹 Azure Data Factory (ADF)

* Used for orchestrating data ingestion pipelines
* Pulls data from GitHub and loads into ADLS
* Parameterized pipelines for scalability

---

### 🔹 Azure Data Lake Storage (ADLS)

* Stores data in layered architecture (Bronze, Silver, Gold)
* Supports scalable and cost-effective storage

---

### 🔹 Azure Databricks (PySpark)

* Used for data transformation and processing
* Handles large-scale distributed data processing

---

## 🔄 Data Transformation Details (Databricks)

Transformations include:

* Schema enforcement
* Data cleansing (handling nulls, incorrect formats)
* Deduplication logic
* Joins between multiple datasets (drivers, races, constructors)
* Deriving new columns (e.g., race rankings, points calculations)
* Incremental data processing (if implemented)

Example:

* Joining race results with driver and constructor data
* Calculating total points per driver

---

## 🪨 Delta Lake & Delta Tables

This project uses **Delta Lake** for reliable and optimized data storage.

### Key Features Used:

* ACID Transactions
* Schema Enforcement
* Time Travel (versioning)
* Efficient upserts (MERGE operations)

### Why Delta Tables?

* Faster query performance
* Reliable data consistency
* Supports incremental loads

---

## 🗂️ Unity Catalog (Data Governance)

Unity Catalog is used for centralized data governance and access control.

### Components:

#### 📦 Metastore

* Central repository to manage metadata
* Stores information about tables, schemas, and permissions

---

#### 🔐 Credentials

* Secure access to external storage (ADLS)
* Managed via service principals or managed identities

---

#### 📍 External Locations

* Maps ADLS storage paths to Databricks
* Enables secure and governed data access

---

#### 🗃️ Catalogs & Schemas

* Organizes data into logical layers
* Example:

  * Catalog: `f1_data`
  * Schemas: `bronze`, `silver`, `gold`

---

---

## 📊 Data Pipeline Workflow

### Step 1: Ingestion

* Azure Data Factory extracts CSV data from GitHub
* Loads raw data into ADLS Bronze layer

---

### Step 2: Transformation

* Databricks notebooks process Bronze data
* Cleaned and transformed into Silver layer

---

### Step 3: Data Modeling

* Business transformations applied
* Gold layer tables created

---

### Step 4: Visualization

* Power BI connects to Gold layer
* Interactive dashboards created

---

## 📸 Power BI Report

<img width="1742" height="746" alt="Power BI Report" src="https://github.com/user-attachments/assets/09937b0a-2ae5-45f3-861c-2ae2540f4ebe" />


---

## 📸 ADF Pipeline

<img width="1915" height="912" alt="ADF Pipeline - F1" src="https://github.com/user-attachments/assets/b05f6805-a184-4974-8597-32d0ce680ceb" />


---

## 📊 Sample Data

Sample datasets are available in `/dataset`.

---

## 🚀 Key Features

* Medallion Architecture (Bronze, Silver, Gold)
* Scalable Data Pipeline using Azure Services
* Delta Lake for optimized storage
* Unity Catalog for governance
* Modular and reusable notebooks
* End-to-end pipeline automation

---

## 🔮 Future Enhancements

* Implement logging framework (log tables in Delta)
* Add data quality validation layer
* CI/CD pipeline integration (Azure DevOps)
* Real-time data ingestion (Streaming)
* Performance optimization (Z-ordering, caching)

---

## 👩‍💻 Author

Rachana Chavan

---

## ⭐ Conclusion

This project showcases an end-to-end data engineering pipeline with modern tools and best practices, making it scalable, maintainable, and industry-ready.
