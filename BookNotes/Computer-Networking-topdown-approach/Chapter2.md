# Chapter 2: Application Layer



#### 2.1 Principles of Network Application

Communication for a network application takes place between end systems at the application layer.

##### 2.1.1 Network Application Architectures

The network architecture is fixed and provides a specifc set of services to applications. The **application architecture** is designed by the application developer and dictates how the application is structured over the various end systems.

predominant architectural paradigms:

- Client-server architecture
- Peer-to-peer architecture



***Client-server architecture***:

There is an always-on host -> *server* which services requests from many other hosts, called *clients*.

​	Note: clients in this paradigm do not directly communicate with each other, the server has a fixed, well-known address, and because the server is always on, a client can always contact the server by sending a packet to the server's IP address. applications with client-server architecture: Web, FTP, Telnet and email.

A single server is incapable of keeping up with all the requests from clients. 

​	For example, a popular social-networking site can quickly become overwhelmed if it has only one server handling all of its requests. For this reason, a **data center**, housing a large number of hosts, is often used to create a powerful virtual server. A data center can have hundreds of thousands of servers which must be powered and maintained. Addtionality, the service providers must pay recurring interconnection and bandwidth costs for sending data from their data centers.



***P2P architecture***: 

peers are not owned by service provider, but are instead desktops and laptops controlled by users, with most of the peers residing in home, universities and offices. Peers communicates without passing through a dedicated server.

​	Features of P2P architectures: 

- Self-scalability: 

  P2P applications face challenges of security, performance and reliability due to their highly decentralized structure.



##### 2.1.2 Processes Communicating

When processes running on the same end system, they can communicate with each other with interprocess communication, using rules that are governed by the end system's operating system

Processes on two different end systems communicates with each other by exchanging messages across the computer network.

A sending process creates and sends messages into the network; a receiving process receives these messages and possibly responds by sending message back



**Client and Server Processes**:

> In the context of a communication session between a pair of processes, the process that initiates the communication (that is, initially contracts the other process at the beginning of the session) is labeled as the client. The process that waits to be contacts to begin the session is the server
>

**The Interface Between the Process nad the Computer Network**:

A process sends messages into, and receives messages from, the network through a software interface called a **socket**. 

A socket is the interface between the application layer and the transport layer within a host. It is also referred to as the **Application programming Interface (API)** between the application and the network. 

The only control that the application developer has on the transport layer side is:

1. The choice of transport protocol
2. perhaps the ability to fix a few transport-layer parameters



**Addressing Processes**:

- Address of the host
- an identifier that specifies the receiving process in the destination host

In the internet, the host is identified by its **IP address**. 

An address is 32 bits quantity, **Port Number** identify the receiving process (more specifically, the receiving socket) running in the host.

- 80 : Web server
- 25 : Mail server

**Transport Services Available to Applications**:

socket is. the interface between the application process and the transport-layer protocol. 

​		The application at the sending side pushes messages through the socket.

​		At the other side of the socket, the transport-layer protocol has the responsibility of getting the messages to the socket of the receiving process.

Four Dimensions:

- reliable data transfer
- throughput
- timing
- security

***reliable data transfer***: 

packets can get lost within a computer network,  For example

1. a packet. can overflow. a buffer in a router
2. packet can be discarded by a host or router after. having some of its bits corrupted.

loss-tolerarnt applications:  when a transport-layer protocol does not provide reliable data transfer, some of the data sent by the sending process may never arrive at the receiving process. Most multimedia applications such as, conversational audio/video that. can tolerate some amount of data loss.



***Throughput***:

**Definition**: rate at which the sending process can deliver bits to the receiving process.



​	Since other sessions will be sharing the bandwidth along the network path

​	Since these other sessions will be coming and going, the available throughput can fluctuate with time.



The application could request a guaranteed throughput of `r bits/sec` and the transport protocol would then ensure that the available throughput is always at least `r bits/sec`. 

​	

​	For example, if an Internet telephony application encodes voice at 32kbps, it needs. to send data into the network and have data delivered to the receiving application at this rate. If the transport protocol cannot provide this throughput, the application would need to encode at a lower rate (and receive enough throughput to sustain this lower coding rate) or may have to give up.

Applications that have throughput requirements are said to be **bandwidth-senstive applications**. Many current multiMedia applications are bandwidth sensitive, although some multimeida applications may use adaptive coding techniques to encode digitized voice or video at a rate that matches the currently available throughput.



**elastic applications** can make use of as much, or as little, throughput as happens to be available. Electronic mail, file transfer, and Web transfers are all elastic applications.



***Timing***:

A transport-layer protocol can also provide timing guarantees. As with throughput guarantees, timing guarantees can come in many shapes and forms.

​		An example guarantee might be that every bit 





















