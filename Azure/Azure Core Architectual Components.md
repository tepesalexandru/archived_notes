#azure 

Throughout your journey with Microsoft Azure, you'll hear and use terms like Regions, Availability Zones, Resources, Subscriptions, and more.

The core architectual components of Azure may be broken down into two main groupings: **physical infrastructure**, and the **management infrastructure**.

### Physical Infrastructure
The physical infrastructure for Azure starts with **datacenters**.

Conceptually, the datacenters are the same as large corporate datacenters. They're facilities with resources arranged in racks, with dedicated power, cooling, and networking infrastructure.

Azure has datacenters all around the world. However, these individual datacenters aren't directly accessible. Datacenters are grouped into **Azure Regions** or **Azure Availability Zones** that are designed to help you achieve resiliency and reliability for your business-critical workloads.

> [!INFO]
> Datacenters are grouped into Regions and Availabilty Zones.

### Regions
A region is a geographical area on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with low-latency network.

When you deploy a resource in Azure, you'll often need to choose the region where you want your resource deployed.

### Availability Zones
Availability zones are physically separate datacenters within an Azure Region.

Each availability zone is made up of one or more datacenters. An availability zone is set up to be an isolation boundary. If one zone goes down, the other continues working.

Availability zones are connected through high-speed, private fiber-optic networks.

> [!INFO]
> An Azure Region is made up of multiple Availability Zones.

