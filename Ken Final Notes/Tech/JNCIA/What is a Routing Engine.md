# Routing Engine

**Definition:**
>The Routing Engine in a Juniper Networks router is the ==**central location**== for control of the system. This is where the intelligence of the router operates. You perform software upgrades and maintenance on the Routing Engine. In addition, you interface with the Routing Engine for monitoring and configuring the router.

## General Functions

Your experience with a Juniper Networks router begins with the Routing Engine. After connecting to the router, you supply authentication information (name and password) to the Routing Engine. After you’re authenticated, you perform management and configuration operations within the Routing Engine. Troubleshooting tools like Telnet, ping, or traceroute operate from within the Routing Engine as well. 

Since control of the router occurs in the Routing Engine, this is the logical location to store the JUNOS software. As such, the Routing Engine operates all routing protocols and makes all routing table decisions, building a master routing table with the best path to each destination selected. The router then places these best paths into the forwarding table on the Routing Engine and copies that same data into the forwarding table on the Packet Forwarding Engine. The forwarding table on the Packet Forwarding Engine allows the router to actually forward user data packets.

## Physical Composition

- Each Routing Engine is based on an Intel PCI motherboard. 
- The actual components of each Routing Engine depend on the model you are using and include the following
	- Routing Engine 2
	- Routing Engine 3 


Notes:
> The hardware in a Juniper Networks Routing Engine is generally composed of the most common components available at its time of construction. As the cost of hardware decreases over time, you can expect that newer versions of the Routing Engine will contain more powerful hardware. Regardless, the requirements of the router design allow the Routing Engine to function quite well using the hardware described here


---
tags: #juniper
links: JNCIA.pdf#page=37
