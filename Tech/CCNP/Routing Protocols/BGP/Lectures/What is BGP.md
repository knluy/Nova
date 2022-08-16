## What is BGP


Border Gateway Protocol (BGP):

- Considered an Exterior Gateway Protocol (EGP)
- Routes between autonomous systems
- "Protocol of the Internet"
- Autonomous System Numbers (ASNs) allow for communication

BGP
- AS numbers provided from the IANA
- Designated 32 bit range of ASN for unique assignment
- Roughly 4.3 bilion unique ASN available
- Adjacencies allow for route exchange
- BGP session = an adjacency established between BGP peers
- Neighbor addressing not learned via Multicast
- Neighbor addressing is explicitly configured
- BGP sessions use a TCP connection
- BGP advertisements contain address prefix and length
- NLRI (Network Layer Reachability Info) contains BGP advertisements info and path attributes (AS)

BGP:
- Path vector routing protocol
- Counts AS hops, rather than router hops
- uses TCP port 179
- TCP allows for adjacencies that are multiple hops away
- Multi-hop sessions require underlying routes from [[RIB]]


iBGP
- Internal BGP
- Communication between routers within the same AS

EBGP
- External BGP (eBGP)
- Communication between routers in different AS

---
tags: #ccna #ccnp #routing #bgp
links: https://www.linkedin.com/learning/cisco-ccnp-enarsi-300-410-cert-prep-2-vpn-technologies/review-of-bgp-fundamentals?autoAdvance=true&autoSkip=true&autoplay=true&contextUrn=urn%3Ali%3AlyndaLearningPath%3A5f88923f498edf8b778e9879&resume=false&u=46118444
see also:
created on: 2022-01-18 10:27