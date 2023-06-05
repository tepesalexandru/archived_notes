---
title: "Azure App Configuration"
#article 
---
### Introduction

Azure App Configuration is a `centralized` store all your application settings and secure their access in one place. Benefits of Azure App Configuration are:
- A fully managed service that can be set up in minutes
- Flexible key representations and mappings
- Tagging with labels
- Point-in-time replay of settings
- Dedicated UI for feature flag management
- Comparison of two sets of configurations on custom-defined dimensions
- Enhanced security through Azure-managed identities
- Complete data encryptions, at rest or in transit
- Native integration with popular frameworks

Azure App Configuration completes [[Azure Key Vault]], which is used to store application secrets. App Configuration makes it easier to implement the following scenarios:
- Centralize management and distribution of hierarchical configuration data for different environments and geographies
- Dynamically change application settings without the need to redeploy or restart the application
- Control feature availability in real-time

### Create Paired keys and values
Azure App Configuration stores configuration data as `key-value pairs`.

`Keys` serve as the "name" for key-value pairs and are used to `store` and `retrieve` corresponsing values.

It's a common practice to organize keys into a hierarchical namespace by using a character delimited, such as `/` or `:`. However, keep in mind that App Configuration treats your keys as a whole, it doesn't parse them in order to understand the hierarchy.

Key names are case sensitive. You can use any characters expect `*`, `,` and `\`. The name and the value of the key must be less than 10,000 characters (combined).

An example of hierarchical keys are the following:

```
AppName:Region1:DbEndpoint
AppName:Region2:DbEndpoint
```

### Label keys
Key values in App Configuration can optionally have a label attribute. Labels are used to differentiate key values with the same key. 

Ex: A key named "app1" with labels `A` and `B` forms two separate keys in an App Configuration store. By default, the label for a key value is empty, or `null`.

Labels provide a convenient way to create variants of a key. A common use of labels is to specify multiple environments for the same key:

```
Key = AppName:DbEndpoint & Label = Test
Key = AppName:DbEndpoint & Label = Staging
Key = AppName:DbEndpoint & Label = Production
```

### Version key values
App Configuration doesn't version key values automatically as they're modified. Use different labels in order to keep track of versions.

### Query key values
Each key is identified by its key plus a label that can be `null`. When you query an App Configuration store, you specify a pattern, and the store returns all keys that match that pattern.

### Values
Values assigned to keys are also unicode strings, and you can use all unicode characters.

Note: Azure App Configuration isn't a replacement for Azure Key Vault, don't store application secrets in it.

---
### Security

Azure App Configuration uses 256-bit AES encryption for data at rest.

---

### Feature flags
A `Filter` evaluates the state of a feature flag.
