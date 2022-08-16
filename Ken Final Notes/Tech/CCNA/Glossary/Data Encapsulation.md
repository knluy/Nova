## Data Encapsulation Terminology

**Definition:**
>In computer networking, encapsulation is a method of designing modular communication protocols in which logically separate functions in the network are abstracted from their underlying structures by inclusion or information hiding within higher-level objects. In other words, encapsulation "`takes information from a higher layer and adds a header to it`, treating the higher layer information as data".
>
>Source: [Encapsulation (networking) - Wikipedia](https://en.wikipedia.org/wiki/Encapsulation_(networking))

The process by which a TCP/IP host sends data can be viewed as a five-step process. The first four steps relate to the encapsulation performed by the four TCP/IP layers, and the last step is the actual physical transmission of the data by the host. The steps are summarized in the following list:


>![[encapsulation.PNG]]
>*Five Steps of Data Encapsulation: TCP/IP*

1. __Create and encapsulate the application data with any required [[application layer]] headers.__ For example, the HTTP OK message can be returned in an HTTP header, followed by part of the contents of a web page.
2. __Encapsulate the data supplied by the application layer inside a [[Transport Layer]] header.__ For end-user applications, a TCP or UDP header is typically used.
3. __Encapsulate the data supplied by the [[Transport Layer]] inside a network layer (IP) header.__ IP defines the IP addresses that uniquely identify each computer.
4. __Encapsulate the data supplied by the network layer inside a data-link layer header and trailer.__ This layer uses both a header and a trailer.
5. __Transmit the bits.__ The physical layer encodes a signal onto the medium to transmit the frame.

---
tags: #ccna #encapsulation #ip 
links: [Encapsulation (networking) - Wikipedia](https://en.wikipedia.org/wiki/Encapsulation_(networking))
see also:
created on: 2021-12-17 11:27
