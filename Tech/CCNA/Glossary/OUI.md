## OUI
**Definition:**
>An organizationally unique identifier (OUI) is a 24-bit number that uniquely identifies a vendor, manufacturer, or other organization.
>
>Source: https://en.wikipedia.org/wiki/Organizationally_unique_identifier


In MAC addresses, the OUI is combined with a 24-bit number (assigned by the assignee of the OUI) to form the address. The first three octets of the address are the OUI.

```md
|            OUI                 |
| Octet 0  | Octet 1  | Octet 2  |
|  nibble  |  nibble  |  nibble  |
|  __||__  |  __||__  |  __||__  |
| |      | | |      | | |      | |
| 0  ||  1 | 2  ||  3 | 4  ||  5 |
|bits||bits|bits||bits|bits||bits|
|7654||3210|7654||3210|7654||3210|
|||||  |||||||||  |||||||||  |||||
|  A     C |  D     E |  4     8 |
|1010  1100|1101  1110|0100  1000|
 |    |  ||                 |   |
 |    |  ||                 |   least-significant-bit of OUI
 |    |  ||                 least-significant-byte of OUI
 |    |  |least-significant-bit of first octet of OUI = I/G or M bit
 |    |  next-to-least-significant-bit of first octet of OUI = U/L or X bit
 |    most-significant-byte of OUI
 most-significant-bit of OUI
```

---
tags: #ccna #mac #switch 
links: [Organizationally unique identifier](https://en.wikipedia.org/wiki/Organizationally_unique_identifier)
see also:
created on: 2021-12-30 09:57