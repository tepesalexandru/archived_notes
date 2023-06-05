#azure #az-204 

Auzre supports two types of queue mechanisms: `Service Bus queues` and `Storage queues`.

Azure Service Bus is a fully managed enterprise integration message broker. Service Bus can decouple applications and services. Data is transferred between applications and services using `messages`.

A `message` is a container decorated with metadata, and contains data. The data can by any kind of information, includting structured data encoded with the common formats such as JSON, XML, Apache Avro or Plain Text.

The core entities that make up Service Bus are `queues`, `topics` and `subscriptions`, and rules / actions.

Queues offer a First In, First Out (FIFO) message delivery to one or more competing consumers. This enables applications to process messages in the order that they were received. Another benefit of using a queue, compared to a service such as Azure Event Grid, is that messages can be processed at the application's pace. The messages are stored in a queue in the cloud, so there is no hurry to process them all at once. Therefore, producers can send messages at a different rate (possibly higher) than the speed at which messages are processed by consumers.

Every consumer can receive a message in one of two ways:
- Receive and delete - after the consumer has received the message, it is deleted by Service Bus. This is the simplest way of building a queue, but it doesn't offer fault tolerance. In case your application receives a message, but crashes before it is processed, it will still be marked for deletion.
- Peek lock - after the consumer has received the message, it locks it so other applications cannot access it. After the application processes the message, it sends a new request to Service Bus to mark the message as consumed, and will be deleted from the queue. This is best used when your application cannot tolerate missing even a single message.

A queue allows processing of a message by a single consumer (the fastest that got hold of the message). In contrast to queues, topics and subscriptions allow a one-to-many relationship between publisher and consumer. Publishers can send messages to topics, and subscriptions make a copy of that message and send it to the subscribed service. Apart from that, it works identically to the process mentioned previously.

A great example application you can build using Azure Service Bus is a food delivery application. Whenever a customer makes an order, a new message with the order's information gets sent to an Azure Service Bus queue, allowing it to be processed. Then, a back-end service will process the message and display various details to the end user, such as the fact that the order has been received or that the food is on its way.