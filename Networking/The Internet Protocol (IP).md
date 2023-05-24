#networking 

The IP is the protocol responsible for the logical addressing of a host, enabling the packet to be sent from one host to another.

For this each device on the network is assigned a unique IP address, and it is possible to assign more than one address to the same device.

In the version 4 of the Internet Protocol, usually called **IPv4**, the address is formed by a set of 32 bits separated into 4 groups of 8 bits, represented in a decimal form, called **dotted quad**.

> [!INFO]
> Example of an IPv4 Address
> 
> 11000000.10101000.00001010.00010100 (Binary Format)
> 192.168.10.20 (Decimal Format)

In IPv4, the values for each octet can range from 0 to 255, which is the equivalent of 11111111 in binary format (the maximul value).

### Public and Private IPs
If every device connected to the Internet in the world had a unique IP address, there would not be enough IPv4 addresses for everyone. For this, **Private IP** addresses were defined.

Private IPs are ranges of IP addresses that have been resereved for use in the internal (private) networks of companies, institutions, homes, etc. Within the same network, the use of an IP address remains unique. However, the same private IP address can be used within any private network.

Thus, on the Internet we have data traffic using public IP addresses, which are recognizable and routed over the Internet, while within private networks these reserved IP ranges are used. 

> [!INFO]
> The **router** is responsible for converting traffic from private network to the public network and vice versa. 

https://learning.lpi.org/en/learning-materials/102-500/109/109.1/109.1_01/