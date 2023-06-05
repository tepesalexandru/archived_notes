---
title: "ELT (Extract, Load, Transform)"
---
## Introduction
When using an extract, load, and transform (ELT) process, you need a target `data store` powerful enough to transform data.

Some `benefits` of using an ELT process are:
- It can reduce the transfer of sensitive data to destination systems
- It minimizes the time it takes to copy large volumes of data to the destination systems

Important Note: The ELT process does not use a compute resource independent of the source system and destination system

## Examples
Your company plans to load data from a customer relationship management (CRM) system to a data warehouse by using an extract, load, and transform (ELT) process.  
Where does data processing occur for each stage of the ELT process?

Extract: CRM
Load: The Data Warehouse
Transform: The Data Warehouse