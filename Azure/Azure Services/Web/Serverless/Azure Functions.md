#azure #az-204 

Azure Functions lets you develop `serverless` applications on Microsoft Azure. You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.

## Hosting Plan
When you create a function app in Azure, you must choose a hosting plan for your app. There are three main options for this:
- Consumption Plan
- Premium Plan
- Dedicated Plan

There are also two extra ones, which provide the highest amount of control and isolation in which to run your function apps:
- ASE (App Service Environment)
- Kubernetes

On any plan, a function app requires a general `Azure Storage` account, which supports Azure Blob, Queue, Files, and Table Storage.

## Development
A function contains two important pieces - your code, which can be written in a variety of languages, and some config, the `function.json` file.

For compiled languages, the config file is generated automatically from annotations in your code. For scripting languages, you must provide the config file yourself.

Below is an example of a `function.json` file:

```json
{
    "disabled":false,
    "bindings":[
        // ... bindings here
        {
            "type": "bindingType",
            "direction": "in",
            "name": "myParamName",
            // ... more depending on binding
        }
    ]
}
```

The `function.json` file defines the function's trigger, bindings, and other configuration settings. Every function has one and only one trigger.

The `bindings` property is where you configure both triggers and bindings. Each binding shares a few common settings and some settings which are specific to a particular type of binding. Every binding requires the following settings:

- type - name of the binder
- direction - can be `in` or `out`
- name - the name that is used for the bound data in the function

---

Azure Functions supports `triggers`, which are ways to start execution of your code, and `bindings`, which are ways to simplify coding for input and output data. There are other integration and automation services in Azure and they all can solve integration problems and automate business processes. They can all define input, actions, conditions, and ouput.

When you create a Function App in Azure, you must choose a hosting plan for your app. There are three basic hosting plans available for Azure Functions: Consumption plan, Functions Premium Plan, and App Service (dedicated) plan. All hosting plans are generally available (GA) on both Linux and Windows virtual machines.

The hosting plan you choose dictates the following behaviours:
- How your function app is scaled
- The resources available to each function app instance
- Support for advanced functionality, such as Azure Virtual Network connectivity.

The following is a summary of the benefits of the three main hosting plans for functions:
- Consumption: The default hosting plan. It scales automatically and you only pay for compute resources when your functions are running.
- Premium: Same as consumption plan, with the added benefit of pre-warming functions, therefore removing any possible cold-starts. It can also connect to an Azure Virtual Network.
- Dedicated: Run your functions within an App Service plan at regular App Service plan rates. Best used when durable functions can't be used.

On any plan, a Function App requires a general Azure Storage account. This is because Functions rely on Azure Storage for operations such as managing triggers and logging function executions. The same storage account used by your function app can also be used by your triggers and binding to store your application data.

