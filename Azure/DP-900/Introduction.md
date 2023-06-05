---
title: "Introduction to the world of Data"
---
#### Date: 13.06.2022
Data can be classified as `structured`, `semi-structured` or `unstructured`.

Structured data adheres to a common schema, so all of the data has the same fields or properties. Most commonly, the schema for structured entities is tabular. Example: SQL Databases

Semi-structured data is information that has some structure, but which allows for some variation between entity instances. Example: JSON objects.

Unstructured data is represented by things such as documents, images, audio, video data, binary files etc.

Usually, all of this data is stored in one of two broad categories:
- File stores
- Databases

Transctional systems are often high-volume, handling many millions of transactions in a single day. The work performed by transactional systems if often reffered to as `Online Transactional Processing (OLTP)`.

`OLTP` systems enforce transctions that support so-called `ACID` semantics:
- Atomicity
- Consistency
- Isolation
- Durability

Analytical data processing typically uses read-only systems that store vast volumes of historical data or business metrics.

A common architecture for data processing on an enterprise-scale could look like this:

![Example Image](https://docs.microsoft.com/en-us/learn/wwl-data-ai/explore-core-data-concepts/media/analytical-processing.png)

1. Data files may be stored in a central `data lake` for analysis.
2. An extraction, transform and load (`ETL`) process copies data from files and `OLTP` databases into a `data warehouse` that is optimized for read activity.
3. Data in the `data warehouse` may be aggregated and loaded into an online analytical processing `OLAP` model, or cube.
4. The data in the `data lake`, `data warehouse`, and analytical model can be queried to produce reports, visualizations, and dashboards.

`Data lakes` are common in modern data analytical processing scenarios, where a large volume of file-based data must be collected and analyzed.

`Data warehouses` are an established way to store data in a relational schema that is optimized for read operations - primarily queries to support reporting and data visualization.

An `OLAP` model is an aggregated type of data storage that is optimized for analytical workloads.

---

There are three key job roles in the world of data:
- `Database administrators`
- `Data engineers`
- `Data analysts`

---
There are many services out there used for modern transactional and analytical solutions. Some of them are:
- Azure SQL
- Azure CosmosDB
- Azure Storage
- Azure Data Factory
- Azure Synapse Analytics
- Azure Databricks
- Azure HDInsight
- Azure Stream Analytics
- Azure Data Explorer
- Microsoft Purview#
- Microsoft Power BI