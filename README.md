# FinWealth Advisors – Wealth Analytics Data Platform

## 📌 Project Overview

FinWealth Advisors required a centralized cloud-based analytics platform to consolidate wealth management data from multiple operational systems into a scalable Data Warehouse for reporting and business intelligence.

This project demonstrates the complete implementation of an **end-to-end Azure Data Engineering Solution** using:

* Microsoft Azure
* Azure Data Factory (ADF)
* Azure SQL Database
* Azure Blob Storage
* SQL Stored Procedures
* ADF Mapping Data Flows
* Power BI Ready Analytical Views

The platform ingests raw CSV data, validates it, transforms it into a Star Schema Data Warehouse, and prepares analytical datasets for reporting and dashboarding.

---

# 🚀 Architecture Overview

## End-to-End Pipeline Flow

```text
CSV Files
   ↓
Azure Blob Storage
   ↓
ADF Copy Pipelines
   ↓
Staging Tables
   ↓
Validation Layer
   ↓
Dimension Loading (Stored Procedures)
   ↓
Fact Loading (ADF Mapping Data Flows)
   ↓
Star Schema Data Warehouse
   ↓
Power BI Analytical Views
```

---

# 🛠️ Technologies Used

| Technology             | Purpose                        |
| ---------------------- | ------------------------------ |
| Azure Blob Storage     | Store raw CSV source files     |
| Azure SQL Database     | Data Warehouse & Staging Layer |
| Azure Data Factory     | ETL Orchestration              |
| SQL Stored Procedures  | Dimension Loading Logic        |
| ADF Mapping Data Flows | Fact Table Transformations     |
| Power BI               | Analytics & Dashboarding       |
| GitHub                 | Version Control                |

---

# 📂 Source Data

The project processes **12 CSV files** containing wealth management data.

| File            | Description                 |
| --------------- | --------------------------- |
| Clients.csv     | Client information          |
| Advisors.csv    | Advisor details             |
| Accounts.csv    | Account information         |
| Securities.csv  | Security master data        |
| Trades.csv      | Buy/Sell transactions       |
| Holdings.csv    | Portfolio holdings          |
| Cashflows.csv   | Deposits & Withdrawals      |
| Fees.csv        | Advisory & Management fees  |
| Prices.csv      | Daily security prices       |
| Benchmarks.csv  | Benchmark index data        |
| Performance.csv | Monthly performance metrics |
| DataDictonary.csv|  About What Files Are there|

---

# 🏗️ Data Warehouse Design

## ⭐ Star Schema

### Dimension Tables

* Dim_Client
* Dim_Advisor
* Dim_Account
* Dim_Security
* Dim_Benchmark
* dim_date

### Fact Tables

* Fact_Trades
* Fact_Cashflows
* fact_fees
* fact_holdings
* Fact_Performance

---

# ⚙️ ETL Pipeline Design

## 1️⃣ Staging Layer

Raw CSV data is loaded into staging tables using ADF Copy Activities.

### Features

* Pre-copy TRUNCATE scripts
* Batch tracking
* Source file tracking
* Audit columns

---

## 2️⃣ Validation Layer

A dedicated validation stored procedure checks:

* NULL primary keys
* Duplicate IDs
* Referential integrity
* Invalid business values
* Row count thresholds

### Real Validation Issue Solved

* Identified and removed **400 duplicate TradeIDs** from source data.

---

## 3️⃣ Dimension Loading

Dimension tables are loaded using SQL Stored Procedures implementing:

* SCD Type 1 Logic
* Surrogate Key Generation
* Derived Columns
* NULL Handling
* Idempotent Loading

---

## 4️⃣ Fact Loading

Fact tables are loaded using ADF Mapping Data Flows.

### Transformations Included

* Multi-source joins
* Lookup transformations
* Derived columns
* Date surrogate key generation
* Business rule implementation

---

# 📊 Business Rules & Transformations

## NULL Handling Rules

| Data Type   | Replacement  |
| ----------- | ------------ |
| Text        | 'Unknown'    |
| Date        | '1900-01-01' |
| Numeric     | 0            |
| Key Columns | Row Rejected |

---

## Derived Columns

### Examples

* ClientTier
* ExperienceBand
* CurrencyGroup
* AssetClassGroup
* TradeCategory
* TradeSize
* FlowDirection
* PerformanceBand

---

# 🔄 ADF Pipelines

## Main Pipelines

### PL_Copy_CSV_To_Staging_To_DWH

* Loads CSV files to staging
* Executes dimension stored procedures

### PL_Validation

* Runs staging validation logic
* Writes to audit/error logs

### PL_Load_Fact

* Executes all Mapping Data Flows

### PL_Master

Master orchestration pipeline controlling the full ETL workflow.

---

# 📈 Analytical Views for Power BI

Created **13 analytical SQL views** including:

* AUM Summary
* Performance Dashboard
* Advisor Performance
* Product Mix Analysis
* Trade Summary
* Fee Summary
* Risk Analysis

These views are optimized for direct Power BI consumption.

---

# 📊 Final Data Warehouse Row Counts

| Table            | Rows    |
| ---------------- | ------- |
| Dim_Client       | 8,000   |
| Dim_Advisor      | 350     |
| Dim_Account      | 12,000  |
| Dim_Security     | 3,000   |
| Fact_Trades      | 100,000 |
| Fact_Cashflows   | 30,000  |
| fact_fees        | 18,000  |
| fact_holdings    | 96,027  |
| Fact_Performance | 110,000 |

---

# 🔥 Key Features

✅ End-to-End Azure Data Engineering Project
✅ Fully Automated ETL Pipelines
✅ Star Schema Data Warehouse
✅ Surrogate Key Implementation
✅ SCD Type 1 Dimensions
✅ Data Validation Framework
✅ Error Logging & Audit Tracking
✅ Power BI Ready Data Model
✅ Idempotent Pipeline Design
✅ Scalable Architecture

---

# 📚 Key Learnings

* Hybrid ETL approach using Stored Procedures + Data Flows
* Spark optimization techniques in ADF
* Handling duplicate and bad source data
* Designing scalable star schema models
* Building enterprise-grade validation frameworks
* Creating reusable analytical views

---

# 📸 Project Components

## Azure Services Used

* Azure Data Factory
* Azure SQL Database
* Azure Blob Storage

## Data Engineering Concepts

* ETL Pipelines
* Data Warehousing
* Star Schema
* Slowly Changing Dimensions
* Surrogate Keys
* Data Validation
* Incremental-safe Loads

---

# 👨‍💻 Author

**Helly Patel**
Data Engineering Project – FinWealth Advisors Wealth Analytics Platform

---

# 📌 Future Improvements

* Incremental Fact Loading
* SCD Type 2 Implementation
* CI/CD Deployment Pipelines
* Azure Synapse Integration
* Real-time Streaming Support
* Monitoring Dashboards

---

# ⭐ Repository Purpose

This repository showcases practical implementation skills in:

* Azure Data Engineering
* ETL Development
* Data Warehousing
* SQL Optimization
* ADF Data Flows
* Analytics Engineering

---

# 📄 License

This project is for academic and portfolio purposes.
