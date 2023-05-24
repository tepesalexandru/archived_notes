#networking 

There are several network standard-compliant devices that make up the structure of networks. These devices are:
1. Repeaters
3. Bridges
2. Hubs
4. Switches
5. Routers

### Repeater
A repeater is a two-port device that **repeats** networks signals.

Repeaters are used when network devices are some distance from each other. The repeater doesn't modify or interpret data packets before it resends them, and it doesn't amplify the signal.

Instead, it regenerates the data packaet at the original strength, bit by bit.

### Bridge
A bridge divices a network into network segments, and can filter and forward data packets between these segments.

> [!INFO]
> Bridges use the network device's MAC address to decide the data package's destination.

Typically, a bridge is used to improve network performance by reducing unnecessary network traffic on network segments.

### Hubs
A hub acts as a multiport repeater on a network.

Hubs are used to connect more than one device and structure the layout of a network.

For example, you can cascade hubs to create network branches, or as an endpoint to create a star layout with multiple-user-type devices.

### Switch
A switch combines the functionality of a bridge and a hub. It segments networks and can interpret and filter packet data to send it directly to an attached network device. 

> [!INFO]
> Switches use the network device's MAC address to decide the data package's destination (**just like bridges**).

### Router
Routers link networks with different ranged addresses together.

They can interpret and filter data packets, and then forward them to the correct network.

> [!INFO]
> Routers use the network device's IP address information to route the data package to its destination.

A router is also called a **gateway**.

When you configure network devices, you'll usually configure them with a default **gateway IP address**.

A router is responsible for converting traffic from the private network to the public network and vice versa.