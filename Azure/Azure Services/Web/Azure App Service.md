#azure #az-204 #app-service 

Azure App Service is an HTTP-based service for hosting web applications, REST APIs, and mobile backends.

## App Service Plan
When using Azure App Service, an app (Web App, API, or Mobile App) always run in an `App Service Plan`.

There is a special plan only used for Function Apps (serverless), called `consumption` plan.

## CI/CD
App Service also supports automated deployment, or continuous integration, using services such as: Azure DevOps, GitHub and Bitbucket.

## Authentication / Authorization
App Service also provides built in `authentication and authorization`.

## Networking
You can find all outbound IPs of you app in the Azure Portal or by using the CLI with the followign command:

```bash
az webapp show \
    --resource-group <group_name> \ 
    --name <app_name> \ 
    --query possibleOutboundIpAddresses \
    --output tsv
```

You can use the `hybrid connections` network feature of an App Service in order to control outbound network traffic.

## Configuration
### Environment Variables
In App Service, app settings are variables passed as environment variables to the application code.

For ASP.NET / ASP.NET Core developers, the values you set in App Service override the ones in `web.config`.

## Logging
There are built-in diagnostics to assist with debugging an App Service app.

However, on Linux only Deployment Logging is supported.

## Security
### Certificates
Azure App Service supports operations in order to create, upload, or import a `private certificate` or a `public certificate`.

### HTTPs
By default, anyone can still access your app using HTTP. You can redirect all your HTTP requests to the HTTPS port by navigating to your app page and enabling the `HTTPS Only` settings from the `TLS/SSL settings` page.

## Feature Management
App Service allows you to define and use several feature management techniques such as `feature flags`. Each feature flag must have a `name` and `one or more filters`.

## Scaling
[[Azure App Service Autoscaling]]

## Deployment Slots
The deployment slot functionality in App Service is a powerful tool that enables you to preview, manage, test, and deploy your different development environments.

Deployment slots also allow for the operation to `swap slots`. (ex: staging slot to the production slot). Doing so provides zero downtime.

You can manually swap deployment slots in the Overview page of the App Service.

Azure also offers a bonus feature, called `swap with preview` (or multi-phase swap).
In a swap with preview, you can validate that the app runs with the swapped settings before completing the swap.

You can also configre `auto swap` in order to streamline an Azure DevOps process.

## Routing
By default, all client requests to the app's production URL are routed to the production slot. You can route a portion of the traffic to another slot.

By default, the amount of traffic applied to a new deployment slot is `0%`.