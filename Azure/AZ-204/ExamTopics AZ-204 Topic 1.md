#az-204-exam-practice

1. You are implementing a software as a service (SaaS) ASP.NET Core web service that will run as an Azure Web App. The web service will use an on-premises  
SQL Server database for storage. The web service also includes a WebJob that processes data updates. Four customers will use the web service.  
✑ Each instance of the WebJob processes data for a single customer and must run as a singleton instance.  
✑ Each deployment must be tested by using deployment slots prior to serving production data.  
✑ Azure costs must be minimized.  
✑ Azure resources must be located in an isolated network.  
You need to configure the App Service plan for the Web App.  
How should you configure the App Service plan?

Answer:
Number of `VM instances`: 4
`Pricing tier`: Isolated

2. DRAG DROP
You are a developer for a software as a service (SaaS) company that uses an Azure Function to process orders. The Azure Function currently runs on an Azure  
Function app that is triggered by an Azure Storage queue.  
You are preparing to migrate the Azure Function to Kubernetes using Kubernetes-based Event Driven Autoscaling (KEDA).  
You need to configure Kubernetes Custom Resource Definitions (CRD) for the Azure Function.  
Which CRDs should you configure?

- Azure Function Code - `Deployment`
- Polling Interval - `ScaledObject`
- Azure Storage Connection String - `Secret`

3. HOT SPOT
You are creating a CLI script that creates an Azure web app and related services in Azure App Service. The web app uses the following variables:

![](https://www.examtopics.com/assets/media/exam-media/04204/0004400001.png)

You need to automatically deploy code from GitHub to the newly created web app.  
How should you complete the script?

```powershell
az group create --location westeurope --name myResourceGroup
az appservice plan create --name $webappname --g myResourceGroup --sku FREE
az webapp create--name $webappname --g myResourceGroup --plan $webappname 
az webapp deployment source config --name $webappname --g myResourceGroup --repo-url $gitrepo --branch master --manual-integration
```

4. 
You develop a software as a service (SaaS) offering to manage photographs. Users upload photos to a web service which then stores the photos in Azure  
Storage Blob storage. The storage account type is General-purpose V2.  
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.  
You need to design the process that starts the photo processing.  
Solution: Trigger the photo processing from Blob storage events.  
Does the solution meet the goal?

Answer: `No`

