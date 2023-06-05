---
title: "Relational Data"
---
#### Date: 15.06.2022
In a relational database, you model collections of entities from the real world as `tables`.
A table contains `rows`, and each row represents a single instance of an `entity`.

Relational databases are a format for `structured data`. Each column stores data of a specific datatype.

---

Data `normalization` is a term used by database professionals for a schema design process that minimizes data duplication and enforces data integrity.

A simple definition for practical purposes is the following:
1. Separate each entity into its own table
2. Separate each discrete attribute into its own column
3. Uniquely identify each entity instance (row) using a `primary key`
4. Use `foreign key` columns to link related entities.

In some cases, a `key` (primary or foreign) can be defined as a `composite key` based on a unique combination of multiple columns.

---

`SQL` stands for `Standard Query Language` and is used to communicate with a relational database. Some common relational database management systems that use SQL include:
- Microsoft SQL Server
- MySQL
- PostgreSQL
- MariaDB
- Oracle

Some popular dialects of SQL include:
- `Transact-SQL` (T-SQL) - Used by Microsoft SQL Server and Azure SQL services.
- `pgSQL` - Used by PostgreSQL
- `PL/SQL` (Procedural Language/SQL) - Used by Oracle

---

SQL statements are grouped into three main logical groups:
- Data Definition Language (DDL)
- Data Control Language (DCL)
- Data Manipulation Language (DML)

`DDL` statements are used to create, modify, and remove tables and other objects in databases. Some of the most used statements are: `CREATE`, `ALTER`, `DROP`, and `RENAME`.

`DCL` statements are used to manage access to objects in a database by granting, denying, or revoking permissions to specific users or groups. The three main DCL statements are: `GRANT`, `DENY`, and `REVOKE`.

`DML` statements are used to manipulate the rows in tables. The four main DML statements are: `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.

---

In addition to tables, a relational database can contain other structures that help to optimize data organization, encapsulate programmatic actions, and improve the speed of access. Some of them are: `views`, `stored procedures` and `indexes`.

---

A `view` is a `virtual table` based on the results of a `SELECT` query. You can query the view and filter the data in much the same way as a table. Here are some examples:

Creating the view "Deliveries":

```SQL
CREATE VIEW Deliveries
AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.CustomerID = c.ID;
```

Querying the view:

```SQL
SELECT OrderNo, OrderDate, LastName, Address
FROM Deliveries
WHERE City = 'Seattle';
```

---

A `stored procedure` defines SQL statements that can be run on command. They are used to encapsulate programmatic logic in a database for actions that applications need to perform when working with data. Here is an example:

Creating a procedure named "RenameProduct" that has two parameters:

```SQL
CREATE PROCEDURE RenameProduct
	@ProductID INT,
	@NewName VARCHAR(20)
AS
UPDATE Product
SET Name = @NewName
WHERE ID = @ProductID;
```

Calling the stored procedure:

```SQL
EXEC RenameProduct 201, 'Spanner';
```

---

An `index` helps you search for data in a table. When you create an index, you have to specify a column from the table, and the index contains a copy of this data in a sorted order, with pointers to the corresponding rows in the table.

When a user runs a query that specifies this column in the `WHERE` clause, the database management system can use this index to fetch the data more quickly than if it had to scan through the entire table row by row.

Here is an example of how to create an index:

```SQL
CREATE INDEX idx_ProductName
ON Product(Name);
```

The index creates a `tree-based` structure that the database system's query optimizer can use to quickly find rows:

![Example](https://docs.microsoft.com/ro-ro/learn/wwl-data-ai/explore-relational-data-offerings/media/index.png)


But, there is a catch. You can't simply put infinite indexes on all your columns, they come at a cost. Each index `consumes storage space`, and each time you insert, update, or delete data in a table, the indexes for that table must be maintained. This can slow down the DML statements. 

A `clustered index` is an object associated with a table that sorts and stores the data rows in the table based on their key values.

---

The best intro to relational data in azure is through [[Azure SQL]]

---

A relational database is appropriate for scenarios that involve a high volume of `transactional writes`.