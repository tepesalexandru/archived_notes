---
title: "Desired State Configuration"
---
#### Date: 14.05.2022
Desired State Configuration or DSC for short is a configuration management approach that you can use for configuration, deployment, and management of systems to ensure that an environment is maintained in a state that you specify (the *defined state*) and doesn't deviate from that state.

DSC also helps eliminate configuration drift.

DSC mainly consists of three primary parts:
- Configurations
- Resources
- Local Configuration Manager (LCM)

There are two methods of implementing DSC:
- Push mode
- Pull mode

Azure Automation State configuration DSC is available as part of [[Azure Automation]].

DSC configurations are just Windows Powershell scripts that define a special type of function. Here is an example of such as script:

```Powershell
configuration LabConfig
    {
        Node WebServer
        {
            WindowsFeature IIS
            {
                Ensure = 'Present'
                Name = 'Web-Server'
                IncludeAllSubFeature = $true
            }
        }
    }
```

And another example:

```Powershell
Configuration MyDscConfiguration
    {
        param
        (
            [string[]]$ComputerName='localhost'
        )
   
        Node $ComputerName
        {
            WindowsFeature MyFeatureInstance
            {
                Ensure = 'Present'
                Name = 'RSAT'
            }
   
            WindowsFeature My2ndFeatureInstance
            {
                Ensure = 'Present'
                Name = 'Bitlocker'
            }
        }
    }
   
    MyDscConfiguration
```

Azure also offers Hybrid Runbook Worker as part of Azure Automation, which allows you to run runbooks that manage local resources in your private data center.