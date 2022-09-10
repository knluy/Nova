

conf t
hostname PE-1

vlan 5
name MANAGEMENT
exit
vlan 10
name DATA
exit

int range g0/2
switchport trunk encapsulation dot1q
switchport mode trunk
exit

int vlan 5
ip address 192.168.2.1 255.255.255.0
no shut
exit

int vlan 10
ip address 192.168.3.1 255.255.255.0
no shut
exit


int g0/3
no switchport
ip address 100.0.0.6 255.255.255.252
description LINK CORE-RTR-1 TO PE-1
no shut
exit

int g1/0
no switchport
ip address 100.0.0.13 255.255.255.252
description LINK CORE-RTR-2 TO PE-1
no shut
exit

router ospf 1
router-id 3.3.3.3
network 100.0.0.4 0.0.0.3 area 0
network 100.0.0.12 0.0.0.3 area 0
exit

router ospf 1
network 192.168.2.0 0.0.0.255 area 0
network 192.168.3.0 0.0.0.255 area 0
exit

int g0/1
switchport mode access	
switchport access vlan 5
exit

int g0/0
switchport mode access
switchport access vlan 10
exit

---



