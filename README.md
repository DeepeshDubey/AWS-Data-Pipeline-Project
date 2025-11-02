# 📂 AWS-Data-Pipeline-Project

This project demonstrates a simple, yet effective, **Serverless Data Analytics Pipeline** using core AWS services. The goal is to ingest raw data (CSV), prepare it for querying, and finally visualize the insights.

<img width="452" height="314" alt="image" src="https://github.com/user-attachments/assets/defdbf5c-0096-4692-802f-c387fbb1a11b" />

---

## 💡 Project Overview

The pipeline takes raw data files stored in **Amazon S3**, uses **AWS Glue Crawler** to automatically infer the schema, and registers the metadata in the **AWS Glue Data Catalog**. This data is then queried using **Amazon Athena** (standard SQL) and ultimately connected to **Amazon QuickSight** for dynamic and interactive business intelligence (BI) dashboards.

---

## 🛠️ Services Used

| Service | Category | Function in Project |
| :--- | :--- | :--- |
| **Amazon S3** | Storage | Secure, scalable storage for the raw CSV data. |
| **AWS Glue Crawler** | ETL/Catalog | Automatically scans S3 data, infers schema, and creates metadata tables in the Data Catalog. |
| **Amazon Athena** | Analytics | Serverless, interactive query service to analyze data in S3 using standard SQL. |
| **Amazon QuickSight** | Visualization | Cloud-native BI service for creating dashboards and reports from the Athena query results. |

---

## 🪜 Step-by-Step Process

1.  **Data Ingestion (S3):** Raw **CSV files** containing the dataset were uploaded to a specific S3 bucket path (e.g., `s3://my-data-pipeline-bucket/raw-data/`).
2.  **Schema Definition (Glue Crawler):** An **AWS Glue Crawler** was configured to point to the S3 data location. The crawler was run to automatically detect the schema (column names and data types).
3.  **Metadata Registration (Data Catalog):** The crawler's output was registered as a new table in the **AWS Glue Data Catalog**, making it available for querying.
4.  **Data Querying (Athena):** **Amazon Athena** was used to run standard SQL queries (e.g., `SELECT COUNT(*), AVG(column_x) FROM my_database.my_table;`) against the table defined in the Data Catalog.
5.  **Visualization (QuickSight):** The Athena data source was connected to **Amazon QuickSight**. SPICE (Super-fast, Parallel, In-memory Calculation Engine) was utilized for fast data import, and a dashboard was created to visualize key metrics.

---

## 🎨 Architecture Diagram (Recommended)

A simple architecture diagram is highly recommended for GitHub projects as it visually explains the process instantly.

**Suggested Image:**

You should include an image that shows a logical flow:

**S3 Bucket** $\rightarrow$ **Glue Crawler** (to **Data Catalog**) $\rightarrow$ **Athena** $\rightarrow$ **QuickSight** Dashboard.



---

## 📝 Example Query

An example query run in Athena against the raw dataset:

```sql
SELECT
    product_category,
    SUM(sale_amount) AS total_sales
FROM
    "my_database"."my_table"
GROUP BY
    product_category
ORDER BY
    total_sales DESC;
