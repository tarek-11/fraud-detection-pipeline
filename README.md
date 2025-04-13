# Real-Time & Batch Fraud Detection Pipeline

This project implements a scalable data pipeline to detect fraudulent financial transactions in real-time and analyze fraud trends using batch processing. It leverages Apache Kafka, Apache Spark, Airflow, Hadoop HDFS, and Trino to provide both instant fraud alerts and deep fraud investigations.

## Overview

Fraud detection requires intelligent systems that not only catch fraud as it happens but also find hidden fraud patterns over time. This project simulates real-time transaction data using Kafka, processes it using Spark Streaming with custom fraud detection rules, stores the data in HDFS, and uses Trino and batch jobs (via Airflow + Spark) for historical analysis and reporting.

## Features

- Real-time fraud detection using Spark Streaming
- Rule-based detection logic (e.g., high amount, location mismatch)
- Fraud alerts via Kafka topic
- Long-term fraud pattern analysis via Spark Batch
- Transaction storage in Hadoop HDFS
- SQL-based investigation with Trino
- Ready for ML model integration

  ### Prerequisites

- Java 8+
- Python 3.8+
- Apache Kafka
- Apache Spark
- Apache Hadoop
- Airflow
- Trino

### Installation Steps

1. **Start Kafka**

   ```bash
   # Start Zookeeper
   bin/zookeeper-server-start.sh config/zookeeper.properties

   # Start Kafka
   bin/kafka-server-start.sh config/server.properties

   # Create topics
   bin/kafka-topics.sh --create --topic transactions --bootstrap-server localhost:9092
   bin/kafka-topics.sh --create --topic fraud-alerts --bootstrap-server localhost:9092

## Architecture

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

