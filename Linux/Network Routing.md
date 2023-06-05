`Routing` is selecting the path for the traffic in a network or across multiple networks. Network traffic is the amount of data moving across a computer network at a given time. It's broken down into `data packets`.

A `router` is a networking device that forwards data packets between networks.

For example, your broadband router provides Internet access by connecting your local area network (LAN, i.e. the devices in your house) with the Internet.

When a packet gets to a router, it looks at the destination IP address of the packet and works out where to route it to using a `routing table`.

A `routing table` is a set of rules that works out where data packets travelling over the Internet Protocol (IP) network will be directed. The routing table tells the router where to send the packet for its next hop along the network.

What does a routing table have in it?
- A network ID and the subnet mask - This specifies a range of IP addresses of the destination of the packet.
- The next hop or Gateway - This is the address of the next station where the packet should go on the way to its destination
- The outgoing interface - This is where the packet should leave from to reac the gateway
- A metric - This indicates the cost of using the route (the higher the number, the less efficient)
