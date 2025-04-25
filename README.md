# 🏦 Financial Data Engineering Pipeline with Databricks

## 📌 Project Overview

This project showcases a complete data engineering pipeline using **Azure Databricks** that implements the **Medallion Architecture** (Bronze → Silver → Gold). 

The pipeline performs the following steps:
- Extracts raw data from the **Bronze layer** in **Azure Data Lake Storage Gen2 (ADLS Gen2)**.
- Applies necessary transformations and writes the cleaned data to the **Silver layer** in **Parquet** format.
- Implements **Slowly Changing Dimension Type 1 (SCD Type 1)** logic to create a business-ready **Gold layer** in **Delta Lake** format for downstream analytics and reporting.

---

## 🗂️ Project Architecture

![Project_2 architecture](https://github.com/user-attachments/assets/f6a9949e-6f60-4c5b-9fdf-613b12095402)


### 1. 🔸 Bronze Layer (Raw Layer)

- **Description:** Raw data is manually copied into the Bronze container in ADLS Gen2.
- **Files Included:**
  - `accounts.csv`
  - `customers.csv`
  - `loans.csv`
  - `loan_payments.csv`
  - `transactions.csv`

---

### 2. ⚪ Silver Layer (Cleaned/Transformed Layer)

- **Process:**
  - Handling missing/null values
  - Data type casting
  - Joining related tables (if applicable)
- **Target:** Cleaned and structured data is saved in **Parquet** format in the Silver container.

---

### 3. 🟡 Gold Layer (Business-Ready Layer)

- **Source:** Cleaned data from the Silver layer.
- **Process:** Apply **SCD Type 1** transformations.
- **Target:** Enriched data is written in **Delta Lake** format to the Gold container in ADLS Gen2 for analytics, reporting, and consumption.

---

## 🛠️ Tools & Technologies Used

- **Azure Data Lake Storage Gen2** – Storage for Bronze, Silver, and Gold layers  
- **Azure Databricks** – Data transformation and orchestration  
- **Azure Key Vault** – Secure management of secrets and credentials  
- **Microsoft Entra ID (formerly Azure AD)** – App registration and service principal authentication for mounting ADLS  

---

## ⚙️ Databricks Job Overview

A scheduled **Databricks job** handles the pipeline with two dependent tasks:

### 🔁 Task 1: Bronze to Silver
- Transforms raw data from Bronze
- Writes cleaned data to the Silver container

### 🔁 Task 2: Silver to Gold
- Applies **SCD Type 1** logic to the Silver data
- Writes the result in Delta format to the Gold container  
- This task runs **after Task 1**

---
###  Power BI 
![power bi](https://github.com/user-attachments/assets/c2518756-90bf-4ba7-93ff-d63b8cc6b345)
