## TCP Error Recovery Basics

![[tcp error recovery.PNG | 500]]
*TCP Error-Recovery Services as Provided to HTTP*



---

Figure shows web server Larry sending a web page to web browser Bob, using three separate messages. Note that this figure shows the same HTTP headers as Figure 1-6, but it also shows a TCP header. The TCP header shows a sequence number (SEQ) with each message. 

In this example, the network has a problem, and the network fails to deliver the TCP message (called a segment) with sequence number 2. When Bob receives messages with sequence numbers 1 and 3, but does not receive a message with sequence number 2, Bob realizes that message 2 was lost. That realization by Bob’s TCP logic causes Bob to send a TCP segment back to Larry, asking Larry to send message 2 again.


---
tags: #ccna #tcpip 
links:
see also:
created on: 2021-12-17 12:28