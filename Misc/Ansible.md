---
title: "Ansible"
---

**Ansible** is an open-source platform by Red Hat that automates cloud provisioning, configuration management, and application deployments.

The main difference between Ansible and other tools such as Puppet or Chef is that Ansible is **agentless**, meaning that you don't have to install software on the managed machines.

The main components of Ansible are the following:
- Control Machine
- Managed Nodes
- Playbooks
- Modules
- Inventory
- Roles
- Facts
- Plug-ins

To enable a computer to act as a Control Machine which can run playbooks, you will need to install Python and Ansible.

You can use Ansible on Azure in various ways, such as:
- From the Marketplace, with the "Red Hat Ansible" or "Ansible Tower (by Red Hat)" images
- An Azure VM with Linux as Operating System (Windows isn't supported as Control Machine)

Playbooks in Ansible are written in YAML, here's how a playbook looks like:

```Yml
- name: Create Azure VM.
  hosts: localhost
  connection: local
  vars:
  resource_group: ansible_rg5
  location: westus
  tasks:
    - name: Create resource group.
      azure_rm_resourcegroup:
        name: "{{ resource_group  }}"
        location: "{{ location  }}"
    - name: Create virtual network.
      azure_rm_virtualnetwork:
        resource_group: myResourceGroup
        name: myVnet
        address_prefixes: "10.0.0.0/16"
    - name: Add subnet.
      azure_rm_subnet:
        resource_group: myResourceGroup
        name: mySubnet
        address_prefix: "10.0.1.0/24"
        virtual_network: myVnet
    - name: Create public IP address.
      azure_rm_publicipaddress:
        resource_group: myResourceGroup
        allocation_method: Static
        name: myPublicIP
      register: output_ip_address
    - name: Dump public IP for VM, which will be created.
      debug:
        msg: "The public IP is {{ output_ip_address.state.ip_address }}."
    - name: Create Network Security Group that allows SSH.
      azure_rm_securitygroup:
        resource_group: myResourceGroup
        name: myNetworkSecurityGroup
        rules:
          - name: SSH
            protocol: Tcp
            destination_port_range: 22
            access: Allow
            priority: 1001
            direction: Inbound
    - name: Create virtual network interface card.
      azure_rm_networkinterface:
        resource_group: myResourceGroup
        name: myNIC
        virtual_network: myVnet
        subnet: mySubnet
        public_ip_name: myPublicIP
        security_group: myNetworkSecurityGroup
    - name: Create VM.
      azure_rm_virtualmachine:
        resource_group: myResourceGroup
        name: myVM
        vm_size: Standard_DS1_v2
        admin_username: azureuser
        ssh_password_enabled: false
        ssh_public_keys:
          - path: /home/azureuser/.ssh/authorized_keys
            key_data: <your-key-data>
        network_interfaces: myNIC
        image:
          offer: CentOS
          publisher: OpenLogic
          sku: "7.5"
          version: latest
```
