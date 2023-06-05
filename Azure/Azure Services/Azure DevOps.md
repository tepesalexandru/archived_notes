---
title: "Azure DevOps"
---
DevOps combines the world of 2 kind of professionals: the "dev" side, e.g. software developer and the "OPS" side operations, people who monitor the software and make sure that everything runs smoothly.

The four key principles of DevOps are the following:
- Automation of the software development lifecycle
- Collaboration and communication
- Continuous improvement and testing
- Focus on user needs with short feedback loops

---

Azure DevOps Services is a suite of services that address every stage of the software development lifecycle.
- Azure Repos is a one-place source-code repository where sofftware development code and documentation are stored to work upon, for review and collaboration.
- Azure Boards is an agile project management suite that includes Kanban boards, reporting, and tracking progress and work from high-level scenarios, and deliverables to work items and bugs
- Azure Pipelines is a Continuous Integration / Continuous Deployment pipeline automation tool that helps in smoothly running daily repetitive tasks.
- Azure Artifacts is a repository for hosting artifacts, such as compiled source code.
- Azure Test Plans is an automated test tool that can be used in a CI/CD pipeline to ensure quality before a software release.

---

#### Date: 19.05.2022
Inside of Azure DevOps, you can use the Wiki section to store information about the project. 

Everyone in the project can view the wiki, even stakeholders. But only people from the "Contributors" group can actually edit the wiki.

People who use IT Service Management Connector (ITSMC) for Azure can also connect to things such as Azure Alerts, Near Real-Time metric alert and Log Analytics alerts.

You can configure Work Items directly from inside the Application Insights blade. This is useful when you want to create a work item in the board whenever something goes wrong with the App Service as an example.

---

WhiteSource is an extension available in the Azure DevOps marketplace. It helps addressing Secure DevOps security-related issues in the CI/CD pipeline. 

WhiteSource Bolt is used to assess open-source security and licensing compliance.

Other tools also exist, such as GitHub Dependabot, which helps detect vulnerabilities in your package dependencies.

GitHub Dependabot will detect new vulnerabilities whenever they are added to the GitHub Advisory database.

The term "software composition analysis" is best described as: Analyzing open-source software (OSS) to identify potential security vulnerabilities and provide validation that the software meets a defined criterion to use in your pipeline.

---

#### Date: 13.06.2022
3. You are making use of Azure DevOps manage build pipelines, and also deploy pipelines.  
The development team is quite large, and is regularly added to.  
You have been informed that the management of users and licenses must be automated when it can be.  
Which of the following is a task that can't be automated?

Answer: `License procurement`

---

4. You have been tasked with strengthening the security of your team's development process.  
You need to suggest a security tool type for the Continuous Integration (CI) phase of the development process.  
Which of the following is the option you would suggest?

Answer: `Static Code Analysis`

5. Your company is currently making use of Team Foundation Server 2013 (TFS 2013), but intend to migrate to Azure DevOps.  
You have been tasked with supplying a migration approach that allows for the preservation of Team Foundation Version Control changesets dates, as well as the changes dates of work items revisions. The approach should also allow for the migration of all TFS artifacts, while keeping migration effort to a minimum.  
You have suggested upgrading TFS to the most recent RTW release.  
Which of the following should also be suggested?

Answer: `Using the TFS Database Import Service to perform the upgrade.`

7. You are currently developing a project for a client that will be managing work items via Azure DevOps.  
You want to make sure that the work item process you use for the client allows for requirements, change requests, risks, and reviews to be tracked.  
Which of the following is the option you would choose?

Answer: `The Capability Maturity Model Integration (CMMI)`

---

When moving to Azure DevOps, JIRA must be replaced with the `Azure Boards` Azure DevOps service.

[[Workflow States]]
