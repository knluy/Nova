## Switch
**Definition:**
>A network switch connects devices within a network (often a local area network, or LAN) and forwards data packets to and from those devices. Unlike a router, a switch only sends data to the single device it is intended for (which may be another switch, a router, or a user's computer), not to networks of multiple devices.
>
>Source: https://www.cloudflare.com/learning/network-layer/what-is-a-network-switch/

### Differences between a switch and a router

[[Router | Routers]] select paths for data packets to cross networks and reach their destinations. Routers do this by connecting with different networks and forwarding data from network to network — including [[LAN]]s, wide area networks ([[WAN | WANs]]), or autonomous systems, which are the large networks that make up the [[Internet]].

>![[network switch.PNG]]
>*_A local area network (LAN) is a group of connected devices within close physical proximity. Home WiFi networks are one common example of a LAN._*

In practice, what this means is that routers are necessary for an Internet connection, while [[Switch | Switches]] are only used for interconnecting devices. Homes and small offices need routers for Internet access, but most do not need a network switch, unless they require a large amount of Ethernet* ports. However, large offices, networks, and data centers with dozens or hundreds of computers usually do require switches.

>![[cisco switch.jpg]]
>*Cisco Switch*

### Layer 2 & 3 Switches

Network switches can operate at either [[OSI Model | OSI]] [[Layer 2 Switch | Layer 2]] (the data link layer) or [[Layer 3 Switch | Layer 3]] (the network layer). Layer 2 switches forward data based on the destination MAC address (see below for definition), while layer 3 switches forward data based on the destination IP address. Some switches can do both.

Most switches, however, are layer 2 switches. Layer 2 switches most often connect to the devices in their networks using Ethernet cables. Ethernet cables are physical cables that plug into devices via Ethernet ports.

### Types of Switches

- [[Layer 2 Switch]] - used for traditional LAN setup
- [[Layer 3 Switch]]- uses [[SVI]] technology to route VLANS in a network

---
tags: #ccna #switch #routing
links: https://www.cloudflare.com/learning/network-layer/what-is-a-network-switch/
https://en.wikipedia.org/wiki/Network_switch
https://www.networkworld.com/article/3584876/what-is-a-network-switch-and-how-does-it-work.html
see also: [[BVI]], [[Router on a Stick]], [[Broadcast and Collision]]
created on: 2021-12-17 11:09