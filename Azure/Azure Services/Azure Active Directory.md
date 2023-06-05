#azure #az-104 

#### Date: 17.06.2022
Your company has an Azure DevOps environment that can only be accessed by Azure Active Directory users.  
You are instructed to make sure that the Azure DevOps environment can only be accessed from devices connected to the company's on-premises network.  

In order to do that, you need to configure `conditional access` in Azure Active Directory

![](https://www.examtopics.com/assets/media/exam-media/04156/0001500001.png)

---

Single Sign-On (SSO) - The same identity can be used across multiple applications. And that feature is called a single sign-on. You log in one time, and with that particular login, you try to access all the resources.

---
## Introduction
Azure Active Directory (Azure AD) is Microsoft's multi-tenant cloud-based directory and identity management service. Azure AD helps to support user access to resources and applications, such as:
- Internal resources and apps located on your corporate network
- External resources like Microsoft 365, the Azure Portal, and SaaS applications
- Cloud apps developed for your organization

The key components of the service are the following:
- `Identity` - An identity is an object that can be authenticated. The identity can be a user with a username and a password. Identities can also be applications or other servers that require authentication by using secret keys or certificates. Azure AD is the underlying product that provides the identity service.
- `Account` - An account is an identity that has data associated with it. To have an account, you must first have a valid identity. You can't have an account without an identity.
- `Azure AD Account` - An Azure AD account is an identity that's created through Azure AD or another Microsoft cloud service, such as Microsoft 365. Identities are stored in Azure AD and are accessible to your organization's cloud service subscription. The Azure AD account is also called a `work or school account`.
- `Azure Tenant (directory)` - An Azure tenant is a single dedicated and trusted instance of Azure AD. Each tenant (also called a `directory`) represents a single organization. When your organization signs up for a Microsoft cloud service subscription, a new tenant is automatically created. Because each tenant is a dedicated and trusted instance of Azure AD, you can create multiple tenants or instances.
- `Azure subscription` - An Azure subscription is used to pay for Azure cloud services. A subscription is linked to a credit card. Each subscription is joined to a single tenant. A tenant can have multiple subscriptions. => the tenant has a one to many relation with subscriptions.

## User Accounts
Every user who wants access to Azure resources needs an Azure user account. A user account has all the information required to authenticate the user during the sign-in process.

Azure AD supports three types of user accounts. The types indicate *where* the user is defined (in the cloud or on-premises), and whether the user is internal or external to your Azure AD organization. The types are:
- `Cloud identity` - A user with a cloud identity is defined only in Azure AD. When a cloud identity is removed from the primary directory, the user account is deleted.
- `Directory-syncrhonized identity` - User accounts that have a directory-synchronized identity are in an on-premises Active Directory. A synchronization activity occurs via Azure AD Connect to bring these user accounts in to Azure. The source for these accounts is Windows Server Active Directory.
- `Guest user` - Guest user accounts are defined outside Azure. Examples include user accounts from other cloud providers, and Microsoft accounts like an Xbox LIVE account. The source for guest user accounts is `Invited user`. Guest user accounts are useful when external vendors or contractors need access to your Azure resources.

An administrator user can either `create` a user within the organization or `invite` a guest user to provide access to organization resources.

---

Azure Active Directory (Azure AD) is a cloud-based identity and access management service. It supports single sign-on, multifactor authentication, and conditional access.

Azure Active Directory is made up of 4 core concepts:
- Identity - An identity is something that can be authenticated. For example, a user with an email and password.
- Account - An identity that has data associated with it. For example, username, roles, address and so on.
- Tenant - Also called a directory, its used to represent a single organization
- Subscription - The credit card (or monthly credits) linked to the a tenant

## Accounts
Every user who needs access to an Azure resource needs to have an Azure account.

There are three types of user accounts in Azure:
- Cloud Identity
- Directory-Synchronized Identity
- Guest User

## Tenants
A tenant, also commonly called a "directory", represents an organization. Each Azure AD tenant is globally distinct and is fully independent of other Azure AD tenants.

New Azure AD tenants can be created directly from the Azure Portal. For an in-depth guide, you can follow the official Microsoft Docs here: https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-access-create-new-tenant.

## Subscriptions
An Azure subcription is a logical unit of Azure services that's linked to an Azure account. Subscriptions help you organize access to Azure cloud services, and help you control how resource usage is reported, billed, and paid.

An Azure Subscription can be linked to only one Azure AD tenant. On the other hand, one tenant can have multiple subscriptions.

## User Groups
Azure AD provides several ways to manage access to resources, applications, and tasks. One of these is Azure AD groups, which allow you to grant permission to a group of users instead of assigning the permission to each user individually.

There are two main group types to choose from, and three group membership types.

The two group types are:
- Security
- Microsoft 365

The three membership types are:
- Assigned
- Dynamic User
- Dynamic Device

---

To create and use Azure services, you need an Azure subscription. When you sign up, an Azure subscription is created for you. It allows you to build and deploy cloud-based applications, use sophisticated artificial intelligence services, and extract essential insights from your data.

The Azure free account includes free access to popular Azure products for 12 months, $200 USD credit to spent for the first 30 days, and access to more than 25 products that are always free.

An Azure subscription is a logical container used to provision resources in Azure. It holds the details of all your resources like Virtual Machines (VMs), databases, and more.

When you create an Azure resource like a VM, you identity the subscription it belongs to. As you use the VM, the usage of the VM is aggregated and billed monthly.

An organization (tenant) has one associated default Azure AD directory. However, owners can create additional directories to support development or testing purposes, or because they want to have separate directories to synchronize with their local Windows Server AD forests.

More info here: https://learn.microsoft.com/ro-ro/training/modules/manage-users-and-groups-in-aad/2-create-aad

A subscription in Azure is both a billing entity and a security boundary. Resources such as virtual machines, websites, and databases are associated with a single subscription.

Each subscription also has a single account owner responsible for any charges incurred by resources in that subscription. If your organization wants a subscription billed to another account, you can transfter the subscription.

A subscription is associated with a single Azure AD directory. Multiple subscriptions can trust the same directory, but a subscription can only trust one directory.

A user account contains all the information needed to authenticate during the sign-in process. Once authenticated, Azure AD builds an access token to authorize the user, determine what resources he can access, and determine what he can do with those resources.

An Azure AD group helps organize users, which makes it easier to manage permissions. Using groups lets the resource owner (or Azure AD directory owner), assign a set of permissions to all the members of the group instead of having to provide the rights one-by-one.

Even better, Azure AD supports the ability to define membership based on rules, such as what department a user works in, or the job title they have.

Azure AD provides serveral built-in roles to cover the most common security scenarios. They are:
- Owner - has full access to all resources, including the right to delegate access to others
- Contributor - can create and manage all types of Azure resources but can't grant access to others
- Reader - can view all existing Azure resources

Each role is a set of properties defined in a JSON file. This role definition includes a Name, ID, and Description. It also includes the allowable permissions (Actions), denied permissions (NotActions), and scope (for example, read access) for the role.

The Owner Role, has all actions (indicated by an asterisk `*`), no denied actions, and all scopes (indicated by a forward slash `/`). 

You can display all of this information yourself by using the terminal, for example in PowerShell the command is:

```powershell
Get-AzRoleDefinition Owner
```

And the output would be:

```powershell
Name             : Owner
Id               : 8e3af657-a8ff-443c-a75c-2fe8c4bcb635
IsCustom         : False
Description      : Lets you manage everything, including access to resources.
Actions          : {*}
NotActions       : {}
DataActions      : {}
NotDataActions   : {}
AssignableScopes : {/}
```

As a nice exercise for the reader, you can try displaying the information for the `Contributor` and `Reader` built-in roles.

Ideas: Define your own custom roles (another article) "Create your own roles in Azure AD"

https://learn.microsoft.com/ro-ro/training/modules/manage-users-and-groups-in-aad/5-manage-aad-roles