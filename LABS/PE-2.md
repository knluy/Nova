

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
