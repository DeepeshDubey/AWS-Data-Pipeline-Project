# 📂 AWS-Data-Pipeline-Project

This project demonstrates a simple, yet effective, **Serverless Data Analytics Pipeline** using core AWS services. The goal is to ingest raw data (CSV) sourced from **Kaggle**, prepare it for querying, and finally visualize the insights.

<img width="443" height="164" alt="image" src="https://github.com/user-attachments/assets/51f08de9-e502-4f04-a05d-25fe74bedc44" />


---

## 💡 Project Overview

The pipeline takes raw data files (downloaded from **Kaggle**) stored in **Amazon S3**, uses **AWS Glue Crawler** to automatically infer the schema, and registers the metadata in the **AWS Glue Data Catalog**. This data is then queried using **Amazon Athena** (standard SQL) and ultimately connected to **Amazon QuickSight** for dynamic and interactive business intelligence (BI) dashboards.

---

## 💾 Dataset Source

* **Source:** The raw data (**CSV files**) used for this analysis was downloaded from **Kaggle**.
* **Recommendation:** (If known, add the dataset name here, e.g., "We used the 'Global Superstore Sales' dataset.")

---

## 🛠️ Services Used

| Service | Category | Function in Project |
| :--- | :--- | :--- |
| **Amazon S3** | Storage | Secure, scalable storage for the raw CSV data. |
| **AWS Glue Crawler** | ETL/Catalog | Automatically scans S3 data, infers schema, and creates metadata tables in the **Data Catalog**. |
| **Amazon Athena** | Analytics | Serverless, interactive query service to analyze data in S3 using standard SQL. |
| **Amazon QuickSight** | Visualization | Cloud-native BI service for creating dashboards and reports from the Athena query results. |

---

## 🪜 Step-by-Step Process

1.  **Data Acquisition & Ingestion (Kaggle $\rightarrow$ S3):**
    * The raw data was downloaded (usually as CSV) from **Kaggle**.
    * These files were then uploaded to a specific S3 bucket path (e.g., `s3://my-data-pipeline-bucket/raw-data/`).
2.  **Schema Definition (Glue Crawler):** An **AWS Glue Crawler** was configured to point to the S3 data location. The crawler was run to automatically detect the schema (column names and data types).
3.  **Metadata Registration (Data Catalog):** The crawler's output was registered as a new table in the **AWS Glue Data Catalog**.
4.  **Data Querying (Athena):** **Amazon Athena** was used to run standard SQL queries against the table defined in the Data Catalog.
5.  **Visualization (QuickSight):** The Athena data source was connected to **Amazon QuickSight** to build dashboards and reports.

---

## 🎨 Architecture Diagram

This diagram visualizes the flow, from the raw source to the final dashboard:



---

## 📝 Example Query

An example query run in Athena against the raw dataset to find total sales by product category:

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
