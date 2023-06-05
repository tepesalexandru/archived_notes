#az-204-exam-practice 

T1.2: You publish a custom docker imagine onto the Azure Web App. You need to access the console logs generated from the container in real time.

You can use the following CLI commands in order to do so:

```bash
az webapp log config 
	--name whizlabwebapp 
	--g whizlab-rg 
	--docker-container-logging filesystem

az webapp log tail
	--name whizlabwebapp
	--g whizlab-rg
```


In general, when you need to configure "logging" for a Web App you will use the command

```bash
az webapp log config
```

T1.4 You are retrieving information from Microsoft Graph. Which query parameter combinations would return only the display name with the last name 'Bob'?

```bash
?$filter=surname eq 'Bob' & $select=displayName
```

Because `$filter` returns the results with a specific condition and `$select` gets only the selected property when retrieving the response.

T1.7 You need an `Integration Service Environment` to secure the Logic App.

An integration service environment is a fully isolated and dedicated environment for all enterprise-scale integration needs.

T1.9 Which of the following are suitable scenarios to use `Cache-Aside` pattern?
- Native read-through and write-through cache operations are not provided
- Unpredictable resource demand

---

