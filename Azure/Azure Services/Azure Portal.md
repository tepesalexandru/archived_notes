---
title: "Azure Portal"
---
#### Date: 22.05.2022
The Azure Portal lets you build, manage, and monitor everything from simple web apps to complex cloud applications in a single, unified console.

Azure Cloud Shell is an interactive, browser-accessible shell for managing Azure resources.

Azure Powershell is a module that you add to Windows Powershell or PowerShell Core to enable you to connect to your Azure subscription and manage resources.

An Azure PowerShell script looks like this:

```Powershell
New-AzVm `
    -ResourceGroupName "CrmTestingResourceGroup" `
    -Name "CrmUnitTests" `
    -Image "UbuntuLTS"
    ...
```

Other than this, you can also use the Azure CLI to connect to Azure and execute administrative commands on Azure resources, it runs on Windows, Linux and macOS.

An Azure CLI script looks like this:

```Azure CLI
az storage blob --help
```
