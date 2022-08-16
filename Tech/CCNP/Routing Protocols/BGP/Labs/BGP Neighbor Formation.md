## BGP Neighbor Formation


>![[basic bgp neigbor.PNG]]


### RTR1:

```
Router#
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RTR1
RTR1(config)#int gi0/0
RTR1(config-if)#ip address 10.1.1.1 255.255.255.252
RTR1(config-if)#no shut
RTR1(config-if)#exit
RTR1(config)#router bgp 65100
RTR1(config-router)#neighbor 10.1.1.2 remote-as 65200
RTR1(config-router)#
*Jan 18 03:32:57.717: %LINK-3-UPDOWN: Interface GigabitEthernet0/0, changed state to up
*Jan 18 03:32:58.717: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
RTR1(config-router)#
````

**Verification:**

```
RTR1#sh run | s bgp
router bgp 65100
 bgp log-neighbor-changes
 neighbor 10.1.1.2 remote-as 65200
RTR1#sh ip bgp all sum
For address family: IPv4 Unicast
BGP router identifier 10.1.1.1, local AS number 65100
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.1.2       4        65200       4       4        1    0    0 00:00:50        0
RTR1#

```

### RTR2:

```
Router#
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RTR2
RTR2(config)#int gi0/0
RTR2(config-if)#ip address 10.1.1.2 255.255.255.252
RTR2(config-if)#no shut
RTR2(config-if)#exit
RTR2(config)#router bgp 65200
RTR2(config-router)#neighbor 10.1.1.1 remote-as 65100
RTR2(config-router)#
*Jan 18 03:37:00.397: %LINK-3-UPDOWN: Interface GigabitEthernet0/0, changed state to up
*Jan 18 03:37:01.397: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
RTR2(config-router)#
*Jan 18 03:37:03.925: %BGP-5-ADJCHANGE: neighbor 10.1.1.1 Up
RTR2(config-router)#

```

**Verification:**

```
RTR2#sh run | s bgp
router bgp 65200
 bgp log-neighbor-changes
 neighbor 10.1.1.1 remote-as 65100
RTR2#sh ip bgp all sum
For address family: IPv4 Unicast
BGP router identifier 10.1.1.2, local AS number 65200
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.1.1        4        65100       5       5        1    0    0 00:01:48        0
RTR2#
```

---
tags: #ccnp #routing #bgp #configure
links: https://www.linkedin.com/learning/cisco-ccnp-enarsi-300-410-cert-prep-2-vpn-technologies/neighbor-formation?autoAdvance=true&autoSkip=true&autoplay=true&contextUrn=urn%3Ali%3AlyndaLearningPath%3A5f88923f498edf8b778e9879&resume=false&u=46118444
see also:
created on: 2022-01-18 11:15