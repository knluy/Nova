

conf t
hostname MPLS-1
int e0/0
ip address 10.110.11.1 255.255.255.0
no shut
exit

int e0/1
ip address 10.110.21.1 255.255.255.0
no shut
exit

int e0/2
ip address 10.110.31.1 255.255.255.0
no shut
exit

