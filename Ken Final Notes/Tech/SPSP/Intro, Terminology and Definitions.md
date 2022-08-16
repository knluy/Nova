## Intro, Terminology and Definitions

### SDWAN (Software Defined WAN)
- is not a standard
- Every vendor's implementation is proprietary
- SDWAN devices from different vendors will likely not work together to automate your WAN

### Architecture

**EdgeConnect Appliance** - Transports and optimizes traffic between sites in the network.

**Physical Appliance** — Hardware that comes with software loaded and a burned in serial number linked to an account. 
**Virtual Appliance** — Software appliance running in a hypervisor. No serial number - requires license info to link to account. 

**Orchestrator** — Manages, provisions and monitors the Silver Peak devices in a given network. 
- Must register with the Cloud Portal to manage EdgeConnect appliances. 
- Only one Orchestrator is normally used per organization 

**Cloud Portal** — Silver Peak's portal on the internet. 
- Manages licensing of Silver Peak devices in a network. 
- Talks to Orchestrator and EdgeConnect devices. 
- Knows all licenses and serial numbers of physical devices. 
- Facilitates initial connection between Orchestrator an Edge Connect devices.
- All devices must register with the Cloud Portal. 

>![[silverpeak sdwan architecture.PNG]]
>*Sample of SDWAN architecture*

### Encapsulation and Tunnels

**Tunnel** — a logical connection between two devices, in our case, two Silver Peak appliances. 
- Traffic transported through a tunnel is encapsulated. 
- The tunnel packets carry the source and destination addresses of the SilverPeak devices. 
- The payload packets they carry have the original source and destination addresses of the end devices. 

Note: A tunnel can carry other  tunnels inside it, adding a layer of encapsulation 

>![[sdwan tunnel.PNG]]

**Encapsulation** — placing a packet (e.g. from a PC or server etc.) inside another packet.
- The end device packet becomes the payload of the encapsulating packet.
- The end device packet is usually unaltered except to possibly be encrypted.

### Flow

**Flow** —A stream of packets transmitted between two endpoints 
- Usually identified by at least a Protocol, Source Address and Destination Address (and possibly source & dest port numbers). May or may not be tunnelized. 
**Stale Flow** —A flow that existed prior to a configuration change on a Silver Peak that is operating under old rules. 

**Passthtrough Traffic** - Flows NOT in an SD-WAN tunnel between two EdgeConnects
- Traffic is received by an EdgeConnect, but NOT tunneled/optimized/etc. to another EdgeConnect.
- Passed through to the next hop router for forwarding to its destination. 

Passthrough and Local Internet Breakout traffic can still be treated with Silver Peak QoS before being forwarded to the next hop.

**Local Internet Breakout** — Another way of referring to traffic usually destined to a non Silver Peak device. Usually refers to SaaS/laaS traffic that may be natively secured by other means (TLS, SSL, etc.) 

>![[passthrough flow.PNG]]

### Underlays & Overlays & BIOs

– Business Intent Overlay → Determines Overlay
– Overlay → Selected Underlay(s) to Use
– Underlay
	- 	Ethernet
	- 	MPLS
	- LTE

>![[underlay.PNG]]


### Underlay and Overlay Tunnels

**Underlay Tunnels**
- The physical transport network
- MPLS, Internet, LTE or other transports.
- Site to site connections built using IPsec_UDP* tunnels. 

**Overlay Tunnels**
- Logical connections
- Uses one or more underlay tunnels.
- Uses multiple underlay tunnels and transports depending on configuration 

>![[overlay-underlay.PNG]]
>*Overlay/Underlay Tunnels*

### Business Intent Overlays (BIO)

The set of policies and configuration parameters that determine:
- Which transports are used for underlays
- Which underlays are used for each overlay
- How the traffic is distributed across the underlays
- And more…

>![[BIO.PNG]]

### Traffic Handling Features

**Path Conditioning**
Forward Error Correction (FEC) – Uses parity packets to reconstruct lost packets to avoid retransmission
Packet Order Correction (POC) – Reorders any out-of-order packets to avoid retransmission

**Dynamic Path Control (DPC)**
Methods to dynamically select the appropriate underlay tunnel within a BIO’s Link Bonding Policy.

### WAN OPTIMIZATION FEATURE - BOOST

**BOOST** = WAN optimization technologies available as an extra cost option

**TCP Acceleration** – Optimizes the TCP protocol to mitigate the effects of latency
**Network Memory** – Deduplicates transmitted data to reduce congestion


>![[sdwan.PNG]]

----
tags: #spsp #sdwan #tunnel
links: https://training.silver-peak.com/#/online-courses/79334337-20bf-4642-89fc-46e28b77c525
see also:
created on: 2022-01-08 08:02