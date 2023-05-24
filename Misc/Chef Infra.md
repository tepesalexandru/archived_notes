---
title: "Chef Infra"
---
**Chef Infra** is an infrastructure automation tool used to deploy, configure, manage and ensure application and infrastructure compliance.

**Chef Infra** has 3 main architectual components:
- Chef Server
- Chef Client (node)
- Chef Workstation

You can deploy Chef on Azure from the Azure Marketplace using the Chef Automate image.

Chef uses **cookbooks** in order to define set of commands to execute on the managed client.

Here's an example of a Chef cookbooks:

```Ruby
powershell_script 'Install IIS' do

action :run

code 'add-windowsfeature Web-Server'

end

service 'w3svc' do

action [ :enable, :start ]

end

template 'c:\inetpub\wwwroot\Default.htm' do

source 'Default.htm.erb'

rights :read, 'Everyone'

end
```

**Knife** is a command that's available from the command line and is part of the Chef Development Kit. It allows you to complete a variety of tasks, such as uploading a cookbook to Chef Automate, here's an example:

```Ruby
Knife cookbook upload < cookbook name> --include-dependencies
```
