#azure #docker 

Azure Container Registry (ACR) is a managed, private [[Docker]] registry service based on the open-source Docker Registry 2.0. 

Create and maintain Azure container registries to store and manage your private Docker container images.

You can use Azure Container Registry with your existing container development and deployment pipelines, or use Azure Container Registry Tasks to build container images in Azure. These builds can either be on demand, or fully automated based on triggers such as source code commits or base image updates.

### Use Cases
ACR is often used in two scenarios:
- Scalable orchestration systems that managed containerized applications across clusters of hosts, including [[Kubernetes]], DC/OS, and [[Docker Swarm]].
- Azure services that support building and running applications at scale, such as [[Azure Kubernetes Service]], [[Azure App Service]], Batch, Service Fabric, and others.

You can use ACR as target container when using a CI/CD tool such as Azure Pipelines.

---

Azure Container Registry handles private Docker container images as well as related content formats, such as Helm charts, OCI artifacts, and images built to the OCI image format specification.

You can streamline the process of building, testing, pushing, and deploying images to Azure with Azure Container Registry Tasks.

You can enable a single registry to serve users and hosts wherever they are, with multi-master geo-replication. Synchronize an artifact across all replicas by pushing it to any one replica. Speed up deployment by using regionalized webhooks to receive notifications when a local pull becomes available.

An Azure Container Registry stores and manages private container images and other artifacts, similar to the way Docker Hub stores public Docker container images.

Every pricing plan for Azure Container Registry (Basic, Standard, and Premium) benefits from advanced Azure Storage features including encryption-at-rest. Azure automatically encrypts an image before storing it, and decrypts it on-the-fly when you or your application and services pull the image.

## What is ACR Tasks?
ACR Tasks is a suite of featuer within Azure Container Registry. It provides cloud-based container image building for platforms including Linux, Windows, and ARM, and can automat OS and framework patching for your Docker containers.

### Quick Task
Before you commit your first line of code, ACR Tasks' `quick task` feature can provide an integrated development experience by offloading your container image builds to Azure. With quick tasks, you can verify your automated build definitions and catch potential problems prior to commiting your code.

### Automate OS and framework patching
The power of ACR Tasks to truly enhance your container build workflow comes from its ability to detect an update to a `base image`. 

A feature of most container images, a `base image` is a parent image on which one or more application images are based. Base images typically contain the operating system, and sometimes application frameworks.

### Multi-step Tasks
Multi-step tasks provide step-based task definition and execution for building, testing, and patching container images in the cloud. Task steps are defined in a `YAML` file and specify individual build and push operations for container images or other artifacts.

For example, you can create a multi-step task that automates the following:
1. Build a web application image
2. Run the web application container
3. Build a web application test image
4. Run the web application test container, which performs tests against the runing application container
5. If the tests pass, build a Helm chart archive package
6. Perform a `helm upgrade` using the new Helm chart archive package

Multi-step tasks enable you to split the building, running, and testing of an image into more composable steps, with inter-step dependency support.