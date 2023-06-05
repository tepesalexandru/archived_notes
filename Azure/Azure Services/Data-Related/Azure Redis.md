#azure #az-204 

Redis is an open-source cache system that allows you to work "like-in" an in-memory data structure store, database cache or message broker.

Azure Redis Cache or Azure Cache for Redis is a Redis implementation managed by Microsoft.

Azure Redis Cache has three different pricing tiers:
- Basic - has no SLA, should only be used for testing or development
- Standard - offers 2 nodes, primary-secondary, with an SLA of 99.9%
- Premium - enterprise-grade Redis cluster managed by Microsoft. Has all the features and SLA of 99.9%, and also better hardware.

You can scale up your existing Redis Cache service but you cannot scale it down.

When working with Azure Redis Cache there are different implementation patterns that solve different issues, some of them being:

---

Azure Cache for Redis provides distributed, in-memory data store based on the Redis software for caching data.
- Its ability to process large volumes of application requests by keeping frequently accessed data in the server memory makes it a low-latency and high-throughput data storage for modern applications
- It provides secure and dedicated Redis server instances and full Redis API compatibility
- It allows replicating or syncing the cache in multiple regions in the world. One cache is primary, and other caches act as secondaries. The primary cache has read and write capabilities, but the secondary caches are read-only.
- Azure Cache for Redis offers both the Redis open-source (OSS Redis) and a commercial product from Redis Labs (Redid Enterprise) as a managed service.

Common Application use-cases:
- Static content cache - Using an in-memory cache provides quick access to static content like headers, footers, etc compared to backend datastores.
- Data Cache - quering large databases can be complex and time taking, keeping data in the cache while loading as needed and used can help effectively
- Session data - Like cookies, storing key-value data like users' associated information (shopping cart, personal info, etc.) provides faster loading time for websites.

---

#### Improve application throughput and latency
You can use Azure Cache for Redis to accelerate your data layer through caching. Adding Cache for Redis can increase data throughput by over 800% while increasing latency performance by over 1000% at a cost-effective price. It's a great way to efficiently scale applications and improve user experience without the expense of re-architecting your underlying database.

![](https://azurecomcdn.azureedge.net/cvt-7ca8746392da060c8c7ccdd8f3f176ebcb01259c478514039274c8084a8e749a/images/page/products/cache/latency.png)


#### Speed up applications with distributed cache
Complement database services like Azure SQL Database and Azure Cosmos DB by enabling your data tier to scale throughput at a lower cost than through expanded database instances. Store and share database query results, session states, and static content by using a common [[Cache-Aside]] pattern, and make your application more nimble and scalable.

![](https://azurecomcdn.azureedge.net/cvt-7ca8746392da060c8c7ccdd8f3f176ebcb01259c478514039274c8084a8e749a/images/page/products/cache/distributed-cache.png)

#### Efficiently store session data
Quickly save, retrieve, and update web `session data`, such as user cookies and output pages. Improve the performance of your application by increasing its responsiveness and enabling it to handle increasing loads with fewer web-compute resources. Take advantage of data persistance, and automatic data duplication for maximum user data reliability.

Scale out to terabyte size using `clustering` to meet the needs of even the largest enterprises and synchronize session data globally with `active geo-distribution`.

![](https://azurecomcdn.azureedge.net/cvt-7ca8746392da060c8c7ccdd8f3f176ebcb01259c478514039274c8084a8e749a/images/page/products/cache/session-store.png)

#### Communicate between services as a message broker
Use Azure Cache for Redis as a solution for implementing publish/subscribe or queue architectures. Route real-time messages and scale up web communication frameworks such as [[SignalR]]. Use industry-standard TLS encryption for data in transit, and configure proper network isolation with [[Azure Private Link]].

![](https://azurecomcdn.azureedge.net/cvt-7ca8746392da060c8c7ccdd8f3f176ebcb01259c478514039274c8084a8e749a/images/page/products/cache/message-broker.png)

#### What makes Azure Cache for Redis so fast?
Whilst most databases store data on slower, disk-based storage, Azure Cache for Redis stores data in memory. Since memory is significantly faster than disk storage, data can be written and retrieved much faster.