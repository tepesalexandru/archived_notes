---
title: "Terraform"
---

**Hashicorp Terraform** is an open-source tool that allows you to provision, manage, and version cloud infrastructure. It codifies infrastructure in configuration files that describe the topology of cloud resources such as VMs, storage accounts, and networking interfaces.

Terraform is formed from the following components:
- Configuration files
- Terraform CLI
- Modules
- Provider
- Overrides
- Resources
- Execution plan
- Resource graph

There are many ways to get started with Terraform on Azure, such as the Azure Marketplace, the Terraform Marketplace and Azure VMs directly.

Terraform can be installed on Windows, Linux and macOS.

Terraform files end with the .tf or .tf.json extensions. Here's an example of such a configuration file in Terraform:

```Yml
# Configure the Microsoft Azure Provider
provider "azurerm" {
    subscription_id = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    client_id      = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    client_secret  = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    tenant_id      = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}

# Create a resource group if it does not exist
resource "azurerm_resource_group" "myterraformgroup" {
    name    = "myResourceGroup"
    location = "eastus"

    tags {
        environment = "Terraform Demo"
    }
}

# Create virtual network
resource "azurerm_virtual_network" "myterraformnetwork" {
    name                = "myVnet"
    address_space      = ["10.0.0.0/16"]
    location            = "eastus"
    resource_group_name = "${azurerm_resource_group.myterraformgroup.name}"

    tags {
        environment = "Terraform Demo"
    }
}

# Create subnet
resource "azurerm_subnet" "myterraformsubnet" {
    name                = "mySubnet"
    resource_group_name  = "${azurerm_resource_group.myterraformgroup.name}"
    virtual_network_name = "${azurerm_virtual_network.myterraformnetwork.name}"
    address_prefix      = "10.0.1.0/24"
}

# Create public IPs
resource "azurerm_public_ip" "myterraformpublicip" {
    name                        = "myPublicIP"
    location                    = "eastus"
    resource_group_name          = "${azurerm_resource_group.myterraformgroup.name}"
    public_ip_address_allocation = "dynamic"

    tags {
        environment = "Terraform Demo"
    }
}

# Create Network Security Group and rule
resource "azurerm_network_security_group" "myterraformnsg" {
    name                = "myNetworkSecurityGroup"
    location            = "eastus"
    resource_group_name = "${azurerm_resource_group.myterraformgroup.name}"

    security_rule {
        name                      = "SSH"
        priority                  = 1001
        direction                  = "Inbound"
        access                    = "Allow"
        protocol                  = "Tcp"
        source_port_range          = "*"
        destination_port_range    = "22"
        source_address_prefix      = "*"
        destination_address_prefix = "*"
    }

    tags {
        environment = "Terraform Demo"
    }
}

# Create network interface
resource "azurerm_network_interface" "myterraformnic" {
    name                      = "myNIC"
    location                  = "eastus"
    resource_group_name      = "${azurerm_resource_group.myterraformgroup.name}"
    network_security_group_id = "${azurerm_network_security_group.myterraformnsg.id}"

    ip_configuration {
        name                          = "myNicConfiguration"
        subnet_id                    = "${azurerm_subnet.myterraformsubnet.id}"
        private_ip_address_allocation = "dynamic"
        public_ip_address_id          = "${azurerm_public_ip.myterraformpublicip.id}"
    }

    tags {
        environment = "Terraform Demo"
    }
}

# Generate random text for a unique storage account name
resource "random_id" "randomId" {
    keepers = {
        # Generate a new ID only when a new resource group is defined
        resource_group = "${azurerm_resource_group.myterraformgroup.name}"
    }

    byte_length = 8
}

# Create storage account for boot diagnostics
resource "azurerm_storage_account" "mystorageaccount" {
    name                        = "diag${random_id.randomId.hex}"
    resource_group_name        = "${azurerm_resource_group.myterraformgroup.name}"
    location                    = "eastus"
    account_tier                = "Standard"
    account_replication_type    = "LRS"

    tags {
        environment = "Terraform Demo"
    }
}

# Create virtual machine
resource "azurerm_virtual_machine" "myterraformvm" {
    name                  = "myVM"
    location              = "eastus"
    resource_group_name  = "${azurerm_resource_group.myterraformgroup.name}"
    network_interface_ids = ["${azurerm_network_interface.myterraformnic.id}"]
    vm_size              = "Standard_DS1_v2"

    storage_os_disk {
        name              = "myOsDisk"
        caching          = "ReadWrite"
        create_option    = "FromImage"
        managed_disk_type = "Premium_LRS"
    }

    storage_image_reference {
        publisher = "Canonical"
        offer    = "UbuntuServer"
        sku      = "16.04.0-LTS"
        version  = "latest"
    }

    os_profile {
        computer_name  = "myvm"
        admin_username = "azureuser"
    }

    os_profile_linux_config {
        disable_password_authentication = true
        ssh_keys {
            path    = "/home/azureuser/.ssh/authorized_keys"
            key_data = "ssh-rsa AAAAB3Nz{snip}hwhqT9h"
        }
    }

    boot_diagnostics {
        enabled = "true"
        storage_uri = "${azurerm_storage_account.mystorageaccount.primary_blob_endpoint}"
    }

    tags {
        environment = "Terraform Demo"
    }
}
```

---

In order to deploy an Azure Resource group via Terraform, you should install the following frameworks: `Yeoman` and `Terratest`

---

Terraform is an Infrastructure as Code (IaC) tool that allows you to deploy, you guessed it, infrastructure in a human readable format. What makes it so popular is that it has multi-cloud usability, meaning that the same code/infrastructure can be deployed in AWS and in Azure.

In order to work with it, you will need to install the Terraform CLI first.