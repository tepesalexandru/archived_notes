#azure 

Before diving into Azure Networking, it's recommended to have a good understanding of [[Networking]].

---

Azure has its own physical network in and between data centers. Any network configuration done by an Azure user is purely software configuration of existing infrastructure and applications. It all ends up being entries in a database.

Networking services are split between 4 major categories:
- Connectivity
- Protection
- Delivery
- Monitoring

#### Connectivity
Azure Networking is built around `Virtual Networks` (VN). These provide connectivity betweewn services, inside and outside of Azure.

A VN is not rerquired for a good part of services, since they're usually managed SaaS or PaaS offerings. Instead, for IaaS services, such as VMs, you are usually expected to provide a VN.

---

An Azure Virtual Network (`VNet`) is a representation of your own network in the cloud. It is a logical isolation of the Azure cloud dedicated to your subscription.

You can use VNets to provision and manage Virtual Private Networks (`VPNs`) in Azure and, optionally, link the VNets with other VNets in Azure, or with your on-premises IT infrastructure to create hybrid or cross-premises solutions.

Each VNet you create has its own `CIDR` block and can be linked to other VNets and on-premises networks if the `CIDR` blocks do not overlap. You also have control of `DNS` server settings for VNets, and segmentation of the VNet into `subnets`.

## Subnets
A virtual network can be segmented into one or more `subnets`. Subnets provide logical division within your network. Subnets can help improve security, increase performance, and make it easier to manage the network.

Each subnet contains a range of `IP addresses` that fall within the virtual network `address space`. The range must be unique within the address space for the virtual network.

The address space must be specified by using `Classless Inter-Domain Routing (CIDR)` notation.
