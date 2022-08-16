## Spine and Leaf Network Architecture
**Definition:**
>Spine and Leaf Architecture is a two-layer, full-mesh topology composed of a leaf layer and a spine layer, with the leaf and spine switches. It was originally implemented in data centers to overcome the limitations of the three-tier architecture, where we have more east-west traffic than north-south traffic flow.  East-west traffic flows are server-to-server communication within the same data center.

### Parts of Spine and Leaf Topology

**Spine Layer –** serves as the backbone of the network similar to the core layer in our three-tier design. It is where we can find the spine switches which can be a [[Layer 3 Switch]]. Each Layer 3 port is connected to the underlying [[Layer 2 Switch | Layer 2]] leaf switch.

**Leaf Layer –** connects to end devices similar to the access layer in our three-tier design. It is where the leaf switches which connect to all spine switches reside. In our example above, we have servers that connect to leaf switches. In a data center environment, it can be any kind of server, like web server, application server, database server, or storage server.


>![[spine leaf topology.PNG]]
>*Spine and Leaf Network Architecture*


### Benefits of Spine and Leaf Architecture

- **Improved Redundancy** 
- **Increased Bandwidth**
- **Improved Scalability**
- **Lower Costs**
- **Low Latency and Congestion Avoidance**
- **Energy Efficient** 



---
tags: #ccna #topology 
links: [Spine and Leaf - Study CCNA](https://study-ccna.com/spine-and-leaf-architecture/), https://www.arubanetworks.com/faq/what-is-spine-leaf-architecture/ , https://networklessons.com/cisco/ccna-200-301/spine-and-leaf-architecture , https://searchdatacenter.techtarget.com/definition/Leaf-spine
see also:
created on: 2021-12-23 09:28