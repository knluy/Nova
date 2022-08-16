## Cisco Hierarchial Model(3-tier)

### Three Tier Design

- Used in Data Centers
- The distribution layer was responsible for terminating all customer circuits

>![[cisco hierarchial model 2.PNG]]
>*Sample of Enterprise 3-Tier Design*

### Parts of the 3 Tier Design

#### Core Layer

**Core Layer** consists of biggest, fastest, and most expensive routers with the highest model numbers and Core Layer is considered as the back bone of networks. Core Layer routers are used to merge geographically separated networks. The Core Layer routers move information on the network as fast as possible. The switches operating at core layer switches packets as fast as possible.

#### Distribution layer:
The **Distribution Layer** is located between the access and core layers. The purpose of this layer is to provide boundary definition by implementing access lists and other filters. Therefore the Distribution Layer defines policy for the network. Distribution Layer include high-end layer 3 switches. Distribution Layer ensures that packets are properly routed between subnets and [[VLAN]]s in your enterprise.

#### Access layer
**Access layer** includes acces switches which are connected to the end devices (Computers, Printers, Servers etc). Access layer switches ensures that packets are delivered to the end devices.


### Benefits of Cisco Three-Layer hierarchical model

The main benefits of Cisco Three-Layer hierarchical model is that it helps to design, deploy and maintain a scalable, trustworthy, cost effective hierarchical internetwork.

- **Better Performance:** Cisco Three Layer Network Model allows in creating high performance networks

- **Better management & troubleshooting:** Cisco Three Layer Network Model allows better network management and isolate causes of network trouble.

- **Better Filter/Policy creation and application:** Cisco Three Layer Network Model allows better filter/policy creation application.

- **Better Scalability:** Cisco Three Layer Network Model allows us to efficiently accomodate future growth.

- **Better Redundancy:** Cisco Three Layer Network Model provides better redundancy. Multiple links across multiple devices provides better redundancy. If one switch is down, we have another alternate path to reach the destination.


## Collapse Core Design

- Used in Small Offices
- Core Router was merged to Distribution Layer
>![[cisco hierarchial model 3.PNG]]
>*Sample of Collapse Core Design*



---
tags: #ccna #topology #cisco 
links: [Cisco hierarchical model(3-tier) | CCNAPH](https://ccnaphilippines.teachable.com/courses/742904/lectures/15859374) , https://www.omnisecu.com/cisco-certified-network-associate-ccna/three-tier-hierarchical-network-model.php#:~:text=Cisco%20suggests%20a%20Three%E2%88%92Tier,explained%20based%20on%20below%20picture.
see also:
created on: 2021-12-21 23:13