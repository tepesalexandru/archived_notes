---
title: "Azure Automation"
---
#### Date: 09.05.2022
Azure Automation is a service provided by Azure to automate DevOps tasks and much more.

In order to get started with Azure Automation, you must first create an account inside of the Azure Portal.

Runbooks serve as repositories for your custom scripts and workflows. When creating runbooks, you can choose either from Graphical, Powershell or Python runbooks.

Inside of your runbooks, you can access shared resources.

Many runbooks have already been created by the team at Microsoft as well as by the community, and you can use them by browing the gallery, and make necessary changes if you need to.

You can automate running a runbook by either scheduling it or using a webhook.

Another way to automate tasks is via Powershell Workflow.


---

#### Date: 17.06.2022
The Azure Automation command `Register-AzAutomationDscNode` registers an Azure Virtual Machine running Windows OS as a [[Desired State Configuration (DSC)]] node for an Automation account.

This command can take various parameters, such as the `-ConfigurationMode`. The three possible values for this parameter are:
- ApplyAndMonitor
- ApplyAndAutocorrect
- ApplyOnly

