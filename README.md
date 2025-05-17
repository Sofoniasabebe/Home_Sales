# 🏡 Home Sales Analysis with PySpark

## 📘 Overview

This challenge demonstrates how to use **PySpark** in a distributed environment to analyze real estate sales data. The data is loaded from an AWS S3 bucket, processed with Spark SQL, and partitioned for efficient querying. 

## 🛠️ Setup

1. **Installed Java and Spark** in Colab. 
2. **Started a SparkSession** using PySpark.
3. **Loaded data from S3** into a Spark DataFrame.
4. **Created SQL views** and run Spark SQL queries.
5. **Wrote Parquet partitioned by `date_built`**.
6. **Read and queried partitioned Parquet files**.

## 📈 Queries Performed

- Average price of 4-bedroom homes sold per year
- Average price of 3-bed, 3-bath homes by year built
- Price trends for homes with 3 bed, 3 bath, 2 floors, and 2000+ sqft
- Average price per view rating (filtered by price ≥ $350,000)
- Caching and uncaching temporary tables
- Partitioning and re-reading from Parquet format

## ⏱️ Query Runtime Comparison

To measure the performance impact of caching and Parquet storage, the same query was executed under three conditions and the results are as follows:

| Execution Mode | Data Source             | Runtime (seconds) |
|----------------|-------------------------|--------------------|
| Original       | Uncached `home_sales`   | **0.7251**         |
| Cached         | Cached `home_sales`     | **0.4224**         |
| Parquet        | `parquet_home_sales`    | **0.8997**         |

✅ Caching provided a noticeable performance boost — reducing runtime by ~42% compared to the original.

📉 Reading from Parquet was slower than cached memory access, but still reasonably fast considering it has to load from disk, parse the files, and reconstruct the DataFrame.

