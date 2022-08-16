## Understanding IPv4 Addressing

Sample:

$$192.168.1.1$$

where: 
- IPv4 Address - Divided by dot (dotted decimal)
- 4 groups (octet)
- 0-255 (Decimal)
- 1 octet = 8 bits
- 32 bits in total
- Network and Host portion

Complete form:

>![[ipv4.PNG]]
>*Sample of IPv4 Address*


**From Juniper:**

IPv4 addresses are 32-bit numbers that are typically displayed in dotted decimal notation. A 32-bit address contains two primary parts: the network prefix and the host number.

All hosts within a single network share the same network address. Each host also has an address that uniquely identifies it. Depending on the scope of the network and the type of device, the address is either globally or locally unique. Devices that are visible to users outside the network (webservers, for example) must have a globally unique IP address. Devices that are visible only within the network must have locally unique IP addresses.

IP addresses are assigned by a central numbering authority called the Internet Assigned Numbers Authority (IANA). IANA ensures that addresses are globally unique where needed and has a large address space reserved for use by devices not visible outside their own networks.


---
tags: #ccna #ip #ipv4
links: https://ccnaphilippines.teachable.com/courses/742904/lectures/15878621, https://www.juniper.net/documentation/us/en/software/junos/interfaces-security-devices/topics/topic-map/security-interface-ipv4-ipv6-protocol.html
see also:
created on: 2022-01-28 20:45