#azure 

Resource locks are a powerful mechanism to protect your resources from unauthorized opreations. For example, you can lock your storage account to prevent files and directories from being deleted.

It is advisable to clearly define your "lock strategy" on resource groups as well as at a resource level, to benefit from this feature from the moment you provision resources.

Powershell commands:

- Remove lock by name

```shell
Remove-AzResourceLock
	-LockName '{}'
	-ResourceName '{}'
	-ResourceGroupName '{}'
	-ResourceType '{}'
	-Force	
```

- Remove lock by id

```shell
Remove-AzResourceLock 
	-LockId '{}' 
	-Force
```

- Fetch all lock ids

```shell
Get-AzResourceLock 
	-ResourceGroupName '{}' 
	-ResourceType '{}'
	-ResourceName '{}'
```

- Add "CanNotDelete" lock

```shell
New-AzResourceLock 
	-LockName '{}' 
	-ResourceName '{}' 
	-ResourceGroupName '{}' 
	-ResourceType '{}' 
	-LockLevel "CanNotDelete" 
	-Force
```
