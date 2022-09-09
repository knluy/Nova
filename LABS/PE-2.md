

conf t
hostname PE-2

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
channel-group 1 mode passive
exit

int po1
switchport trunk encapsulation dot1q
switchport mode trunk
exit

---

int e0/3
ip address 100.0.0.9 255.255.255.252
description LINK CORE-RTR-2 TO PE-2
no shut
exit


int e1/0
ip address 100.0.0.17 255.255.255.252
description LINK CORE-RTR-1 TO PE-2
no shut
exit