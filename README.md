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


## 🌟 Features

- **Real-time fraud detection** using Spark Streaming  
- **Rule-based detection logic** (e.g., high amount, location mismatch)  
- **Fraud alerts** sent via a Kafka topic  
- **Long-term fraud pattern analysis** via Spark Batch  
- **Transaction storage** in Hadoop HDFS  
- **SQL-based investigation** with Trino  
- **ML model integration readiness**

---

## ⚙️ Tech Stack

| **Component**   | **Technology**         |
| --------------- | ---------------------- |
| Messaging       | Apache Kafka           |
| Real-time       | PySpark Streaming      |
| Batch           | Spark + Airflow        |
| Storage         | Hadoop HDFS            |
| Query Engine    | Trino (PrestoSQL)      |
| ML (Optional)   | Python, scikit-learn   |
| Dashboards      | Power BI / Grafana     |

---

## 📁 Project Structure

```plaintext
fraud-detection-pipeline/
├── kafka/
│   └── producer_simulator.py
├── spark/
│   ├── real_time_detector.py
│   └── batch_analysis.py
├── airflow/
│   └── fraud_analysis_dag.py
├── hdfs/
├── trino/
│   └── fraud_queries.sql
├── ml/
│   ├── train_model.py
│   └── fraud_api.py
└── README.md
