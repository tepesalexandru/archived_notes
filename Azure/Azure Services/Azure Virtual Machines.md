#azure #az-204 

With Azure Virtual Machines (VMs), you can create and use VMs in the cloud. VMs provide infrastructure as a service (**IaaS**) in the form of a virtualized server and can be used in many ways.

Just like a physical computer, you can customize all of the software running on your VM. 

VMs are an ideal choice when you need:
- Total control over the Operating System (OS)
- The ability to run custom software
- To use custom hosting configurations


Another type of VM in Azure is [[Azure Virtual Desktop]].

### Create an Azure Virtual Machine
Let's look at the flow of creating an Azure VM using the Azure CLI. 

You can use the Azure CLI by going in the Azure Portal and opening up the Cloud Shell. For this example, I'm going to use Bash as the CLI environment.

The first step is to create a `resource group`, in case it doesn't already exist. The command for this is the following:

```bash
az group create \
	--name azure-resource-group \
	--location europe
```

After the resource group has been created, let's run the command to create the Virtual Machine:

```bash
az vm create \
	--name vm1
	--resource-group azure-resource-group
	--image UbuntuLTS
	--admin-username sample-user
```

When creating a VM, you also need to specify what type of image you want to run. In simple terms, the "image" refers to the operating system. In this example, its a virtual machine running Ubuntu, with an admin user named "sample-user".



