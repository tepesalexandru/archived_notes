#azure #az-204 

Azure Key Vault is a cloud service for securely storing and accessing secrets. A secret is anything that you want to tightly control access to, such as API keys, passwords, certificates, or cryptographic keys.

#### Benefits
- Is is a centralized store for application secrets. Instead of storing the connection string in the application's code, you can store it in Key Vault.
- Access to a key vault requires proper authentication and authorization ebfore a caller can get access.
- You can monitor any activity with Key Vault by enabling logging for your vaults

#### Best Practices
- Recommeneded to use separate Key Vaults per environment (dev, prod, etc.)
- Securely control the access of the key vault from unauthorized users and applications
- Create regular backups 
- Turn on soft-delete and purge protection in order to be safe against force deletion attacks.

---

### Using Azure Key Vault provider to secure Kubernetes secrets in AKS

First, create a resource group for the AKS cluster:

```shell
az group create --name myAKSResourceGroup --location eastus
```

Then, create an AKS cluster while enabling Azure Key Vault Provider for Secret Store CSI Driver:

```shell
az aks create \  
	--resource-group myAKSResourceGroup \  
	--name myAKSCluster \  
	--network-plugin azure \  
	--enable-managed-identity \  
	--enable-addons azure-keyvault-secrets-provider
```

Download the cluster credentials and configure `kubectl` to use them:

```shell
az aks get-credentials --resource-group myAKSResourceGroup --name myAKSCluster
```

Now you can check that the Secrets Store CSI Driver and the Azure Key Vault Provider are installed in the cluster:

```shell
kubectl get pods -n kube-system -l 'app in (secrets-store-csi-driver, secrets-store-provider-azure)'
```
