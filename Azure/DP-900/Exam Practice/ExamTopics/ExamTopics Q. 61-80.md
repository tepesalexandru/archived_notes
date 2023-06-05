#dp-900-exam-practice 

61. HOT SPOT 📝
- Azure SQL Database includes a managed backup service => `yes`
- Azure SQL Database has build-in high availability => `yes`
- Azure SQL Database can use Azure Defender => `yes`

62. HOT SPOT
- You can use Azure Data Studio to query a Microsoft SQL Server big data cluster => `yes`
- You can use Microsoft SQL Server Management Studio (SSMS) to query an Azure Synapse Analytics data warehouse => `yes`
- You can use MySQL Workbench to query Azure Database for MariaDB databases. => `yes`

63. HOT SPOT 📝
- PaaS database offerings in Azure provide built-in high availability => `yes`
- PaaS database offerings in Azure provide configurable scaling options => `yes`
- PaaS database offerings in Azure reduce the administrative overhead for managing hardware => `yes`

64. You have the following SQL Query: 📝
![](https://www.examtopics.com/assets/media/exam-media/04162/0007300001.png)

What are dbo.Products and ProductName?
- dbo.Products - `a table`
- ProductName = `a column`

65. HOT SPOT 📝
- You must apply operating system updates to Azure SQL databases regularly => `no`
- You need a Microsoft 365 subscription to create an Azure SQL database => `no`
- You can use existing Microsoft SQL Server licenses to reduce the cost of Azure SQL databases => `yes`

66. Which statement is an example of DDL? `CREATE` 📝
67. HOT SPOT
- Azure Data Studio can be used to query an Azure SQL database from a device that runs macOS `yes`
- SSMS enables users to create and use SQL notebooks => `no`
- Azure Data Studio can be used to restore a database => `yes`

68. You are deploying a software as a service application that requires a relational database for  Online Transaction Processing (OLTP). Which Azure service should you use to support the application? `Azure SQL Database` 📝

69. What are two benefits of PaaS relational databases offerings in Azure, such as Azure SQL Database? 📝
- `access to the latest features`
- `reduced administrative effort for managing the server infrastructure`

70. HOT SPOT 📝
- If you have a PaaS database in Azure, you are responsible for applying operating system updates => `no`
- If you have a PaaS database in Azure, backups are performed automatically => `yes`
- If you have a PaaS database in Azure, you are responsible for installation of the database engine => `no`

71. You have a table names Sales that contains the following data:
![](https://www.examtopics.com/assets/media/exam-media/04162/0008100001.png)

You need to query the table to return the average sales amount per day. The output must produce the following results:

![](https://www.examtopics.com/assets/media/exam-media/04162/0008100002.png)

Answer:

```SQL
SELECT SalesDate, AVG(SalesAmount)
FROM Sales
GROUP BY SalesDate
ORDER BY SalesDate
```

72. When you create an Azure SQL Database, which account can always connect to the database? `the server admin login account of the logical server`. 📝

73. Which statement is an example of DDL? `DROP` 📝
74. A team of developers has computers that run Windows 10 and Ubuntu Desktop.  
The developers need to connect to and query an Azure SQL database from each of their computers. The developers require code assistance features such as IntelliSense.  
What should the developers use? `Azure Data Studio`

75. Transparent Data Encryption (TDE) encrypts `the database to protect data at rest`.
76. You need to ensure that users use multi-factor authentication (MFA) when connecting to an Azure SQL database. Which type of authentication should you use? `Azure Active Directory (Azure AD) authentication` 📝
77. What is a benefit of hosting a database on Azure SQL managed instance as compared to Azure SQL database? `native support for cross-database queries and transactions`
78. By default, each Azure SQL database is protected by `a server-level firewall` 📝
79. You need to design and model a database by using a graphical tool that supports project-oriented offline database development. What should you use? `Microsoft SQL Server Data Tools (SSDT)`
80. DRAG DROP 📝
- Prevent access to an Azure SQL database from another network => `Firewall`
- Support Azure AD sign-ins to an Azure SQL database => `Authentication`
- Ensure that sensitive data never appears as plain text in Azure SQL database => `Encryption`