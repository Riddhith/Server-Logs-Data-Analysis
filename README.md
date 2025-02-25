# Server-Logs-Data-Analysis for Anomaly Detection

Prerequisites:
You should have Apache Hadoop,Apache Hive,My SQL,Apache Spark(Pyspark) installed in the system.

Objective
The goal of this project was to analyze network traffic logs, detect potential security threats (such as port scanning and failed requests), and generate meaningful insights using Hive for data storage and Spark for processing and visualization.

Now lets dive into the project.
Understanding the dataset is very crucial in this project.Observe the data, its columns and datatypes very carefully.

Step-1
(Data Ingestion into HDFS): Download the dataset from Kaggle and extract the CSV file.Move the data to HDFS. 

Step-2
(Create a table in Hive in accordance with the dataset and load the data from the HDFS location to Hive)
Open Hive and create an external table to query logs efficiently and query the data to verify ingestion.

Step-3
(Data Processing, Cleaning and Transformation using Spark Batch)
1. Handle NULL values in packets, flows, and tos columns.
2. Convert necessary data types (e.g., bytes and duration to numerical types).
3. Create a cleaned table.

Step-4
Performing basic Exploratory Data Analysis(EDA) using Hive and Spark SQL
1. Check for Anomalies & Attack Distribution
2. Identify Suspicious Network Traffic
3. Find High Traffic Sources

Step-5
Load Data into Spark for Advanced Analysis
1. Load Hive Table into Spark DataFrame
2. Convert bytes Column to Numeric Format
3. Detect Anomalous Traffic Using Statistics
4. Find the Top Suspicious IPs

Step-6
Did some Data Visualization on the processes data.

Results & Insights

Key Findings

1. Heavy Traffic Sources
Some IPs transmitted >1GB of data, possibly indicating data exfiltration or high-traffic services.

2. Protocol Usage
87% TCP traffic confirms it as the primary protocol.
1.5% ICMP traffic is worth monitoring for potential ping sweeps or network scanning.
   
3. Port Scanning Detection
2-3 IPs scanned >150 unique ports, suggesting active reconnaissance.
Follow-up: Check if these IPs belong to internal users or potential attackers.

4. Failed Requests & Possible Attacks
2 IPs had >8,000 failed requests, possibly indicating brute-force attacks.
High 403 errors could signal unauthorized access attempts.

Conclusion & Next Steps

Summary of Anomalies Detected
3 potential port scanning IPs (scanning >50 ports).
2 potential brute-force attack IPs (>500 failed requests).
5 heavy traffic IPs (sending >500MB each).

Next Steps
Security Team Investigation: Verify flagged IPs.
Machine Learning for Threat Detection: Train a model to classify normal vs. anomalous logs.
Deploy Real-Time Monitoring: Stream logs and alert security analysts in real-time.

Final Thoughts:
This project successfully identified high-risk behaviors using Hive & Spark. By automating detection and integrating with security tools, this analysis can significantly enhance threat detection in real-world systems.
