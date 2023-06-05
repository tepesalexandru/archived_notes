---
title: "DP-900 | Practice Questions #1"
---
Q1. Objects in which things about data should be captured and stored are called `tables`. ❌ => `entities`

A `table` is the object that stores a collection of `entities`.

Q2. You need to process data that is generated continously and near real-time responses are required. You should use `streaming data processing`. ✅

Q3. ❌
- Optimize data privacy => `ELT` 
- Provide support for Azure Data Lake => `ETL`
- Manage large volumes of data `ETL`

=> ETL is the correct approach when you need to filter sensitive data before uploading the data into an analytical model. It is suitable for data models that do not require Azure Data Lake support. (1)

=> ELT is the correct approach because it supports Azure Data Lake as the data store and manages large volumes of data. (2, 3)

Q4. The technique that provides recommended actions that you should take to achieve a goal or target is called `predictive` analysis. ❌

=> `prescriptive` analysis helps you define actions (prescriptions) that you should perform to achieve what you need (or overcome a problem)

Q5. ✅
- Create relationships => `Keys`
- Improve processing speed for data searches => `Indexes`
- Store instances of entities as rows => `Tables`
- Display data from predefined queries => `Views`

Q6. The process of splitting an entity into more than one table to reduce data redudancy is called `normalization`. ✅

Q7. Azure SQL Database is an example of `platform`-as-a-service. ✅

Q8. You need to query an Azure SQL database. ❌
- Query data while working within a Visual Studio project => `Azure Data Studio`
- Query data located in a non-Microsoft platform => `SQL Server Data Tools`
- Query data from within the Azure portal => `Azure Query Editor`

=> `Azure Data Studio` is a cross-platform database tool that you can use with both on-premise and cloud data platforms on Windows, macOS and Linux. (2)
=> `Azure Query Editor` is available in the Azure Portal.
=> `SQL Server Data Tools` is available in Visual Studio. You can use this tool to connect to and query on-premises and cloud data services. (1)

Q9. The act of increasing or decreasing the resources that are available for a service is called `scaling`. ✅

Q10. You are creating queries to retrieve data from an Azure SQL database ✅
- Filter records => `WHERE`
- Combine rows from multiple tables => `JOIN`
- Calculate the total value of a numeric column => `SUM`
- Determine the number of rows retrieved => `COUNT`

---

Q11. What are three characteristics of non-relational data? ✅
- Flexbile storage of ingested data
- Entities are self-describing
- Entities may have different fields

Q12. You have data that consists of JSON-based documents. You need to store the data in an Azure environment that supports efficient non-key, field-based searching. ✅

You should use `Azure Cosmos DB` as the data store.

Q13. You need to create a graph database. Which Azure data service should you use? `Azure Cosmso DB`. ✅

Q14. You use Azure Table Storage as a non-relational data store. You need to optimize data retrieval. You should use `partition keys and row keys` as query criteria. ✅

Q15. You need to use JSON files to provision Azure Stroage. What should you use? ❌
- Azure Portal
- Azure CLI
- Azure PowerShell

=> you need to use `Azure Resource Manager (ARM) templates`

Q16. For which reason should you deploy for a data warehouse? ❌
- Perform sales trend analyses
- Print sales orders
- Search status of sales orders

=> just to perform sales trend analyses

Q17. Which two Azure data services support Apache Spark clusters? ❌
- Azure Synapse Analytics
- Azure Data Factory

=> Azure Synapse Analytics AND `Azure Databricks`

Q18. You design a data ingestion and transformation solution by using Azure Data Factory service. You need to get data from an Azure SQL database. Which two resources should you use? ✅
- Linked service
- Dataset

Q19. Which Azure Data Factory component should you use to represent data that you want to ingest for processing? ❌
- Linked services
- Datasets

=> only `datasets`

Q20. You are designing reports by using Microsoft Power BI. For which three scenarios can you create Power BI reports as paginated reports? ✅
- A report that has a table visual with an ability to print all the data in the table
- A report with a repeatable header and footer
- A report that is formatted to fit well on a printed page

Result => 12/20 => 60% => Failed test ❌