
conf t
hostname PE-2

vlan 5
name MANAGEMENT
exit
vlan 10
name DATA
exit

int vlan 5
ip address 192.168.2.2 255.255.255.0
no shut
exit

int vlan 10
ip address 192.168.3.2 255.255.255.0
no shut
exit

int range g0/2
switchport trunk encapsulation dot1q
switchport mode trunk
exit


int g0/3
no switchport
ip address 100.0.0.9 255.255.255.252
description LINK CORE-RTR-2 TO PE-2
no shut
exit


int g1/0
no switchport
ip address 100.0.0.17 255.255.255.252
description LINK CORE-RTR-1 TO PE-2
no shut
exit

router ospf 1
router-id 4.4.4.4
network 100.0.0.8 0.0.0.3 area 0
network 100.0.0.16 0.0.0.3 area 0
exit

router ospf 1
network 192.168.2.0 0.0.0.255 area 0
network 192.168.3.0 0.0.0.255 area 0
exit

int e0/0
switchport mode access
switchport access vlan 5
exit

int e0/3
switchport mode access
switchport access vlan 10
exit
---

