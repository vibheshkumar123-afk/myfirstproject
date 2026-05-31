## 1. Architectural Overview

The pipeline processes raw data incrementally through three distinct logical layers using **Delta Live Tables (DLT)** or **Spark Declarative Pipelines**.


[ Raw Cloud Storage ] ──(Auto Loader)──> [ Bronze Layer ] ──> [ Silver Layer ] ──> [ Gold Layer ] ──> [ BI & Analytics ]
   (S3 / ADLS / GCS)        (Raw Append)        (Clean / Type 2)      (Aggregations)      (Dashboards / ML)


- **Ingestion Layer:**  
  High-velocity data land in cloud storage (e.g., AWS S3 or Azure ADLS Gen2).

- **Bronze Layer (Raw Storage):**  
  Append-only ingestion retaining full historical fidelity.

- **Silver Layer (Enriched & Cleansed):**  
  Deduplicated, schema-validated, and transformed operational data.

- **Gold Layer (Business Level):**  
  Aggregated, business-level metrics optimized for consumption.