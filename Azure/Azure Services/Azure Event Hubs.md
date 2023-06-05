#azure #az-204 

In short, Azure Event Hub is a big data streaming platform which can receive and process millions of events per second.

It has the following characteristics:
- Partitioned - to support highly-available data sending and parallel readers. Order of data is preserved within each partition.
- Reliable - agnostic to failures, zero data loss and low latency
- Decouples system to process the data - Event Hub sits between event publishers and event consumers to decouple the production of an event stream from the consumption of those events
- Real time data processing - ability to ingest, buffer, store, and process data streams in real time for time-critical decision making

There are a few key concepts to understand in Event Hubs:
![](https://miro.medium.com/max/1400/1*qi6ikZubQ16hpD8nVD-sNw.png)

- Event Producers - any entity that sends event data to an event hub
- Event Receivers - any entity that reads event data from an event hub. 
- Partitions - each consumer only reads a specific subset, or partition of the message stgream. Partition count has to be defined at the creation of the event hub and cannot be modified later
- Consumer group - A specific view of an entire event hub. Receivers can have their own separate view of the event stream. They read the stream independently at their own pace with their own offsets. Hence this allows for consumers to scale independently to meet the requirements.

---

When using Azure Event Hub, you can use the "event hubs capture" feature to persist the events in Blob Service, using the "Apache Avro" format for the files.

---

Data is valuable only when there's an easy way to process and get timely insights from data sources. Event Hubs provides a distributed stream processing platform with low latency and seamless integration, with data and analytics services inside and outside Azure to build your complete big data pipeline.

Event Hubs represents the "front door" for an event pipeline, often called an `event ingestor` in solution architectures.

An `event ingestor` is a component or service that sits between event publishers and event consumers to decouple the production of an event stream from the consumption of those events. 

Event Hubs provides a unified streaming platform with time retention buffer, decoupling event producers from event consumers.

---

An Event Hubs `namespace` is a managed container for event hubs (or topics, in Kafka parlace). It provides DNS-integrated network endpoints and a range of access control and network integration management features such as IP filtering, virtual network service endpoint, and Private Link.

---

Azure Event Hubs `Capture` enables you to automatically deliver the streaming data in Event Hubs to an Azure Blob Storage or Azure Data Lake Storage Gen1 or Gen 2 account of your choice.

---

The pricing tiers for Azure Event Hubs are the following:
- Basic
- Standard
- Premium
- Dedicated

---

Example use-case scenario:

A home security company that monitors 100,000 homes. Each home has a variety of sensors - such as motion-detectors, door/window open sensors, and glass break detectors. These devices report back to a common server, which logs events, sounds an alarm if a threshold number of events occurs, and allows customers to monitor their home from a user-friendly web-page.

This sytem could be implemented with direct communication between devices and the server, though the server may be prone to overloading at certain times of day and any downtime can result in lost sensor messages.

A direct integration may also lead to non-modular design that impedes future attempts to improve the platform.

continue learning: https://docs.microsoft.com/en-us/learn/modules/intro-to-event-hubs/2-what-is-event-hubs