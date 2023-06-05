---
title: "Azure SQL Database"
---
## Benefits
Benefits of using Azure SQL Database are:
- includes all benefits of PaaS Databases
- includes a managed backup service
- can use [[Azure Defender]]

## Creation
After creating an Azure SQL Database, you will always be able to connect to the database using the `admin` login account of the logical server.

## Common Uses
The main type of operation this service supports are Online Transaction Processing (OLTP) operations.

## Security
### Firewall
By default, each Azure SQL database is protected by a server-level firewall.

If the public IP address of your computer has changed, you need to insert it again in the database-level firewall to gain access.

### Azure AD
You can enable multi-factor authentication (MFA) when connecting to an Azure SQL Database by using [[Azure Active Directory]] authentication.

## Costs
You can use existing Microsoft SQL Server licenses to reduce the cost of Azure SQL Databases.
You do not need a Microsoft 365 subscription in order to create an Azure SQL Database.


