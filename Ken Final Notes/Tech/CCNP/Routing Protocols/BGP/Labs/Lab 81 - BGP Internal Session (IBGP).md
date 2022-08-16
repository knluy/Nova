## Lab 81 - BGP Internal Session (IBGP)

>![[lab 81 hacking cisco.png]]

**Updated Topology:**
>![[lab 81 hacking cisco GNS3.png]]


### Task 1
Configure OSPF area 0 between **R1** and **R3**. Make sure that loopback0 on both routers are advertised in OSPF.  
  
  
  #### RTR1:
  
  ```
 RTR1#sh run | s ospf
router ospf 1
 router-id 1.1.1.1
 network 10.1.13.0 0.0.0.255 area 0
 network 172.16.101.0 0.0.0.255 area 0
RTR1#
  ```

#### RTR3:

```
RTR3#sh run | s ospf
router ospf 1
 router-id 3.3.3.3
 network 10.1.13.0 0.0.0.255 area 0
 network 172.16.103.0 0.0.0.255 area 0
RTR3#
```

**Verification:**

on RTR1:

```
RTR1#sh ip route ospf

Gateway of last resort is not set

      172.16.0.0/16 is variably subnetted, 3 subnets, 2 masks
O        172.16.103.3/32 [110/2] via 10.1.13.3, 00:18:06, GigabitEthernet0/0
RTR1#

RTR1#sh ip int b
Interface                  IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0         10.1.13.1       YES manual up                    up  
GigabitEthernet0/1         unassigned      YES unset  administratively down down
GigabitEthernet0/2         unassigned      YES unset  administratively down down
GigabitEthernet0/3         unassigned      YES unset  administratively down down
Loopback0                  172.16.101.1    YES manual up                    up  
RTR1#

RTR1#ping 172.16.103.3 so 172.16.101.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.103.3, timeout is 2 seconds:
Packet sent with a source address of 172.16.101.1
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 4/5/8 ms
RTR1#


```

on RTR3:

```
RTR3#sh ip route ospf

Gateway of last resort is not set

      172.16.0.0/16 is variably subnetted, 3 subnets, 2 masks
O        172.16.101.1/32 [110/2] via 10.1.13.1, 00:16:05, GigabitEthernet0/0
RTR3#

RTR3#sh ip int b
Interface                  IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0         10.1.13.3       YES manual up                    up  
GigabitEthernet0/1         unassigned      YES unset  administratively down down
GigabitEthernet0/2         unassigned      YES unset  administratively down down
GigabitEthernet0/3         unassigned      YES unset  administratively down down
Loopback0                  172.16.103.3    YES manual up                    up  
RTR3#

RTR3#ping 172.16.101.1 so 172.16.103.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.101.1, timeout is 2 seconds:
Packet sent with a source address of 172.16.103.3
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 5/6/9 ms
RTR3#
```

#### Task 2
Configure IBGP session between **R1** and **R3**. Use loopback0 as the source of IP addresses for IBGP session. Check the configuration.


#### RTR1:
```
RTR1#sh run | s bgp
router bgp 13
 bgp router-id 1.1.1.1
 bgp log-neighbor-changes
 neighbor 172.16.103.3 remote-as 13
 neighbor 172.16.103.3 update-source Loopback0
RTR1#
```

#### RTR3:

```
RTR3#sh run | s bgp
router bgp 13
 bgp router-id 3.3.3.3
 bgp log-neighbor-changes
 neighbor 172.16.101.1 remote-as 13
 neighbor 172.16.101.1 update-source Loopback0
RTR3#
```

**Verification:**

on RTR1:

```
RTR1#sh ip bgp summary
BGP router identifier 1.1.1.1, local AS number 13
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
172.16.103.3    4           13      27      26        1    0    0 00:21:00        0
RTR1#

RTR1#sh ip bgp neighbors 172.16.103.3
BGP neighbor is 172.16.103.3,  remote AS 13, internal link
  BGP version 4, remote router ID 3.3.3.3
  BGP state = Established, up for 00:21:29
  Last read 00:00:35, last write 00:00:10, hold time is 180, keepalive interval       is 60 seconds

Connection state is ESTAB, I/O status: 1, unread input bytes: 0
Connection is ECN Disabled, Mininum incoming TTL 0, Outgoing TTL 255
Local host: 172.16.101.1, Local port: 45847
Foreign host: 172.16.103.3, Foreign port: 179

```

on RTR3:

```
RTR3#sh ip bgp summary
BGP router identifier 3.3.3.3, local AS number 13
BGP table version is 1, main routing table version 1

Neighbor        V           AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
172.16.101.1    4           13      28      29        1    0    0 00:22:54        0
RTR3#

RTR3#sh ip bgp neighbors 172.16.101.1
BGP neighbor is 172.16.101.1,  remote AS 13, internal link
  BGP version 4, remote router ID 1.1.1.1
  BGP state = Established, up for 00:23:26
  Last read 00:00:19, last write 00:00:49, hold time is 180, keepalive interval is 60 seconds
  
Connection state is ESTAB, I/O status: 1, unread input bytes: 0
Connection is ECN Disabled, Mininum incoming TTL 0, Outgoing TTL 255
Local host: 172.16.103.3, Local port: 179
Foreign host: 172.16.101.1, Foreign port: 45847

```

---
tags: #ccnp #bgp #routing #labs
links: http://hackingcisco.blogspot.com/2011/03/lab-81-bgp-internal-session-ibgp.html
see also:
created on: 2022-01-18 13:42