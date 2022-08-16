## Basic BGP configuration

>![[basic bgp neigbor with advertised prefix.PNG]]


### RTR1

```
Router#
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RTR1
RTR1(config)#int gi0/0
RTR1(config-if)#ip address 10.1.1.1 255.255.255.252
RTR1(config-if)#no shut
RTR1(config-if)#int lo0
RTR1(config-if)#ip address 1.1.1.1 255.255.255.255
RTR1(config-if)#exit
RTR1(config)#router bgp 65100
RTR1(config-router)#neighbor 10.1.1.2 remote-as 65200
RTR1(config-router)#network 1.1.1.1 mask 255.255.255.255
RTR1(config-router)#exit
RTR1(config)#exit
RTR1#
*Jan 18 03:42:13.344: %SYS-5-CONFIG_I: Configured from console by console
*Jan 18 03:42:13.986: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up
RTR1#
*Jan 18 03:42:14.789: %LINK-3-UPDOWN: Interface GigabitEthernet0/0, changed state to up
*Jan 18 03:42:15.790: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
RTR1#
```

**Verification:**

```
RTR1#sh run | s bgp
router bgp 65100
 bgp log-neighbor-changes
 network 1.1.1.1 mask 255.255.255.255
 neighbor 10.1.1.2 remote-as 65200
RTR1#sh ip bgp all sum
For address family: IPv4 Unicast
BGP router identifier 1.1.1.1, local AS number 65100
BGP table version is 3, main routing table version 3
2 network entries using 288 bytes of memory
2 path entries using 160 bytes of memory
2/2 BGP path/bestpath attribute entries using 304 bytes of memory
1 BGP AS-PATH entries using 24 bytes of memory
0 BGP route-map cache entries using 0 bytes of memory
0 BGP filter-list cache entries using 0 bytes of memory
BGP using 776 total bytes of memory
BGP activity 2/0 prefixes, 2/0 paths, scan interval 60 secs

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.1.2        4        65200       5       5        3    0    0 00:01:17        1
RTR1#ping 2.2.2.2 so 1.1.1.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 2.2.2.2, timeout is 2 seconds:
Packet sent with a source address of 1.1.1.1
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 3/3/5 ms
RTR1#
```

### RTR2

```
Router#
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RTR2
RTR2(config)#int gi0/0
RTR2(config-if)#ip address 10.1.1.2 255.255.255.252
RTR2(config-if)#no shut
RTR2(config-if)#int lo0
RTR2(config-if)#ip address 2.2.2.2 255.255.255.255
RTR2(config-if)#exit
RTR2(config)#router bgp 65200
RTR2(config-router)#neighbor 10.1.1.1 remote-as 65100
RTR2(config-router)#network 2.2.2.2 mask 255.255.255.255
RTR2(config-router)#exit
RTR2(config)#exit
RTR2#
*Jan 18 03:43:02.204: %SYS-5-CONFIG_I: Configured from console by console
*Jan 18 03:43:02.909: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up
RTR2#
*Jan 18 03:43:03.715: %LINK-3-UPDOWN: Interface GigabitEthernet0/0, changed state to up
RTR2#
*Jan 18 03:43:04.715: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0, changed state to up
RTR2#
*Jan 18 03:43:06.809: %BGP-5-ADJCHANGE: neighbor 10.1.1.1 Up
RTR2#
```

**Verification:**

```
RTR2#sh run | s bgp
router bgp 65200
 bgp log-neighbor-changes
 network 2.2.2.2 mask 255.255.255.255
 neighbor 10.1.1.1 remote-as 65100
RTR2#sh ip bgp all sum
For address family: IPv4 Unicast
BGP router identifier 2.2.2.2, local AS number 65200
BGP table version is 3, main routing table version 3
2 network entries using 288 bytes of memory
2 path entries using 160 bytes of memory
2/2 BGP path/bestpath attribute entries using 304 bytes of memory
1 BGP AS-PATH entries using 24 bytes of memory
0 BGP route-map cache entries using 0 bytes of memory
0 BGP filter-list cache entries using 0 bytes of memory
BGP using 776 total bytes of memory
BGP activity 2/0 prefixes, 2/0 paths, scan interval 60 secs

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.1.1        4        65100       6       6        3    0    0 00:02:36        1
RTR2#ping 1.1.1.1 so 2.2.2.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 1.1.1.1, timeout is 2 seconds:
Packet sent with a source address of 2.2.2.2
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 3/3/4 ms
RTR2#
```
---
tags: #ccnp #routing #bgp #configure
links: https://www.linkedin.com/learning/cisco-ccnp-enarsi-300-410-cert-prep-2-vpn-technologies/neighbor-formation?autoAdvance=true&autoSkip=true&autoplay=true&contextUrn=urn%3Ali%3AlyndaLearningPath%3A5f88923f498edf8b778e9879&resume=false&u=46118444
see also:
created on: 2022-01-18 10:27