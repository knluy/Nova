## Lab 82 - BGP External Session (EBGP) and Advertisements

>![[lab 82 hacking cisco.PNG]]

**Updated Topology**

>![[lab 82 hacking cisco GNS3.PNG]]


### Task1 
Configure EBGP session between **R3** and **R5**.  

#### RTR3:
  
  ```
RTR3#sh run | s bgp
router bgp 13
 bgp router-id 3.3.3.3
 bgp log-neighbor-changes
 neighbor 10.1.35.2 remote-as 50
 neighbor 172.16.101.1 remote-as 13
 neighbor 172.16.101.1 update-source Loopback0
RTR3#
*Jan 18 14:07:16.452: %BGP-5-ADJCHANGE: neighbor 10.1.35.2 Up
RTR3#

```
  
  #### RTR5:
  
  ```
RTR5#sh run | s bgp
router bgp 50
 bgp router-id 5.5.5.5
 bgp log-neighbor-changes
 neighbor 10.1.35.3 remote-as 13
RTR5#

  ```
  
  **Verification**
  
  on RTR3:
  
  ```
RTR3#sh ip bgp sum
BGP router identifier 3.3.3.3, local AS number 13
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.35.5       4           50       6       6        1    0    0 00:02:04        0
172.16.101.1    4           13       4       4        1    0    0 00:00:05        0
RTR3#
  ```
  
  on RTR5:
  
  ```
RTR5#sh ip bgp sum
BGP router identifier 5.5.5.5, local AS number 50
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
10.1.35.3       4           13       5       5        1    0    0 00:01:43        0
RTR5#
  ```
  
### Task2

Advertise loopback addresses into BGP on **R1**, **R3** and **R5**. On **R5** do not use the 'network' statement. Ensure the reachability between the advertised subnets.

Note: 
As per scott, this is not realistic anymore, as common config is only on "network" commands
Will put the document here for reference:

```
!
router bgp 13  
 no synchronization  
 bgp router-id 1.1.1.1  
 bgp log-neighbor-changes  
 network 172.16.101.0 mask 255.255.255.0  
 neighbor 172.16.103.3 remote-as 13  
 neighbor 172.16.103.3 update-source Loopback0  
 no auto-summary

!

```

**Notice!**
'Network' statement in BGP does advertise the networks (unlike in IGP protocols). The network/subnet must have the EXACT match in the routing table (network/network_mask). If the subnet is being advertised (not a major class), the 'mask' keyword must be used.

>![[Pasted image 20220119175338.png]]

**Notice!**  
Subnets advertised locally always set the two BGP attributes as  

-   Next-Hop = 0.0.0.0
-   Weight = 32768
-   Path = empty

In addition to this, if the 'network' statement is used to advertise a network/subnet, origin code is set to 'i' = IGP.

>![[Pasted image 20220119175423.png]]

**Notice!**  
**R3** receives 172.16.101.0/24 but is marked as RIB-Failure. This is due to the fact that Administrative Distance of IBGP is 200, and the same prefix is advertised by OSPF with the Administrative Distance 110.    
  
**Notice!**
Next-hop attribute point to the source of BGP advertisements (**R1**'s Loopback0)**:** 172.16.101.1.  
  
**Notice!**  
**R3** automatically assigns Local Preference: 100. The same Local Preference value is assigned by **R1** (originator of the prefix). This can be seen on **R1** using this command:

>![[Pasted image 20220119175448.png]]

>![[Pasted image 20220119180028.png]]

**Notice!**  
**R3** advertising the prefix to an EBGP neighbor, prepends the AS (13).

R3 Configuration:
```
!

router bgp 13  
 no synchronization  
 bgp router-id 3.3.3.3  
 bgp log-neighbor-changes  
 network 172.16.103.0 mask 255.255.255.0  
 neighbor 10.1.35.5 remote-as 50  
 neighbor 172.16.101.1 remote-as 13  
 neighbor 172.16.101.1 update-source Loopback0  
 no auto-summary

!
```

R5 Configuration:
```
!

ip prefix-list LO seq 5 permit 172.16.105.0/24

!

route-map CONN_TO_BGP permit 10  
 match ip address prefix-list LO  
!

router bgp 50  
 no synchronization  
 bgp router-id 5.5.5.5  
 bgp log-neighbor-changes  
 redistribute connected route-map CONN_TO_BGP  
 neighbor 10.1.35.3 remote-as 13  
 no auto-summary
!
```

Verification:

>![[Pasted image 20220119175945.png]]

**Notice!**  
The origin attribute for BGP redistributed prefixes is set to '?' = incomplete.  
  
**Notice!**  
**R1** is going to have problem with the reachability to 172.16.105.0/24. The next-hop attribute set by EBGP peer (BGP neighbor) is not changed (except for connections in the same broadcast domain). **R1** has no reachability to the next-hop 10.1.35.5.

>![[Pasted image 20220119175638.png]]

>![[Pasted image 20220119175648.png]]


There's bunch of ways to resolve this issue. For now (some time later more on that), the 'next-hop-self' is going to be used.

R3 configuration:

```
!
router bgp 13  
 no synchronization  
 bgp router-id 3.3.3.3  
 bgp log-neighbor-changes  
 network 172.16.103.0 mask 255.255.255.0  
 neighbor 10.1.35.5 remote-as 50  
 neighbor 172.16.101.1 remote-as 13  
 neighbor 172.16.101.1 update-source Loopback0  
 neighbor 172.16.101.1 next-hop-self  
 no auto-summary

!
```

>![[Pasted image 20220119175909.png]]

>![[Pasted image 20220119175921.png]]
---
tags: #ccnp #routing #bgp #labs
links: http://hackingcisco.blogspot.com/2011/03/lab-82-bgp-external-session-ebgp-and.html
see also:
created on: 2022-01-18 21:56