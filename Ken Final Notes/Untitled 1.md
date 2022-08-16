[3:16 pm] Nicolas, Archie Val

MPLS1#  
MPLS1(config)#no ip domain lookup  
MPLS1(config)#router ospf 1  
MPLS1(config-router)#router-id 1.1.1.1  
MPLS1(config-router)#mpls ldp autoconfig  
MPLS1(config-router)#network 1.1.1.1 0.0.0.0 area 0  
MPLS1(config-router)#network 172.16.1.1 0.0.0.0 area 0  
MPLS1(config-router)#network 172.16.1.5 0.0.0.0 area 0  

  

MPLS1(config)#int s0/0  
MPLS1(config-if)#ip ospf network point-to-point  
MPLS1#(config)#int s0/1  
MPLS1(config-if)#ip ospf network point-to-point  
----------------------------------------------------------------------------------  
MPLS2#  
MPLS2(config)#no ip domain lookup  
MPLS2(config)#router ospf 1  
MPLS2(config-router)#router-id 2.2.2.2  
MPLS2(config-router)#mpls ldp autoconfig  
MPLS2(config-router)#network 2.2.2.2 0.0.0.0 area 0  
MPLS2(config-router)#network 172.16.1.2 0.0.0.0 area 0  
MPLS2(config-router)#network 172.16.1.5 0.0.0.0 area 0

  

MPLS2(config)#int s0/0  
MPLS2(config-if)#ip ospf network point-to-point  
MPLS2(config)#int s0/1  
MPLS2(config-if)#ip ospf network point-to-point  
----------------------------------------------------------------------------------  
MPLS3#  
MPLS3(config)#no ip domain lookup  
MPLS3(config)#router ospf 1  
MPLS3(config-router)#router-id 3.3.3.3  
MPLS3(config-router)#mpls ldp autoconfig  
MPLS3(config-router)#network 3.3.3.3 0.0.0.0 area 0  
MPLS3(config-router)#network 172.16.1.5 0.0.0.0 area 0  
MPLS3(config-router)#network 172.16.1.13 0.0.0.0 area 0

  

MPLS3(config)#int s0/0  
MPLS3(config-if)#ip ospf network point-to-point  
MPLS3(config)#int s0/1  
MPLS3(config-if)#ip ospf network point-to-point  
-----------------------------------------------------------------------------------  
MPLS4#  
MPLS4(config)#no ip domain lookup  
MPLS4(config)#router ospf 1  
MPLS4(config-router)#router-id 4.4.4.4  
MPLS4(config-router)#mpls ldp autoconfig  
MPLS4(config-router)#network 4.4.4.4 0.0.0.0 area 0  
MPLS4(config-router)#network 172.16.1.6 0.0.0.0 area 0  
MPLS4(config-router)#network 172.16.1.14 0.0.0.0 area 0

  

MPLS4(config)#int s0/0  
MPLS4(config-if)#ip ospf network point-to-point  
MPLS4(config)#int s0/1  
MPLS4(config-if)#ip ospf network point-to-point

  

[3:16 pm] Nicolas, Archie Val

MPLS1(config)#ip cef  
MPLS1(config)#mpls label protocol ldp  
MPLS1(config)#mpls label range 100 199  
MPLS1(config)#mpls ldp router-id loopback 0  
MPLS1(config)#int s0/0  
MPLS1(config-if)#mpls ip  
MPLS1(config)#int s0/1  
MPLS1(config-if)#mpls ip  

  

MPLS2(config)#ip cef  
MPLS2(config)#mpls label protocol ldp  
MPLS2(config)#mpls label range 200 299  
MPLS2(config)#mpls ldp router-id loopback 0  
MPLS2(config)#int s0/0  
MPLS2(config-if)#mpls ip  
MPLS2(config)#int s0/1  
MPLS2(config-if)#mpls ip

  

MPLS3(config)#ip cef  
MPLS3(config)#mpls label protocol ldp  
MPLS3(config)#mpls label range 300 399  
MPLS3(config)#mpls ldp router-id loopback 0  
MPLS3(config)#int s0/0  
MPLS3(config-if)#mpls ip  
MPLS3(config)#int s0/1  
MPLS3(config-if)#mpls ip

  

MPLS4(config)#ip cef  
MPLS4(config)#mpls label protocol ldp  
MPLS4(config)#mpls label range 400 499  
MPLS4(config)#mpls ldp router-id loopback 0  
MPLS4(config)#int s0/0  
MPLS4(config-if)#mpls ip  
MPLS4(config)#int s0/1  
MPLS4(config-if)#mpls ip

  

[3:17 pm] Nicolas, Archie Val

MPLS1#sh ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
3.3.3.3 0 FULL/ - 00:00:32 172.16.1.6 Serial0/1  
2.2.2.2 0 FULL/ - 00:00:38 172.16.1.2 Serial0/0  

  

MPLS2#sh ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
4.4.4.4 0 FULL/ - 00:00:31 172.16.1.6 Serial0/1  
1.1.1.1 0 FULL/ - 00:00:33 172.16.1.1 Serial0/0

  

MPL3#sh ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
4.4.4.4 0 FULL/ - 00:00:37 172.16.1.14 Serial0/1  
1.1.1.1 0 FULL/ - 00:00:33 172.16.1.5 Serial0/0

  

MPLS4#sh ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
3.3.3.3 0 FULL/ - 00:00:36 172.16.1.13 Serial0/1  
2.2.2.2 0 FULL/ - 00:00:37 172.16.1.5 Serial0/0



[3:48 pm] Nicolas, Archie Val

CHANGE DEFAULT

Default username is **admin without password**.

  

root@host# CLI  
root@host# edit private

  

anicolas@Junos# edit system login  
anicolas@Junos# edit user archie  
anicolas@Junos# set full-name "Archie Val Nicolas"  
anicolas@Junos# set class super-user  
anicolas@Junos# set authentication plain text-password  
New password:  
Confirm password:

  

anicolas@Junos# set system host-name Junos  
anicolas@Junos# set system name-server 8.8.8.8  
anicolas@Junos# set system services ssh  
anicolas@Junos# set system time-zone Asia/Manila

  

anicolas@Junos> show system uptime | match time


[3:54 pm] Nicolas, Archie Val

Junos Best Practice (as per advise ni sir Elie)

  

edit private  
show | compare  
commit check  
commit and-quit

like 1