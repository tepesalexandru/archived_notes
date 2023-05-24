#networking 

A **network topology** describes the physical composition of a network. There are four of them:
1. Bus
2. Ring
3. Mesh
4. Star

### Bus Topology
In a **bus topology**, each network device is connected to a single network cable. Even though it's the simplest type of network to implement, it has limitations.

The first is the length of the main cable (bus). The longer it becomes, the higher the chance of signal dropout. This limitation constrains the physical layout of the network.

All devices have to be physically located near each other; for example, in the same room.

Finally, if there is a break in the bus cable, the whole network fails.

### Ring Topology
In a ring topology, each network device is connected to its neighbor to form a ring.

This form of network is more resilient than the bus topology. A break in the cable ring also affects the performance of the network.

### Mesh Topology
The mesh topology is described as either a **physical mesh** or a **logical mesh**.

In a **physical mesh**, each network device connects to every other network device in the network. This dramatically increases the resiliency of the network, but has the physical overhead of connecting all devices.

There's a subtle difference between a physical mesh and a logical one. 

The perception is that most modern networks are mesh based, but since each device can see and communicate with any other device on the network. This describes a **logical mesh** network, and is primarily made possible through the use of network protocols.

### Star Topology
The **star topology** is the most commonly used network topology. Each network device connects to a centralized hub or switch. Switches and hubs can be linked together to extend and build more extensive networks. This type of topology is, by far, the most robust and scalable.