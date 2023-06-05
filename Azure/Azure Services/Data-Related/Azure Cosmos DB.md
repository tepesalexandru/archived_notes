#azure #az-204 

## Introduction
Azure Cosmos DB is a globally distributed database system that allows you to read and write data from the local replicas of your database and it transparently replicates the data to all the regions associated with your Cosmos account.

`Azure Cosmos DB` is a highly scalable cloud database service for `NoSQL` data. You can emulate Cosmos DB locally

Azure Cosmos DB is used for mission critical applications at global scale, including Skype, Xbox, Microsoft 365, Azure, and many others.

Cosmos DB is highlty suitable for the following scenarios:
- IoT and telematics
- Retail and marketing
- Gaming
- Web and mobile applications

## Structure
An Azure Cosmos Container is the fundamental unit of scalability. Azure Cosmos DB transparently partitions your container using the logical `partition key` that you specify in order to elastically scale your provisioned throughput and storage.

The following image visualized the hierarchy of Azure Cosmos DB:

![](https://docs.microsoft.com/en-us/learn/wwl-azure/explore-azure-cosmos-db/media/cosmos-entities.png)

❗ There is a limit of 50 Azure Cosmos DB accounts under one Azure Subscription.

## APIs
Azure Cosmos DB supports multiple `APIs`. When creating a new Cosmos DB instance, you select the API you want to use.

The main APIs for Cosmos DB are the following:
- Core API (SQL) => uses JSON for read/writes
- MongoDB API
- Table API
- Cassandra API
- Gremlin API (graph structure)

❗ You can only choose what API to use at the Cosmos DB Account creation

### Table API
The Table API in Azure Cosmos DB is usually used for simple key/value pairs lookups.

### Gremlin API
You can query a `graph` database in Azure Cosmos DB as nodes and edges by using the Gremlin API.

A graph database natively supports the analysis of `relationships` between entities.

#### Examples
Your company needs to design a database that shows how changes in network traffic in one area of a network affect network traffic in other areas of the network. Which type of data store should you use? `Graph`

## Partition Keys
Cosmos DB stores your data on different servers called partitions.

Partitions can be:
- Logical - A portion of the CosmosDB container based on a condition. All items stored in a logical partion share the same partition key
- Physical - A group of replicas of your data stored on the servers

Each logical partition has a limit of 20 GB.

The partition key is how Cosmos DB knows how to split the data into the logical partitions. Also, the partition key is immutable, once you have selected it.

The partition key must be chosen with performance in mind, frequent queries and the 20 GB limit per logical partition.

The partition key must be on fields that will never update and have high cardinality (wide range of possible values). A good partition key would be "country".

In situations where none of the object's properties can be used as a partition keym a synthetic one can be created by concatenating two properties, such as "city-country" - "Oradea-Romania"

---

Azure Cosmos DB uses partitioning to scale individual containers in a database to meet the performance needs of your application.

---
To create a CosmosDB using the CLI, use the following command:

```shell
az cosmosdb create \
	--name <db-name> \
	--resoucr-group <resource-group-name> \
	--capabilities EnableTable \
	--default-consistency-level Eventual
```

The `EnableTable` configuration is in order to use the TableAPI

After the database has been created, you can use the following command to create a table:

```shell
az cosmosdb table create
	--account-name <db-name> \
	--resource-group <rg-name> \
	--name <table-name> \
	--throughput 400
```

The `throughput` is mesured in RUs.

---
