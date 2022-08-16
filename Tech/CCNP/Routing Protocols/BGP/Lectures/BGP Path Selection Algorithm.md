## BGP Path Selection Algorithm

1. Choose route with the highest weight.
2. Choose route with the highest local preference.
3. Choose routes originating from local router.
4. Choose the shortest Autonomous System path.
5. Choose the path with the lowest origin code.
6. Choose route with the lowest MED.
7. Prefer eBGP over iBGP route.
8. Choose route through nearest IGP neigbor by lowest metric.
9. Choose the oldest route
10. Choose path through neighbor with lowest RID (highest loopback)
11. Choose path with the minimum cluster list length.
12. Choose path through neighbor with lowest IP address.

---
tags: #ccnp #routing #bgp
links: https://www.linkedin.com/learning/cisco-ccnp-enarsi-300-410-cert-prep-2-vpn-technologies/bgp-path-selection?autoAdvance=true&autoSkip=true&autoplay=true&contextUrn=urn%3Ali%3AlyndaLearningPath%3A5f88923f498edf8b778e9879&resume=false&u=46118444
see also:
created on: 2022-01-18 12:19