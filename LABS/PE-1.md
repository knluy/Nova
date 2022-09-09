

conf t
hostname PE-1

vlan 5
name MANAGEMENT
exit
vlan 10
name DATA
exit

int range e0/0-1
switchport trunk encapsulation dot1q
switchport mode trunk
exit

int e0/2
channel-group 1 mode active
exit

int po1
switchport trunk encapsulation dot1q
switchport mode trunk
exit

int vlan 5
ip address 192.168.1.1 255.255.255.0
no shut
exit
---

int e0/3
no switchport
ip address 100.0.0.6 255.255.255.252
description LINK CORE-RTR-1 TO PE-1
no shut
exit

int e1/0
no switchport
ip address 100.0.0.13 255.255.255.252
description LINK CORE-RTR-2 TO PE-1
no shut
exit