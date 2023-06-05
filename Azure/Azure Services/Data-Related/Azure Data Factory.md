---
title: "Azure Data Factory"
---
Azure Data Factory is a managed cloud service that's built for complex hybrid [[ETL (Extract, Transform, Load)]], ELT and data integration projects.

![](https://docs.microsoft.com/en-us/azure/data-factory/media/introduction/data-factory-visual-guide.png)

## Top Level Concepts
An Azure Subscription might have one or more Azure Data Factory instances (or data factories). Azure Data Factory is composed of the components below:
- Pipelines
- Activities
- Datasets
- Linked services
- Data flows
- Integration Runtimes

These components work together to provide the platform on which you can compose data-driven workflows with steps to move and transform data.

### Pipelines
A `pipeline` is a logical grouping of `activities` that perform one unit of work.

A data factory might have one or more pipelines. Together, the activities in a pipeline perform a task. The activities in a pipeline can be chained together to operate sequentially, or they can operate independently in parallel.

As an example, a pipeline can contain a group of activities that ingest data from an Azure Blob, and then runs a Hive query on an HDInsight cluster to partition the data.

### Activities
Activities represent a processing step in a pipeline.

Data Factory supports three types of activities:
- data movement activities
- data transformation activities
- control activities

### Datasets
Datasets represent data structures within the data stores, which simply point to or reference the data you want to use in your activities as inputs or outputs.

### Linked Services
Linked Services are much like connection strings, which define the connection information that's needed for Data Factory to connect to external resources.

---

### Triggers
A trigger initiates the execution of a pipeline. There are different types of triggers for different types of events.

Example: Scheduling a pipeline

---

Azure Data Factory is easy to use. There are over 90+ built-in connectors.

---


#### Simple Guide to CICD for Azure Data Factory
Azure Data Factory is a serverless and no-code service for ETL Pipeline in Azure Cloud. By publishing changes in a Data Factorym the code is converted to Azure Resource Manager Templates (ARM) in a special publishing branch as IaaS.

The Data Factory resources should be deployed beforehand in each environment, using tools such as Terraform.

#### Monitoring Azure Data Factory Pipeline
If you want to see the status of your pipeline or activies in Azure Dashboards, you can use Azure Log Analytics. You don't need to be an expert in KQL, since it's easy to master.

Below is the query you need to get all the pipelines that have succeded

```KQL
ADFPipelineRun

| project Status, Start, End, PipelineName

| filter Status == “Succeeded”

| sort by End
```

And in order to get information about the failed ones, we write the following query:

```KQL
ADFActivityRun

| filter Status == “Failed”

| project PipelineName, OperationName, Status, Start, End

| summarize End = max(End) by PipelineName, OperationName, Status

| sort by End
```

After that, just pin it to the Azure Dashboard and you're good to go.

![](https://miro.medium.com/max/1400/1*3Z1vajNwiLk-vIJZ9Zf7dg.png)

---

Azure Data Factory provides data integration and transformation layer that works across your digital transofmration initiatives.

### Workspaces
A Data Factory or Synapse Workspace can have one or more pipelines. A pipeline is a logical grouping of activities that together perform a task.

For example, a pipeline could contain a set of activities that ingest and clean log data, and then kick off a mapping data flow to analyze the log data.

The pipeline allows you to manage the activities as a set instead of each one individually. You deploy and schedule the pipeline of the activities independently.

### Datasets
A `dataset` is a named view of data that simply points or references the data you want to use in your `activities` as inputs and outputs.

Before you create a dataset, you must create a `linked service` to link your data store to the service. Linked services are much like connection strings, which define the connection information needed for the service to connect to external resources.