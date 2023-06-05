---
title: "Data Warehousing"
---
On Azure, large-scale `data ingestion` is best implemented by creating `pipelines` that orchestrate `ETL` (*extract, transform, load*) processes.

These pipelines can be created using `Azure Data Factory` or by using the same pipeline engine in `Azure Synapse Analytics`.

Pipelines consists of one or more `activities`. An input dataset provides the source data, and activities can be defined as a data flow that incrementally manipulates the data until an output dataset is produced.

Pipelines use `linked services` to load and process data. For example, you might use an Azure Blob Storage linked service to ingest the input dataset, then use the Azure SQL Database service to run a stored procedure, before running a task on Azure Databricks or Azure HDInsight. Finally, you can save the output dataset in a linked service such as Azure Synapse Analytics.

The following image is a visual representation of the process mentioned above (not entirely one-to-one):

![](https://docs.microsoft.com/ro-ro/learn/wwl-data-ai/examine-components-of-modern-data-warehouse/media/pipeline.png)

---

There are two common types of analytical data store: `Data Warehouses` and `Data Lakes`.

A data warehouse is a `relational database` in which the data is stored in a schema that is optimized for data analytics rather than transactional workloads.

A data lake is a `file store`, usually on a distributed file system for high performance data access. Technologies like `Spark` or `Hadoop` are often used to process queries on the stored files and return data for reporting and analytics.

You can also use a `hybrid approach` that combines the feature of data lakes and data warehouses in a `lake database` or `data lakehouse`.

---

On Azure, there are three main services that you can use to implement a large-scale analytical store:
- Azure Synapse Analytics => includes Apache Spark
- Azure Databricks
- Azure HDInsight

### Star Schema
A `star schema` is a database organizational structure optimized for use in a data warehouse or business intelligence that uses a single large `fact table` to store transactional or measured data, and one or more smalled `dimensional tables` that store attributes about the data.

It is called a `star schema` because the fact table sits at the center of the logical diagram, and the small dimensional tables branch off to form the points of the star.

A `fact table` is the central table is a star schema of a data warehouse, and is used to store quantitive information.

`Dimensional tables` store supporting information about the `fact table`. Each star schema database has at least one dimension table, but will often have many. Each dimension table will relate to a `column` in the fact table with a dimension value, and will store additional information about that value.

Star schema's dimension tables do not contain any foreign keys. 

![](https://cdn.ttgtmedia.com/rms/onlineimages/dm-star_schema-f.png)

### Snowflake Schema
A `snowflake schema` is similar to a star schema in that it has a single fact table and many dimensional tables. However, for a snowflake schema, each dimension table might have foreign keys that relate to other dimension tables.

![](https://cdn.ttgtmedia.com/rms/onlineimages/dm-snowflake_schema-f.png)

