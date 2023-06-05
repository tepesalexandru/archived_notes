---
title: "Real-Time Analytics"
---

There are two general ways to process data:
- `Batch processing` - data records are collected and stored before being processed together in a single operation
- `Stream processing` - source of data is constantly monitored and processed in real time as new data events occur

---

At its simplest, a high-level architecture for stream processing looks like this:
1. An event generates some data.
2. The generated data is captured in a streaming `source` for processing.
3. The event data is processed.
4. The results of the stream processing operation are written to an output (or `sink`)

Microsoft Azure supports multiple technologies that you can use to implement real-time analytics of streaming data, including:
- Azure Stream Analytics
- Spark Structured Streaming
- Azure Data Explorer

---

Common `sources` for stream processing are:
- Azure Event Hubs
- Azure IoT Hub
- Azure Data Lake Store Gen 2
- Apache Kafka

Common `sinks` for stream processing are:
- Azure Event Hubs
- Azure Data Lake Store Gen 2
- Azure SQL Database / Azure Synapse Analytics / Azure Databricks
- Microsoft Power BI

---

`Azure Stream Analytics` is a service for complex event processing and analysis of streaming data. It is used to:
- Ingest data from an `input`
- Process the data by using a `query` to select, project, and aggragated data values
- Write the results to an `output`.

Here is a visualization of the above process:

![](https://docs.microsoft.com/ro-ro/learn/wwl-data-ai/explore-fundamentals-stream-processing/media/stream-analytics.png)

Once started, a Stream Analytics query will run perpetually, processing new data as it arrives in the input and storing the results in the output.

The easiest way to use Azure Stream Analytics is to create a Stream Analytics `job` in an Azure Subscription, configure its input(s) and output(s) and fine the query that the job will use to process the data in SQL format.

---

`Apache Stark` is a distributed processing framework for large scale data analytics. You can use Spark on Microsoft Azure in the following services:
- Azure Synapse Analytics
- Azure Databricks
- Azure HDInsight

To process streaming data on Spark, you can use the `Spark Structured Streaming` library, which provides an API for ingesting, processing, and outputting results from perpetual streams of data.

Spark Structured Streaming is build on a common structure in Spark called a `dataframe`, which encapsulated a table of data.

`Delta Lake` is an open-source storage layer that adds support for transactional consistency, schema enforcement, and other common data warehousing feature to data lake storage.

---

`Azure Data Explorer` is a standalone Azure service for efficiently analyzing data. You can use the service as the output for large volumes of diverse data sources such as websites, applications, IoT devices, and more.

To query Data Explorer Tables, you can use the `Kusto Query Language` (KQL), a language that is specifically optimized for fast read performance - particularly with telemetry data that includes a timestamp attribute.

---

Two common characteristics of real-time data processing are:
- Data is processed as it is created
- Low latency is expected