## Ring Topology

**Definition:**
>A ring topology is a network configuration where device connections create a circular data path. Each networked device is ==connected to two others, like points on a circle==. Together, devices in a ring topology are referred to as a ring network.
>
>Source: https://www.computerhope.com/jargon/r/ringtopo.htm

In a ring network, packets of data travel from one device to the next until they reach their destination. Most ring topologies allow packets to travel only in one direction, called a unidirectional ring network. Others permit data to move in either direction, called bidirectional.

>![[ring topology.png]]
>*Sample of Ring Topology*


### Advantages
-   All data flows in one direction, reducing the chance of packet collisions.
-   A network server is not needed to control network connectivity between each workstation.
-   Data can transfer between workstations at high speeds.
-   Additional workstations can be added without impacting performance of the network.


### Disadvantages
-   All data being transferred over the network must pass through each workstation on the network, which can make it slower than a [[Star Topology]]

-   The entire network will be impacted if one workstation shuts down.

-   The hardware needed to connect each workstation to the network is more expensive than Ethernet cards and hubs/switches.

Ring topologies may be used in either LANs (local area networks) or WANs (wide area networks). Depending on the network card used in each computer of the ring topology, a coaxial cable or an RJ-45 network cable is used to connect computers together.

---
tags: #ccna #network #topology 
links: https://www.computerhope.com/jargon/r/ringtopo.htm
see also:
created on: 2021-12-22 13:11

