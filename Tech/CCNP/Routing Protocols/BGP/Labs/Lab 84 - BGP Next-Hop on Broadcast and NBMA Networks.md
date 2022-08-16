## Lab 84 - BGP Next-Hop on Broadcast and NBMA Networks

>![[lab 84 hacking cisco gns3.PNG]]

### Task 1
Configure BGP on all routers according to the topology diagram. Advertise all loopbacks using 'network' statement. Check the next-hop behavior on LAN link connecting **R1**, **R2** and **R4**.

### RTR1:
```
!

router bgp 13  
 no synchronization  
 bgp router-id 1.1.1.1  
 bgp log-neighbor-changes  
 network 172.16.101.0 mask 255.255.255.0  
 neighbor 10.1.13.3 remote-as 13  
 neighbor 10.1.13.3 next-hop-self  
 neighbor 10.1.124.4 remote-as 40  
 no auto-summary

!
```

### RTR2:

```
!

router bgp 20  
 no synchronization  
 bgp router-id 2.2.2.2  
 bgp log-neighbor-changes  
 network 172.16.102.0 mask 255.255.255.0  
 neighbor 10.1.124.4 remote-as 40  
 no auto-summary

!

```

### RTR3:
```
!

router bgp 13  
 no synchronization  
 bgp router-id 3.3.3.3  
 bgp log-neighbor-changes  
 network 172.16.103.0 mask 255.255.255.0  
 neighbor 10.1.13.1 remote-as 13  
 neighbor 10.1.13.1 next-hop-self  
 neighbor 10.1.35.5 remote-as 50  
 no auto-summary

!

```

### RTR4:

```
!

router bgp 40  
 no synchronization  
 bgp router-id 4.4.4.4  
 bgp log-neighbor-changes  
 network 172.16.104.0 mask 255.255.255.0  
 network 172.16.144.0 mask 255.255.255.0  
 neighbor 10.1.124.1 remote-as 13  
 neighbor 10.1.124.2 remote-as 20  
 no auto-summary

!

```

### RTR5:

```
!

router bgp 50  
 no synchronization  
 bgp router-id 5.5.5.5  
 bgp log-neighbor-changes  
 network 172.16.105.0 mask 255.255.255.0  
 neighbor 10.1.35.3 remote-as 13  
 no auto-summary

!
```

Verification on RTR5:

![[Pasted image 20220126090603.png]]

Verification on RTR1:

![[Pasted image 20220126090625.png]]

---
tags: #ccnp #routing #bgp #labs
links: http://hackingcisco.blogspot.com/2011/03/lab-84-bgp-next-hop-on-broadcast-and.html
see also:
created on: 2022-01-26 00:11