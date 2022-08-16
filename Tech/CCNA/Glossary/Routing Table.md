## Routing Table

**Definition:**

>A routing table is a `set of rules`, often viewed in table format, that is used to determine where data packets traveling over an Internet Protocol (IP) network will be directed. All IP-enabled devices, including routers and switches, use routing tables.
>
>Source: [Routing Tables in Computer Network - GeeksforGeeks](https://www.geeksforgeeks.org/routing-tables-in-computer-network/#:~:text=A%20routing%20table%20is%20a%20set%20of%20rules%2C,devices%2C%20including%20routers%20and%20switches%2C%20use%20routing%20tables.)

Routing table:

![[routing table.PNG | 350]]

**Entries of an IP Routing Table:**

A routing table contains the information necessary to forward a packet along the `best path toward its destination`. Each packet contains `information about its origin and destination`. Routing Table provides the device with instructions for sending the packet to the next hop on its route across the network.

#### Routing Table Entries

1.  **Network ID:**  
    The network ID or destination corresponding to the route.
	
2.  **Subnet Mask:**  
    The mask that is used to match a destination IP address to the network ID.
	
3.  **Next Hop:**  
    The IP address to which the packet is forwarded
	
4.  **Outgoing Interface:**  
    Outgoing interface the packet should go out to reach the destination network.

5.  **Metric:**  
    A common use of the metric is to indicate the `minimum number of hops` (routers crossed) to the network ID.
	
---
tags: #ccna #ip #router
links: [Routing Tables in Computer Network - GeeksforGeeks](https://www.geeksforgeeks.org/routing-tables-in-computer-network/#:~:text=A%20routing%20table%20is%20a%20set%20of%20rules%2C,devices%2C%20including%20routers%20and%20switches%2C%20use%20routing%20tables.)
see also: [[Router]]
created on: 2021-12-17 11:06
	
	
	

