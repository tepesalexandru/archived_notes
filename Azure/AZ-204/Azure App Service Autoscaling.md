#azure #app-service

## Autoscaling
Autostacling enables a system to adjust the resource required to meet the varying demand from users, while controlling the costs associated with these resources. You can use autoscaling with many Azure services, including web applications.

Autoscaling requires you to configure `autoscale rules` that specify the conditions under which resources should be added or removed.

Autoscaling by metric requires that you define one or more autoscale rules. An autoscale rule specifies a metric to monitor, and how autoscaling should respond when this metric crosses a defined threshold. The metrics you can monitor for a web app are:
- CPU Percentage
- Memory Percentage
- Disk Queue Length
- Http Queue Length
- Data In
- Data Out

When an autoscale rule detects that a metric has crossed a threshold, it can perform an `autoscale action`. An autoscale action can be `scale-out` or `scale-in`.

A scale-out action increases the number of instances, and scale-in reduces the amount of instances.

In order to enable autoscaling, you need to enable the `Custom autoscale` setting for you App Service inside of the Azure Portal.

![](https://docs.microsoft.com/en-us/learn/wwl-azure/scale-apps-app-service/media/enable-autoscale.png)

After enabling this option, you can create `scale conditions` and `scale rules`:

![](https://docs.microsoft.com/en-us/learn/wwl-azure/scale-apps-app-service/media/autoscale-rules.png)

