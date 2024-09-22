# Kafka Data Pipeline Project

## Overview

This project demonstrates the integration of Apache Kafka with AWS services, including EC2, S3, Glue, and Athena, to create a real-time data pipeline. The pipeline collects data from producers, processes it using Kafka, stores it in S3, and makes it queryable via Athena.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Project](#running-the-project)
- [Data Flow](#data-flow)
- [AWS Glue and Athena Integration](#aws-glue-and-athena-integration)
- [Troubleshooting](#troubleshooting)
- [Conclusion](#conclusion)

## Prerequisites

- AWS Account
- AWS CLI installed and configured
- Java installed on the EC2 instance
- Python installed on your local machine with the following packages:
  - `pandas`
  - `kafka-python`
  - `boto3` (for AWS S3 integration)

## Setup

1. **Create an EC2 Instance on AWS**
   - Launch an EC2 instance with appropriate security group settings to allow inbound traffic on the required ports (default Kafka ports).

2. **Install Apache Kafka**
   - Connect to your EC2 instance via SSH.
   - Download Kafka:
     ```bash
     wget https://downloads.apache.org/kafka/3.8.0/kafka_2.12-3.8.0.tgz
     ```
   - Decompress the Kafka tarball:
     ```bash
     tar -xvf kafka_2.12-3.8.0.tgz
     ```

3. **Install Java**
   - Ensure Java is installed on your EC2 instance.

4. **Start Zookeeper and Kafka**
   - Open two terminal windows:
     - In the first terminal, navigate to the Kafka directory and start Zookeeper:
       ```bash
       bin/zookeeper-server-start.sh config/zookeeper.properties
       ```
     - In the second terminal, start Kafka:
       ```bash
       bin/kafka-server-start.sh config/server.properties
       ```

5. **Configure Kafka for Public Access**
   - Update the Kafka server configuration to allow connections via your EC2 instance's public IP address.

6. **Create Topics, Producers, and Consumers**
   - Use a third terminal to create Kafka topics and run producer and consumer scripts.

## Running the Project

1. **Producer and Consumer Setup**
   - Write a producer script in Python that sends data to the Kafka topic. Use `pandas` to read a dataset and convert it into JSON format.
   - Write a consumer script that reads messages from the Kafka topic and saves the data to an S3 bucket.

2. **AWS S3 Integration**
   - Create an S3 bucket in your AWS account.
   - Modify the consumer code to save received data into the S3 bucket.

## Data Flow

1. **Data Ingestion**: The producer sends data to Kafka.
2. **Real-time Processing**: The Kafka consumer processes data and saves it to S3.
3. **Data Storage**: The data is stored in S3 as JSON files.
4. **Data Querying**: Use AWS Glue to crawl the data and create a schema, then query it with AWS Athena.

## AWS Glue and Athena Integration

1. **Set Up AWS Glue**
   - Create a new IAM role for AWS Glue with access to the S3 bucket.
   - Configure the Glue Crawler with the S3 bucket as the data source and create a new database.
  
2. **Query with Athena**
   - Once the crawler finishes running, preview the table in Athena and execute SQL queries to analyze the data.

## Troubleshooting

- If the Kafka server stops, restart both Zookeeper and Kafka.
- Ensure the security group settings on your EC2 instance allow inbound traffic for Kafka.
- Check IAM permissions for AWS Glue and S3 access.

## Conclusion

This project showcases the ability to create a scalable, real-time data processing pipeline using Apache Kafka and AWS services. By leveraging these technologies, you can efficiently handle large volumes of data and query it in real-time.

## License

This project is licensed under the MIT License.
