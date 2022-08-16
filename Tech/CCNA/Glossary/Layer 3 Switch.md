## Layer 3 Switch
**Definition:**
>

### Functions:
 - *Connect End Devices*
- *Layer 2*
	- *[[Mac Addresses]]*
	- *Filter/Forward*
	- *[[ASIC]]*
- *Connect network devices*
- *Layer 3*
	- *Capable of Routing*
	- *[[SVI]]*
- *Disable Switchport*
- Comes in *3550, 3560, 3750 Series*

### How to enable Layer 3 routing
```
Switch(config)# int Fa0/1
Switch(config-if)# no switchport
Switch(config)# ip routing
```


>![[cisco hierarchial model.PNG]]
>
>*Sample of a Cisco Hierarchial Model*

---
tags: #ccna #switch #routing
links: 
see also:
created on: 2021-12-17 11:05