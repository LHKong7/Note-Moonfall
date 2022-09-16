# Chapter 1 Computer Networks and the Internet



End Systems are connected together by a network of **communication links** and **packet swicthes**. There are different types of physical media, including coxial cable, copper wire, optical fiber and radio spectrum.



**Socket interface**: specifies how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end system.



**Network Protocol**: All activity in the Internet that involves two or more communicating remote entities is governed by a protocol. A protocol defines the format and the order of messages exchanged between two or more communicating entities, as well as the actions taken on the tranmission and/or receipt of a message or other event.



**edge router**: The network that physically connects an end system to the first router on a path from the end system to any other distant end system.



**Cable internet**: external device and connects to the home PC through an Ethernet port. At the cable head end, the cable modem termination system (CMTS) serves a similar function as the DSL network's DSLAM turning the analog signal sent from the cable modems in many downstream home back into digital format. ***Shared broadcast medium*** (if multiple users are simultanously download a video file, the actual rate will be lower than downstream rate.)

- Downstream bitrates of 40 Mbps and 1.2 Gbps
- Upstream rates of 30 Mbps and 100 Mbps.



**FTTH**

On corporate and university campuses, and increasingly in home settings, a **local area network (LAN)** is used to connect an end system to the edge router.



**physical media**: twisted-pair copper wire, coaxial cable, multimode fiber-optic cable, terrestrial radio spectrum and satellite radio spectrum. Guided media -> the waves are guided along a solid medium; unguided media -> the waves propagate in the atmosphere and in outer space.



#### Packet Swicthing

**packets**: To send a message from a source end system to a destination end system,  the source breaks long messages into smaller chunks of data.

Between source and destination, each packet travels through communication links and **packet switches** (routers and link-layer swicthes)



##### Store-and-Forward Tranmission

***Definition***: The packet switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the outbound link.



Each packet switch has multiple links attached to it. For each attached link, the packet switch has an output buffer (also called an output queue), which stores packets that the router is about to send into that link. The output buffers play a key role in packet switching. If an arriving packet needs to be transmitted onto a link but finds the link busy with the transmission of another packet, the arriving packet must wait in the output buffer.

**Queuing Delay**: These delays are variable and depend on the level of congestion in the network. Since the amount of buffer space is finite, an arriving packet may find that the buffer is completely full with other packets waiting for tranmission.



#### Circuit Switching

The resources needed along the path (buffers, link transmission rate) to provide for communication between the end systems are reserved for the duration of the communication session between the end systems.





















