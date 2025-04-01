# 📁 AdventureWorks Data Sources

This project utilizes a collection of **AdventureWorks** CSV datasets as source files for implementing ETL pipelines and analytics. These files are structured and serve as the foundation for processing through the **Medallion Architecture** (Bronze → Silver → Gold) in Azure Data Factory (ADF) and Databricks.

---

## 🗂️ File Overview

| File Name                             | Description                                              | Primary Use       |
|--------------------------------------|----------------------------------------------------------|-------------------|
| `AdventureWorks_Calendar.csv`        | Calendar dimension table with dates, months, quarters    | Time intelligence |
| `AdventureWorks_Customers.csv`       | Customer details such as name, location, and ID          | Customer dimension|
| `AdventureWorks_Product_Categories.csv` | High-level product category classifications           | Product hierarchy |
| `AdventureWorks_Product_Subcategories.csv` | Subcategory mappings for each product category     | Product hierarchy |
| `AdventureWorks_Products.csv`        | Detailed product information                             | Product dimension |
| `AdventureWorks_Returns.csv`         | Return transactions with reasons and quantities          | Returns analysis  |
| `AdventureWorks_Sales_2015.csv`      | Sales transaction data for the year 2015                 | Fact table        |
| `AdventureWorks_Sales_2016.csv`      | Sales transaction data for the year 2016                 | Fact table        |
| `AdventureWorks_Sales_2017.csv`      | Sales transaction data for the year 2017                 | Fact table        |
| `AdventureWorks_Territories.csv`     | Sales territory regions and assignments                  | Geography dimension|

---

## 🧱 How These Files Fit the Medallion Architecture

| Layer     | Description                                          | Example Files                           |
|-----------|------------------------------------------------------|-----------------------------------------|
| **Bronze** | Raw ingestion into ADLS using ADF Copy Activity      | All files in their original format      |
| **Silver** | Cleaned and transformed datasets in Delta format     | Joined Sales with Customer/Product data |
| **Gold**   | Business-ready tables for reporting & dashboards     | Aggregated sales, returns, KPIs         |

---

## 💾 Data Format

- **File Type**: CSV  
- **Encoding**: UTF-8  
- **Delimiter**: `,` (Comma)  
- **Headers**: Present in all files  
- **Storage Location**: Azure Data Lake Storage (ADLS)

---

## 🔐 Access & Security

All CSVs are ingested from a secured storage location:
- Stored in ADLS Gen2 (container: `/raw/adventureworks/`)
- Access managed via Azure Key Vault and Managed Identity in ADF

---

## 🔍 Usage in ETL Pipelines

- **Ingestion**: Handled by Azure Data Factory Copy Activity
- **Transformation**: Conducted using Databricks with PySpark
- **Output**: Transformed data stored in Silver and Gold layers for Power BI reporting

---

