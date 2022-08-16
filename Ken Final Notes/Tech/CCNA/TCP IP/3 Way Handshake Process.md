## 3 Way Handshake Process


- **Step 1 (SYN):** In the first step, the client wants to establish a connection with a server, so it sends a segment with [[SYN]](Synchronize Sequence Number) which informs the server that the client is likely to start communication and with what sequence number it starts segments with.


- **Step 2 (SYN + ACK):** Server responds to the client request with SYN-ACK signal bits set. Acknowledgement(ACK) signifies the response of the segment it received and [[SYN]] signifies with what sequence number it is likely to start the segments with


- **Step 3 (ACK):** In the final part client acknowledges the response of the server and they both establish a reliable connection with which they will start the actual data transfer


>![[3wayhandshake.PNG]]
>*3 Way Handshake Process*


---
tags: #ccna #tcp #ip #3wayhandshake
links: [TCP 3-Way Handshake Process](https://www.geeksforgeeks.org/tcp-3-way-handshake-process/)
see also: [[TCP]]
created on: 2021-12-18 10:56