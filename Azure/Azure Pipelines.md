#azure 

Azure Pipeline is one of the core features inside of Azure DevOps. It's a Continuous Integration / Continuous Deployment tool in order to automatically build in your projects and deploy them to the cloud, for example to an Azure App Service.

There are two types of pipelines in Azure Pipelines:
- Build Pipelines - used to bundle together your project into a deployable artifact
- Release Pipelines - used to deploy the built artifact to the cloud

Pipelines can also be automated with triggers. For example, a build pipeline can run every time a commit is made to the main branch.

## Deployment Automation
A deployment is required every time the application is installed in an environment for testing, but the most critical moment for deployment automation is rollout time.

Since the preceding stages have verified the overall quality of the system, it's a low-risk step.

The deployment can be staged, with the new version being initially released to a subset of the production environment and monitored before being rolled out.

The deployment is automated, allowing for the reliability delivery of new functionality to users within minutes if needed.

## What is Azure Pipelines?
Azure Pipelines is a cloud service that automatically builds and tests your code project and makes it available to other users. It works with any language or project type.

Azure Pipelines combines continuous integration (CI) with continuous delivery (CD) to test and build your code and shit it to your target audience constantly and consistently.

## Key Terms
Understanding the basic terms and parts of Azure Pipelines helps you further explore how it can help you deliver better code more efficiently and reliably.

### Agent
When your build or deployment runs, the system begins one or more jobs. An agent is an installable software that runs a build or deployment job.

### Artifcat
An artifact is a collection of files or packages published by a build. Artifacts are made available for the tasks, such as distribution or deployment.

### Build
A build represents one execution of a pipeline. It collects the logs associated with running the steps and the test results.

### Continuous Delivery (CD)
CD is a process by which code is built, tested, and deployed to one or more test and production stages.

### Continuous Integration (CI)
CI is the practice used by development teams to simplify the testing and building of code. It helps catch bugs or problems early in the development cycle, making them more accessible and faster to fix. Automated tests and builds are run as part of the CI process. The process can run on a schedule, whenever code is pushed, or both. Items known as artifacts, mentioned previously, are produced in the CI process. The CD release pipeline use them to drive automatic deployments.

### Deployment Target
A deployment target is a virtual machine, container, web app, or any service to host the developed application. A pipeline might deploy the app to one or more deployment targets after the build is completed and tests are run.

### Job
A build contains one or more jobs. Jobs run on agents. A job represents an execution boundary of a set of steps. All the steps run together on the same agent.

### Pipeline
A pipeline defines the CI/CD process of your app. It's made of steps called tasks. It can be thought of as a script that describes how your test, build, and deployment are run.

### Release
A release is a term used to describe one execution of a release pipeline. It's made up of deployments to multiple stages.

### Stage
Stages are the primary division in a pipeline: "build the app", "run integration tests", "deploy to UAT (user acceptance testing)" are good examples of stages.

### Task
A task is the building block of a pipeline

### Trigger
A trigger is set up to tell the pipeline when to run. You can configure a pipeline to run upon a push to a repository at scheduled times or upon completing another build. All these actions are known as triggers.
