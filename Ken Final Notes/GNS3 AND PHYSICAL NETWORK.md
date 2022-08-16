## GNS3 AND PHYSICAL NETWORK

parameters to check when connecting physical network to gns3:

vmware adapter
bridge - directly connected to physical network
NAT - uses NAT to hide the gns3vm network
Host Only - isolates gns3vm to the network

check cloud interface
- always check vmware network adapters for direction
- always starts at 0

check connectivity
-check static routing
- interface of cloud is always the gateway 

check firewall 
- is firewall on/off
- check inbound/outbound rules (in firewall > advanced settings)

NOTE:
in gns3 perspective:
tplink gateway is 0.0.0.0
cloud interface is the default gateway


---
tags: #ccnp #labs 
links:
see also:
created on: 2022-02-02 11:51