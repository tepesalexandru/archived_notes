#azure #az-204 

A content delivery network (CDN) is a distributed network of servers that can efficiently deliver web content to users. CDNs store cached content on `edge servers` in `point-of-presence` (POP) locations that are close to end users, to minimize latency.

The benefits of Azure CDN are:
- Better performance and improved user experience for end users, especially when using applications in which multiple round-trips are required to load content
- Laerge scaling to better handle instantaneous high loads, such as the start of a product launch event
- Distribution of user requests and serving of content directly from edge servers so that less traffic is sent to the origin server.

## How it works
![](https://docs.microsoft.com/en-us/learn/wwl-azure/develop-for-storage-cdns/media/azure-content-delivery-network.png)


1. A user requests a file by using a URL with a special domain name, such as `<endpoint-name>.azureedge.net`. The DNS routes the request to the best performing POP location, which is usually the POP that is geographically closest to the user.
2. If no edge servers in the POP have the file in their cache, the POP requests the file from the origin server. The origin server can be an Azure Web App, Azure Cloud Service, Azure Storage Account, or any publicly accessible web server.
3. The origin server returns the file to an edge server in the POP.
4. An edge server in the POP caches the file and returns the file to the original requestor. The file remains cached on the edge server in the POP until the time-to-live (TTL) specified by its HTTP headers expires. If the origin server didn't specify a TTL, the default TTL is seven days.
5. Additional users can then request the same file by using the same URL that Alice used, and can also be directed to the same POP.
6. If the TTL for the file hasn't expired, the POP edge server returns the file directly from the cache. This process results in a faster, more responsive user experience.

## Caching Behaviour
A cached resource can potentially be out-of-date or stale (compared to the corresponding resource on the origin server). For this reason, it's important to have in place a mechanism to control when content is refreshed.

The standard Microsoft Tier for Azure CDN provides three main ways of dealing with cached content:
- **Ignore query strings** - This is the default option. A CDN POP simply passes the request and any query strings directly to the origin server on the first request and caches the asset. New requests for the same asset will ignore any query strings until the TTL expires.
- **Bypass caching for query strings** - Each query request from the client is passed directly to the origin server with no caching.
- **Cache every unique URL** - Every time a requesting client generated a unique URL, that URL is passed back to the origin server with its own TTL. This final method is inefficient where each request is a unique URL, as the cache-hit ratio becomes low. 