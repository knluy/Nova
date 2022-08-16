## Lab 83 - BGP Synchronization

>![[lab 83 hacking cisco.PNG]]

**Updated Topology**

>![[lab 83 hacking cisco GNS3.PNG]]


### Task1
Enable BGP Synchronization on **R1**. Ensure **R1** can reach 172.16.105.0/24.

#### RTR1:
```
!
router bgp 13  
 synchronization  
 bgp router-id 1.1.1.1  
 bgp log-neighbor-changes  
 network 172.16.101.0 mask 255.255.255.0  
 neighbor 172.16.103.3 remote-as 13  
 neighbor 172.16.103.3 update-source Loopback0  
 no auto-summary

!
```

**Verification:**

```
RTR1#sh ip bgp
BGP table version is 3, local router ID is 1.1.1.1
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, m multipath, b backup-path, f RT-Filter,
              x best-external, a additional-path, c RIB-compressed,
Origin codes: i - IGP, e - EGP, ? - incomplete
RPKI validation codes: V valid, I invalid, N Not found

     Network          Next Hop            Metric LocPrf Weight Path
 *>  172.16.101.0/24  0.0.0.0                  0         32768 i
 *>i 172.16.103.0/24  172.16.103.3             0    100      0 i
 * i 172.16.105.0/24  10.1.35.5                0    100      0 50 i
RTR1#    
```

**Notice!**  
The code for the best path '>' has been removed since the prefix is not synchronized with with IGP (IBGP loop prevention mechanism). It takes about a minute to see the change in the BGP table. The result: no reachability to 172.16.105.0/24 (prefix will not be installed in the routing table).



 #### RTR3:

```
!
ip prefix-list BGP_PREFIX seq 5 permit 172.16.105.0/24

!

route-map BGP_TO_OSPF permit 10  
 match ip address prefix-list BGP_PREFIX  
!  
router ospf 1  
 router-id 3.3.3.3  
 log-adjacency-changes  
 redistribute bgp 13 subnets route-map BGP_TO_OSPF  
 network 10.1.13.3 0.0.0.0 area 0  
 network 172.16.103.3 0.0.0.0 area 0

!
```

**Verification:**

```
Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C        10.1.13.0/24 is directly connected, GigabitEthernet0/0
L        10.1.13.1/32 is directly connected, GigabitEthernet0/0
      172.16.0.0/16 is variably subnetted, 5 subnets, 2 masks
C        172.16.101.0/24 is directly connected, Loopback0
L        172.16.101.1/32 is directly connected, Loopback0
B        172.16.103.0/24 [200/0] via 172.16.103.3, 00:07:40
O        172.16.103.3/32 [110/2] via 10.1.13.3, 00:08:22, GigabitEthernet0/0
O E2     172.16.105.0/24 [110/1] via 10.1.13.3, 00:00:17, GigabitEthernet0/0
RTR1#      


```

>![[Pasted image 20220120214630.png]]

---
tags: #ccnp #routing #bgp #labs
links: http://hackingcisco.blogspot.com/2011/03/lab-83-bgp-synchronization.html, http://docwiki.cisco.com/wiki/Internetworking_Case_Studies_--_Using_the_Border_Gateway_Protocol_for_Interdomain_Routing#Synchronization
see also:
created on: 2022-01-20 21:03