# 🏗️ Modern Data Warehouse & Sales Analytics Project

> An end-to-end data engineering and business intelligence solution built with **SQL Server**, **Power BI**, and the **Medallion Architecture** — transforming raw sales data into actionable insights.

---

## 📌 Project Overview

This project demonstrates a complete data pipeline — from raw CSV ingestion to interactive Power BI dashboards. It covers data architecture, ETL engineering, dimensional modeling, and analytics, making it a comprehensive portfolio piece for data professionals.

---

## 📂 Project Structure

```
📦 Data Warehouse Project
├── 📁 data/
│   └── sales_details_.csv          # Source data (60,398 records | 2011–2013)
├── 📁 sql/
│   ├── bronze/                     # Raw ingestion scripts
│   ├── silver/                     # Cleansing & transformation scripts
│   └── gold/                       # Star schema — fact & dimension tables
├── 📁 reports/
│   └── sales_analytics.pbix        # Power BI dashboard
└── README.md
```

---

## 🗂️ Dataset — `sales_details_.csv`

| Field | Description |
|---|---|
| `order_number` | Unique sales order identifier |
| `order_date` | Transaction date (2011–2013) |
| `sales_amount` | Revenue per line item |
| `price` | Unit price |
| `quantity` | Units sold |
| `first_name / last_name` | Customer name fields |
| `Gender` | Customer gender |
| `Country` | Sales region |
| `product_name` | Product description |
| `category` | Top-level category (Bikes, Clothing, Accessories) |
| `sub_category` | Product sub-category (17 types) |
| `product_cost` | Cost of goods sold |
| `Customer_Full_Name` | Full customer name |
| `Total_Cost` | Aggregated cost per customer |

### 📊 Dataset Summary
- **Total Records:** 60,398 rows
- **Date Range:** January 2011 – September 2013
- **Total Sales Revenue:** $29,356,250
- **Unique Orders:** 27,659
- **Unique Customers:** 18,399
- **Countries:** Australia, United States, Canada, United Kingdom, France, Germany
- **Categories:** Bikes · Clothing · Accessories
- **Sub-Categories:** 17 (Jerseys, Helmets, Road Bikes, Mountain Bikes, Touring Bikes, and more)

---

## 🏛️ Data Architecture — Medallion Layers

```
CSV Source Files
      │
      ▼
┌─────────────┐
│ 🥉 BRONZE   │  Raw ingestion — data stored as-is, no transformation
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ 🥈 SILVER   │  Cleansing · Standardization · Deduplication · Normalization
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ 🥇 GOLD     │  Star Schema · Fact Tables · Dimension Tables · BI-Ready
└──────┬──────┘
       │
       ▼
  Power BI Dashboard
```

### 🥉 Bronze Layer — Raw Ingestion
- Loads CSV data directly into SQL Server with no modifications
- Preserves original source data for full auditability and lineage
- Captures load timestamps and source file metadata

### 🥈 Silver Layer — Cleansing & Standardization
- Handles null values, duplicates, and data type corrections
- Standardizes date formats, text casing, and country names
- Applies business validation rules and flags anomalies

### 🥇 Gold Layer — Star Schema
- **Fact Table:** `fact_sales` — order transactions with measures (sales amount, quantity, cost)
- **Dimension Tables:** `dim_customer`, `dim_product`, `dim_date`, `dim_geography`
- Optimized with indexes and partitioning for analytical query performance

---

## ⚙️ ETL Pipeline

| Stage | Description |
|---|---|
| **Extract** | Reads CSV flat files and bulk-loads into Bronze layer |
| **Transform** | Applies cleansing, standardization, and business rules (Silver) |
| **Load** | Populates star schema fact and dimension tables (Gold) |

**Pipeline Design Principles:**
- ✅ **Idempotent** — safe to re-run without producing duplicates
- ✅ **Modular** — each layer is independently executable
- ✅ **Observable** — row counts and error logs captured per run
- ✅ **Auditable** — full lineage from source CSV to Gold layer

---

## 📊 Power BI Dashboard — Sales Analytics

**File:** `sales_analytics.pbix`  
**Pages:** 1 (Sales Overview)  
**Visuals:** 25 components

### Dashboard Components

| Visual | Description |
|---|---|
| 📦 **KPI Cards (×4)** | High-level metrics — Total Revenue, Orders, Customers, Quantity |
| 📊 **Revenue by Country** | Clustered column chart — regional performance comparison |
| 🍩 **Revenue by Category** | Donut chart — Bikes vs Clothing vs Accessories breakdown |
| 📈 **Sales by Month** | Line chart — monthly revenue trend over time |
| 🌳 **Revenue by Sub-Category** | Treemap — granular product category performance |
| 🔽 **Slicers (×4)** | Interactive filters — Date, Country, Category, Sub-Category |

### Key Business Insights Enabled
- Period-over-period sales trend analysis (2011–2013)
- Country-level revenue performance across 6 markets
- Product category and sub-category profitability breakdown
- Customer-level sales aggregation and segmentation

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| **Database Engine** | Microsoft SQL Server (T-SQL) |
| **Architecture Pattern** | Medallion Architecture — Bronze / Silver / Gold |
| **ETL Development** | T-SQL Stored Procedures, SSIS |
| **Data Ingestion** | CSV flat-file bulk load |
| **Data Modeling** | Star Schema — Fact & Dimension Tables |
| **BI & Reporting** | Power BI Desktop (`.pbix`) |
| **Custom Visuals** | Power KPI (powerKPI) |
| **Version Control** | Git |

---



## 🎯 Skills Demonstrated

| Skill | Details |
|---|---|
| **SQL Development** | T-SQL queries, stored procedures, performance tuning |
| **Data Architecture** | Medallion pattern, layer design, schema governance |
| **Data Engineering** | Pipeline design, ingestion, transformation workflows |
| **ETL Development** | Source-to-target mapping, scheduling, error handling |
| **Data Modeling** | Star schema, SCD Type 2, surrogate keys, indexing |
| **Data Analytics** | KPI reporting, trend analysis, BI dashboard design |
| **Power BI** | Data modeling, DAX measures, interactive dashboards |

---

## 📁 Data Dictionary

<details>
<summary>Click to expand full column definitions</summary>

| Column | Type | Layer | Description |
|---|---|---|---|
| order_number | VARCHAR | Bronze → Gold | Unique sales order ID |
| order_date | DATE | Bronze → Gold | Transaction date |
| sales_amount | INT | Bronze → Gold | Revenue per line |
| price | INT | Bronze → Gold | Unit selling price |
| quantity | INT | Bronze → Gold | Units sold per line |
| first_name | VARCHAR | Bronze → Silver | Customer first name |
| last_name | VARCHAR | Bronze → Silver | Customer last name |
| Gender | VARCHAR | Bronze → Silver | Customer gender |
| Country | VARCHAR | Bronze → Gold | Sales country/region |
| product_name | VARCHAR | Bronze → Gold | Full product name |
| category | VARCHAR | Bronze → Gold | Top-level product category |
| sub_category | VARCHAR | Bronze → Gold | Product sub-category |
| product_cost | INT | Bronze → Gold | Cost of goods sold |
| Customer_Full_Name | VARCHAR | Silver → Gold | Derived full name |
| Total_Cost | INT | Silver → Gold | Aggregated customer cost |

</details>

---

## 📬 Contact & Contributions

Feel free to fork this repository, raise issues, or submit pull requests.  
This project is open for collaboration and learning purposes.

> 💡 *Follow the data journey — from a raw CSV file to a fully interactive business intelligence dashboard.*
