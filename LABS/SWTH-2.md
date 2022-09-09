

conf t
hostname SWTH-2
vlan 5
name MANAGEMENT
exit
vlan 10
name DATA
exit

int range e0/1-2
switchport trunk encapsulation dot1q
switchport mode	trunk

int e0/0
switchport mode access
switchport access vlan 5
exit

---
int e0/3
switchport mode access
switchport access vlan 10
exit
