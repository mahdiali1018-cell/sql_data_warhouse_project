
🏗️ Modern Data Warehouse Project

A production-style data warehouse built with SQL Server, structured around the Medallion Architecture (Bronze, Silver, Gold).
Designed to demonstrate end-to-end data engineering — from raw CSV ingestion to business-ready analytics and reporting.


📐 Architecture Overview
This project follows the Medallion Architecture pattern, a layered approach that progressively refines raw data into trusted, analytics-ready assets.
Each layer has a distinct responsibility, ensuring clear separation of concerns and full data lineage from source to consumption.
🥉 Bronze Layer — Raw Ingestion

Stores raw, unmodified data exactly as received from CSV source files.
Acts as a historical archive with no transformations applied.
Ensures full auditability and traceability back to the original source.

🥈 Silver Layer — Cleansing & Standardization

Applies data cleansing, deduplication, and null handling.
Standardizes data types, formats, and naming conventions.
Normalizes records into a consistent schema ready for modeling.

🥇 Gold Layer — Business-Ready Data

Models cleansed data into a Star Schema (fact + dimension tables).
Optimized for high-performance analytical queries and aggregations.
Powers dashboards, reports, and self-service BI tools.


⚙️ ETL Pipelines

Extract — Reads structured CSV files and stages them in the Bronze layer.
Transform — Applies business rules, type coercions, and validation logic across layers.
Load — Materializes clean, enriched records into Gold layer star schema tables.
Pipelines are idempotent, modular, and emit structured logs for full observability.


🛠️ Tech Stack
ComponentTechnologyDatabase EngineMicrosoft SQL Server (T-SQL)ETL DevelopmentT-SQL Stored Procedures, SSISData ModelingStar Schema — Fact & Dimension TablesData IngestionCSV Flat-File Bulk LoadReportingPower BI / Tableau / SSRS ReadyVersion ControlGit

🎯 Skills Demonstrated
SQL Development Data Architecture ETL Engineering Data Modeling Data Analytics
Dimensional Modeling Star Schema Design Pipeline Observability BI Reporting
