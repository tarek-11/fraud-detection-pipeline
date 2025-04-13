# 🚨 Real-Time & Batch Fraud Detection Pipeline

This project implements a scalable data pipeline to detect fraudulent financial transactions in real-time and analyze fraud trends using batch processing. It leverages Apache Kafka, Apache Spark, Airflow, Hadoop HDFS, and Trino to provide both instant fraud alerts and deep fraud investigations.

## 🔍 Overview

Fraud detection requires intelligent systems that not only catch fraud as it happens but also find hidden fraud patterns over time. This project simulates real-time transaction data using Kafka, processes it using Spark Streaming with custom fraud detection rules, stores the data in HDFS, and uses Trino and batch jobs (via Airflow + Spark) for historical analysis and reporting.

## 🏗️ Architecture

```plaintext
+-------------------+    +-------------------------+
| Banking Systems   |    | User Behavior Simulation|
| (Transaction Flow)|    | (Kafka Producer)        |
+-------------------+    +-------------------------+
           |                          |
           v                          v
      +-------------+        +------------------+
      |    Kafka    | <------| Real-time Stream |
      +-------------+        +------------------+
           |
           v
+------------------------------+
| Spark Structured Streaming   |
| - Rule-based fraud detection |
+------------------------------+
           |
           +---------------------> Kafka Topic: fraud-alerts
           |
           v
+------------------------+
| Hadoop HDFS Storage    |
| - Raw & processed data |
+------------------------+
           |
           v
     +--------------------+
     |   Spark Batch Jobs |
     |   (via Airflow)    |
     +--------------------+
           |
           v
     +-----------+
     |   Trino   |
     | (SQL over |
     |   HDFS)   |
     +-----------+
           |
           v
     +----------------+
     | BI Dashboards  |
     |   & Analysts   |
     +----------------+
