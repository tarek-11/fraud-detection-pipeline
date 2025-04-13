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


## Fraud Detection Rules

| Rule Type     | Description               | Threshold       |
|---------------|---------------------------|-----------------|
| Amount        | High-value transaction    | > $5,000        |
| Frequency     | Multiple transactions     | 5+ in 10 min    |
| Location      | Geographic dispersion     | 2+ countries in 30 min |
| New Account   | First large purchase      | > $1,000        |
| Chargebacks   | Multiple refunds          | 3+ in 7 days    |

## ML Integration (Optional)

- Historical fraud data training
- Real-time prediction API
- Model scoring in Spark
- Continuous model updates

## Future Enhancements

- Deploy ML-based fraud classifier
- Add Docker containerization
- Implement real-time dashboards
- Add geolocation-based rules
- Enhance API security

## Author

Built with ❤️ by [Mohamed Tarek]
- GitHub: [https://github.com/tarek-11]
- LinkedIn: [(https://www.linkedin.com/in/tarek11/]

