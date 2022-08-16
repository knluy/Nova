## Full mesh Topology

>A mesh topology is a network setup where each computer and network device is interconnected with one another. This topology setup allows for most transmissions to be distributed even if one of the connections goes down. It is a topology commonly used for wireless networks. Below is a visual example of a simple computer setup on a network using a mesh topology.
>
>Source: https://www.computerhope.com/jargon/m/mesh.htm

### Different types of Mesh Topology

There are two forms of this topology: full mesh and a partially-connected mesh.

#### Full Mesh
In a full mesh topology, every computer in the network has a connection to each of the other computers in that network. The number of connections in this network can be calculated using the following formula (n is the number of computers in the network): 
>![[full mesh topology.png]]
> $number of computers = n(n-1)/2$
> *Sample of Full Mesh Topology*


#### [[Partial Mesh Topology | Partial Mesh]]
In a partially-connected mesh topology, ==at least two of the computers in the network have connections to multiple other computers== in that network. It is an inexpensive way to implement redundancy in a network. If one of the primary computers or connections in the network fails, the rest of the network continues to operate normally.

### Advantages
- Manages high amounts of traffic, because multiple devices can transmit data simultaneously.
- A failure of one device does not cause a break in the network or transmission of data.
- Adding additional devices does not disrupt data transmission between other devices.

### Disadvantages
- The cost to implement is higher than other network topologies, making it a less desirable option.
- Building and maintaining the topology is difficult and time consuming.
- The chance of redundant connections is high, which adds to the high costs and potential for reduced efficiency.

---
tags: #ccna #network #topology 
links: https://www.computerhope.com/jargon/m/mesh.htm
see also: 
created on: 2021-12-22 13:59

