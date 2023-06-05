What is a network? A `network` is two or more computers that are linked together to share stuff or communicate. The computers on a network might be linked through physical cables, telephone lines, radio waves, etc.

A business might find a computer network useful to:
- allow staff to access files for sharing and modifying
- add security measures
- connecting to printers

Networks can be `public` or `private` and can be lots of different sizes.
Local Area Networks (`LANs`) are often used in offices. 
Virtual Private Networks (`VPNs`) are a way of accessing a private network using a public one.

Virtual networks are divided up into `subnets`. Subnets are good to improve security, increase performance and make the network easier to manage.

Subnets have a range of IP addresses that fall within the virtual network address space. The IP addresses of the different subnets can't overlap and should be specific using something called `Classless Inter-Domain Routing` (CIDR) notation.

Azure resources can be deployed to specific subnets.

`Internet Protocol` (IP) is the way data is sent from one computer to another on the internet.
Data traversing the internet is divided into smaller pieces, called `packets`. IP information is attached to each packet, and this information helps routers to send packets to the right place.

Every device or domain that connects to the Internet is assigned an IP address, and as packets are directed to the IP address attached to them, data arrives where it is needed.

There are two kinds of IP address, `IPv4` and `IPv6`. These are the internet protocol version 4 and 6. From what I gathered from a quick bit of research, version 6 is faster and better.

IP Addresses can be `static` (they do not change) or `dynamic` (they do change).
Static IP addresses would be good for:
- DNS name resolution (where IP addresses are translated to domain names for websites)
- TLS/SSL certificates linked to an IP address
- Firewall rules that allow or deny traffic using IP address ranges

---

Also explore [[Network Routing]].