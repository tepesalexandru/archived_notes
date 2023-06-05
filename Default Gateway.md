#networking  #linux 

A default gateway is a node that enalbes a connection between networks in order to allow machines on other neetworks to communicate. The "*default*" part of the terminology relates to the fact it is often the first and default route taken.

One of the most common uses for a default gateway is to access web pages; a request is sent through the gateway before it actually gets onto the internet.

Other use cases of default gateways include connecting multiple devices to a single subnet. In that scenario, the default gateway acts as an intermediary.

You can find your default gateway's IP address on Linux by using the `netstat -nr | grep default`.