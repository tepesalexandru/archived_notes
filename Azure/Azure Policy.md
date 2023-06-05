#azure #az-104 

## Introduciton
Azure Policty is a service in Azure that enables you to create, assign, and manage policies to control or audit your resources. These policies enforce different rules over your resource configurations so the configurations stay compliant with corporate standards. 

You apply the policies to your resources by using `management groups`.

## Management Groups
Azure management groups provide a level of scope and control above your subscription. You can use management groups as container to manage access, policy, and compliance across your subscription.

By default, all new subscriptions are placed under the top-level management group: `root group`

A management group tree can support up to six levels of depth, and all subscriptions within a management group automatically inherit the conditions applied to that management group.

Management groups can be created using the Azure Portal, PowerShell, or the Azure CLI.

Every management group has a directory unique identifier (ID) and a display name (optional, can be changed at any time).

The `ID` is used to submit commands on the management group.

---

Azure Policy is a service in Azure that you can use to create, assign, and manage policies. You can use policies to enforce rules on your resources to meet corporate compliance standards and service level agreements.

Azure Policy runs evaluations and scan on your resources to make sure they're compliant.

The main advantages of Azure Policy are in the areas of enforcement and compliance, scaling, and remediation.

Advantages of Azure Policy:
- Enforce rules and compliance
- Apply policies at scale
- Perform remediation
- Exercise governance

Examples of policy usages:
- Specify the resource types that your organization can deploy, for example, which Virtual Machine SKUs are available.
- Restrict locations users can specify when deploying resources
- Have mandatory tags on resources and define the allowed values
- Have mandatory backups of VMs

A `policy definition` describes the compliance conditions for a resource, and the action to complete when the conditions are met. One or more policy definitions are grouped into an `initiative definition`.

There are 4 steps to create and work with policy definitions:
1. Create policy definitions
2. Create an initiative definition
3. Scope the initiative definition
4. Determine compliance

Azure Policy offers built-in policy definitions to help you quickly configure control conditions for your resources. In addition, you can also create your own definitions, or import definitions from other sources.

Examples of built-in policies are:
- Allowed Virtual Machine size SKUs
- Allowed locations
- Disable public network access on IoT devices

If you don't find a build-in policy, you can create your own definition. Policy definitions can also be imported from GitHub. For example, this one: https://github.com/Azure/azure-policy/tree/master/samples/SQL/sql-db-skus

Policy Definitions are specified in JSON, and have a specific format which you can find here: https://learn.microsoft.com/en-us/azure/governance/policy/concepts/definition-structure

The next step after creating a set of policy definitions is to create an `initiative definition`.
Policy Initiatives can be created in the Azure Portal, and also follow a specific JSON structure: https://learn.microsoft.com/en-us/azure/governance/policy/concepts/initiative-definition-structure

There are also built-in policy initiative definitions, such as:
- ISO 27001:2013
- Audit machines with insecure password security settings
- Configure Windows Machines to run Azure Monitor Agent and associate them to the Data Collection Rule

The next step is to `scope the initiative definition`. The scope determines what resources or grouping of resources are affected by the conditions of the policies.

The scope is applied to a subscription, and a resource group in that subscription.

After the scope has been set, you can evaluate your `compliance` in the Azure Portal. This is a percentage calculated on existing resources, since applying the policy doesn't affect the existing resources in any way, it only blocks new non-compliant ones.

By analyzing the compliance report, you can take the needed steps to modify the existing resources to meet the new standard.