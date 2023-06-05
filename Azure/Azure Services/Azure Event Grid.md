#azure #az-204 

Azure Event Grid is deeply integrated with Azure services and can be integrated with third-party services. It simplifies event consumption and lowers costs by eliminating the need for constant polling. Event Grid efficiently and reliably routes events from Azure and non-Azure resources, and distributes the events to registered subscriber endpoints.

Azure Event Grid enables event-driven, reactive programming. It uses a publish-subscribe model. Publishers emit events, but have no expectation about how the events are handled. Subscribers decide on which events they want to handle.

Event Grid allows you to easily build applications with event-based architectures. Event Grid has built-in support for events coming from Azure services, like storage blobs and resource groups. Event Grid also has support for your own events, using custom topics.

You can use filters to route specific events to different endpoints, multicast to multiple endpoints, and make sure your events are reliably delivered.

There are five concepts in Azure Event Grid that you need to understand in order to get started:
- Event - What happens
- Event sources - Where that event took place
- Topics - The endpoint where publishers send events
- Event subscriptions - The endpoint or built-in mechanicsm to route events, sometimes to more than one handler
- Event handlers - The app or service reacting to the event

Azure Event Grid provides durable delivery. It tries to deliver each event at least once for each matching subscription immediately. If the delivery fails, Event Grid will retry again based on a fixed retry schedule and retry policy. By default, Event Grid will retry to send the event a maximum of 30 times until its successful.

When creating an event subscription, you have three options for filtering:
- Event types
- Subject begins or ends with
- Advanced fields and operators

Event type filtering refers to what type of event you want to be subscribed to, for example, you may want to receive events from changes in a resource group, but only updates to the resources, not also deletes.

```json
"filter": {
  "includedEventTypes": [
    "Microsoft.Resources.ResourceWriteFailure",
    "Microsoft.Resources.ResourceWriteSuccess"
  ]
}
```

Subject filtering refers to being able to subscribe to an event based on its name, if it either begins or ends with a certain string. An example here would be subscribing to an Azure Storage Account, and only receiving events of files ending with ".jpg":

```json
"filter": {
  "subjectEndsWith": ".jpg"
}
```

The last type is the advanced filtering, used in case you need to apply extra logic to the event at hand. Here, you can specify extra logic, such as:
- operator type - the type of comparison
- key - the field in the event data that you're using for filtering
- value or values - the value or values to compare to the key

Example:

```json
"filter": {
  "advancedFilters": [
    {
      "operatorType": "NumberGreaterThanOrEquals",
      "key": "Data.ImageSizeKb",
      "value": 2048
    },
  ]
}
```

