## Subnet Mask

**Definition:**
>A subnet mask is a 32-bit number created by setting host bits to all 0s and setting network bits to all 1s. In this way, the subnet mask separates the IP address into the network and host addresses.
>
>Source: https://avinetworks.com/glossary/subnet-mask/

Note:
Network Portion - to the left
Host Portion - to the right

If this will be converted to binary digit, all 1s will be located at the left while all 0s will be located at the right.

```
                       192   .   168   .    1    .   1

                     11000000.10101000.00000001.00000001
```

>![[subnet mask.PNG]]	

For /22 subnet:

```
                      255  .   255  .   252  .    0
				   11111111.11111111.11111100.00000000

```





---
tags: #ccna #ip #ipv4 
links: https://ccnaphilippines.teachable.com/courses/742904/lectures/15885668, https://avinetworks.com/glossary/subnet-mask/
see also:
created on: 2022-01-28 20:57