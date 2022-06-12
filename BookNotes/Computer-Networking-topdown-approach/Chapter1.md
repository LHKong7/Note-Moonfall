# Chapter 1 Computer Networks and the Internet



End Systems are connected together by a network of **communication links** and **packet swicthes**. There are different types of physical media, including coxial cable, copper wire, optical fiber and radio spectrum.

Different links can transmit data at different rates with the **transmission rate** of a link measured in bits/second.

> When one end system has data to send to another end system, the sending end system segments the data and adds header bytes to each segment.  The resulting packages of information, known as **packets** are then sent through the network to the destination end system, where they are reassembled into the original data

A packet switch takes a packet arriving on one of its incoming communication links and forwards that packet on one of its outgoing communication links.

Two prominent types of packet switch:

- **routers**
- **link-layer switches**

The sequence of communication links and packet switches traversed by a packet from the sending end system to the receiving end system is known as a **route** or **path** through the network.

End systems access the Internet through **Internet Service Providers(ISPs)** :

- residential ISPs → local cable or telephone companies
- corporate ISPs
- univerisity ISPs
- Cellular data ISPs

Each ISP is in itself a network of packet switches and communication links

End systems, packet swicthes and other pieces of the Internet run **protocol** that control the sending and receiving of information within the Internet. The **Transmission Control Protocol (TCP)** and the **Internet Protocol(IP)** are two of the most important protocols in the Internet.

- The IP protocol specifes the format of the packets that are sent and received among routers and end systems

End systems attached to the Internet provide a **socket interface** that specifies how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end systems.

### Network Protocols

A network protocl: all activities in the Internet that involves two or more communicating remote entities is governed.

A protocol: defines the format and the order of messages exchanged between two or more communicating entities, as well as the actions taken on the transmission and/or receipt of a message or other event

Cable Internet access:

important characteristic → shared broadcast medium

In particular, every packet sent by the head end travels downstream on every link to every home and every packet sent by a home travels on the upstream channel to the head end.

### The Network Core

**Packet Switching**:

In a network application, end systems exchange messages with each other.

Messages may perform a control function or can contain data.

To send a message from a source end system to a destination end system, the source breaks long messages into smaller chunks of data known as **packets**. Between source and destination, each packet travels through communication links and packet swicthes. (for which there are two predominant types, routers and link-layer switches). packet are transmitted over each communication link at a rate equal to the full tranmission rate of the link. So, if a source end system or a packet swicth is sending a packet of L bits over a link with transmission rate R bit/second, then the time to transmit the packet is L/R seconds

**Store-and-Forward Tranmission**:

Most packet swicthes use store-and-forward transmission at the inputs to the links. (routers need to receive, store and process the entire packet before forwarding)

A router will typically have many incident, since its job is to switch an incoming packet onto an outgoing link; The router rather simple task of transferring  a packet from one (input) link to the only other attached link.

***Definition***: The packet switch must receive the entire packet before it can begin to tranmist the first bit of the packet onto the outbound link.

The amount of time that elapses from when the source begins to send the packet until the destination has received the entire packet.

General case of sending one packet from source to the destination over a path consisting of N links each of rate R (there are N-1 routers between source and destination)

$d_{end-to-end} = N*L/R$

**Queue Delays and Packet Loss**:

Each packet switch has multiple links attached to it. For each attached link, the packet switch ahs an **output buffer** (also called an output queue), which stores packets taht the router is about to send into that link. The output buffers play a key role in packet swicthing. If an arriving packet needs to be transmitted onto a link but finds the link busy with the tramission of another packet, the arriving packet must wait in the output buffer.

Packets suffer output buffer queuing delays. These delays are variable and depend on the level of congestion in the network. Since the amount of buffer space is finite, an arriving packet may find that the buffer is completely full with other packets waiting for transmission. In this case, **packet loss** will occur, either the arriving packet or one of the already queued packets will be dropped.

**Circuit Switching**

In circuit-swicthed networks, the resources needed along a path (buffers, link transmission rate) to provide for communication bewteen the end systems are reserved for the duration of the communication session between the end systems.

### Overview of Delay in Packet-swicthed Networks

The most important of these delays are:

- nodal processing delay

  **Definition**: The time required to examine the packet's header and determine where to direct the packet is part of the processing delay. Can also include other factors such as, the time needed to check for bit-level errors in the packet that occurred in tranmitting the packet's bits from the upstream node to router A. Processing delays in high-speed routers are typically on the order of microseconds or less.

- queuing delay

   At the queue, the packet experiences a **queuing delay** as it waits to be transmitted onto the link.

- transmission delay

  Assume that packets are transmitted in a FCFS(first come first server) manner, as is common in packet-swicthed networks, out packet can be transmitted only after all the packets that have arrived before it have been transmitted. 

  The length of packet is L bits, tranmission rate of the link from Router A to Router B by R bit/sec, The transmission delay is L/R

  

- propagation delay

  Once a bit is pushed into the link, it needs to propagate to router B. The time required to propagate from the beginning of the link to router B is the propagation delay.



**Throughput in Computer Networks**

In additional to delay and packet loss, another critical performance measure in computer networks is end-to-end throughput.

The instantaneous throughput at any instant of time is the rate (in bits/sec) at which Host B is receiving the file.

​	For some applications, such as Internet telephony, it is desirable to have a low delay and an instantaneous throughput consistently above some threshold (Over 24kbps for some Internet telephony applications and over 256 kbps for some real-time video applications)



##### Protocol Layers and Their Service Models

**Application Layer**: includes many protocols such as:

-  the HTTP protocol (which provides for web document request and transfer)
- SMTP provides for the transfer of email messages
- FTP provides for the transfer of files between two end systems

An Application layer protocol is distributed over multiple end systems, with the application in one end system using the protocol to exchange packets of information with the application in another end system. We will refer to this packet of information at the application layer as a message.

**Transport Layer**: The internet's transports application-layer messages between application endpoints.

There are two transport protocols, TCP and UDP, either of which can transport application-layer messages.

TCP provides a connection-oriendted service to its applications. This service includes guaranteed delivery of application-layer messages to the destination and flow control (send/receiver speed matching), also break long messages into shorter segments and provides a congestion-control mechanism, so that a source throttles its transmission rate when the network is congested.

UDP protolcol provides a connectionless service to its applications. This is a no-frills service that provides no reliability, no flow control, and no congestion control. 

Transport layer packet => segment

**Network Layer**: is responsible for moving network-layer packets known as datagrams from one host to another.

The Internet's network layer includes the celebrated IP protocol, which defines the fields in the datagram as well as how the end systems and routers act on these field.

​	There is only one IP protocol, and all Internet components that have a network layer must run the IP protocol. The Internet's network layer also contains routing protocol that determine the routes that datagrams take between sources and destinations.



**Link Layer**: The Internet’s network layer routes a datagram through a series of routers between the source and destination. To move a packet from one node (host or router) to the next node in the route, the network layer relies on the services of the link layer. In particular, at each node, the network layer passes the datagram down to the link layer, which delivers the datagram to the next node along the route. At this next node, the link layer passes the datagram up to the network layer

we’ll refer to the link-layer packets as frames.



**Physical Layer**: While the job of the link layer is to move entire frames from one network element to an adjacent network element, the job of the physical layer is to move the individual bits within the frame from one node to the next. The protocols in this layer are again link dependent and further depend on the actual transmission medium of the link (for example, twisted-pair copper wire, single-mode fiber optics). For example, Ethernet has many physical-layer protocols: one for twisted-pair copper wire, another for coaxial cable, another for fiber, and so on. In each case, a bit is moved across the link in a different way.





















