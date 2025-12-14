The first iteration of the Internet was within the ARPANET project in the late 1960s. This project was funded by the United States Defence Department and was the first documented network in action. However, it wasn't until 1989 when the Internet as we know it was invented by Tim Berners-Lee by the creation of the World Wide Web (WWW). It wasn't until this point that the Internet started to be used as a repository for storing and sharing information, just like it is today.

###### IP Address
IP address (or Internet Protocol) address can be used as a way of identifying a host on a network for a period of time, where that IP address can then be associated with another device without the IP address changing. 
Public IP addresses are given by your **I**nternet **S**ervice **P**rovider (or **ISP**) at a monthly fee (your bill!)

IPv6 is a new iteration of the Internet Protocol addressing scheme to help tackle this issue. Although it is seemingly more daunting, it boasts a few benefits:

- Supports up to 2^128 of IP addresses (340 trillion-plus), resolving the issues faced with IPv4
- More efficient due to new methodologies

###### MAC Addresses
Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built at, called a MAC (Media Access Control ) address. The MAC address is a twelve-character hexadecimal number (a base sixteen numbering system used in computing to represent numbers) split into two's and separated by a colon. These colons are considered separators. For example, a4:c3:f0:85:ac:2d. The first six characters represent the company that made the network interface, and the last six is a unique number.

###### Ping
Ping is one of the most fundamental network tools available to us. Ping uses ICMP (Internet Control Message Protocol) packets to determine the performance of a connection between devices.
This measuring is done using ICMP's echo packet and then ICMP's echo reply from the target device.


#### LAN
A Local Area Network (LAN) is a computer network that interconnects devices within a limited geographical area, such as a home, office, building, or campus.

###### LAN Topologies
- Star
- Bus
- Ring
- Mesh
- Tree
- Hybrid

###### Hubs
Hubs are simple networking devices with an input Ethernet port that connects to a router and multiple output ports for devices to connect. When a hub receives data, it transmits it to all connected devices, leaving the intended device to recognize the data. 

###### Switch 
Switches are dedicated devices within a network that are designed to aggregate multiple other devices such as computers, printers, or any other networking-capable device using ethernet. These various devices plug into a switch's port. Switches are usually found in larger networks such as businesses, schools, or similar-sized networks, where there are many devices to connect to the network. Switches can connect a large number of devices by having ports of 4, 8, 16, 24, 32, and 64 for devices to plug into.

###### Router
A router is a networking device that forwards data packets between computer networks, including internetworks such as the global Internet.

#### Subnetting
Network administrators use subnetting to categorise and assign specific parts of a network to reflect this. Subnetting is achieved by splitting up the number of hosts that can fit within the network, represented by a number called a subnet mask.

| **Type**        | **Purpose**                                                                                                                                    | **Explanation**                                                                                                                                                                                                                                      | **Example**   |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| Network Address | This address identifies the start of the actual network and is used to identify a network's existence.                                         | For example, a device with the IP address of 192.168.1.100 will be on the network identified by 192.168.1.0                                                                                                                                          | 192.168.1.0   |
| Host Address    | An IP address here is used to identify a device on the subnet                                                                                  | For example, a device will have the network address of 192.168.1.1                                                                                                                                                                                   | 192.168.1.100 |
| Default Gateway | The default gateway address is a special address assigned to a device on the network that is capable of sending information to another network | Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device. These devices can use any host address but usually use either the first or last host address in a network (.1 or .254) | 192.168.1.254 |

#### ARP (Address Resolution Protocol)
**A**ddress **R**esolution **P**rotocol or **ARP** for short, is the technology that is responsible for allowing devices to identify themselves on a network.

When an ARP request is sent, a message is broadcasted on the network to other devices asking, "What is the mac address that owns this IP address?" When the other devices receive that message, they will only respond if they own that IP address and will send an ARP reply with its MAC address. The requesting device can now remember this mapping and store it in its ARP cache for future use.


#### DHCP (**D**ynamic **H**ost **C**onfiguration **P**rotocol)
IP addresses can be assigned either manually, by entering them physically into a device, or automatically and most commonly by using a **DHCP** (**D**ynamic **H**ost **C**onfiguration **P**rotocol) server.
When a device connects to a network, if it has not already been manually assigned an IP address, it sends out a request (DHCP Discover) to see if any DHCP servers are on the network. The DHCP server then replies back with an IP address the device could use (DHCP Offer). The device then sends a reply confirming it wants the offered IP Address (DHCP Request), and then lastly, the DHCP server sends a reply acknowledging this has been completed, and the device can start using the IP Address (DHCP ACK).

# OSI Model
The OSI model (or Open Systems Interconnection Model) is an essential model used in networking.  This critical model provides a framework dictating how all networked devices will send, receive and interpret data.
OSI Model has 7 layers at every individual layer that data travels through, specific processes take place, and pieces of information are added to this data that this process is called encapsulation.

#### Layers of OSI model :

- **Physical :** This layer references the physical components of the hardware used in networking and is the lowest layer that you will find. Devices use electrical signals to transfer data between each other in a binary numbering system (1's and 0's).

- **Data Link :** The data link layer focuses on the physical addressing of the transmission. It receives a packet from the network layer (including the IP address for the remote computer) and adds in the physical **MAC** (Media Access Control) address of the receiving endpoint. Inside every network-enabled computer is a **N**etwork **I**nterface Card (**NIC**) which comes with a unique MAC address to identify it. It’s also the job of the data link layer to present the data in a format suitable for transmissiot’s also the job of the data link layer to present the data in a format suitable for transmission.

-  **Network :** The third layer of the OSI model (network layer) is where routing & re-assembly of data takes place (from these small chunks to the larger chunk). Some protocols at this layer determine exactly what is the "optimal" path that data should take to reach a device, these protocols include **OSPF** (**O**pen **S**hortest **P**ath **F**irst) and **RIP** (**R**outing **I**nformation **P**rotocol).

- **Transport :** Layer 4 of the OSI model plays a vital part in transmitting data across a network.

**TCP :** The **T**ransmission **C**ontrol **P**rotocol (**TCP**). Potentially hinted by the name, this protocol is designed with reliability and guarantee in mind. This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.

| **Advantages of TCP**                                                                    | **Disadvantages of TCP  <br>**                                                                                                                    |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Guarantees the accuracy of data.                                                         | Requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used. |
| Capable of synchronising two devices to prevent each other from being flooded with data. | A slow connection can bottleneck another device as the connection will be reserved on the receiving computer the whole time.                      |
| Performs a lot more processes for reliability.                                           | TCP is significantly slower than UDP because more work has to be done by the devices using this protocol.                                         |

**UDP :** User Datagram Protocol (or UDP for short). This protocol is not nearly as advanced as its brother - the TCP protocol. It doesn't boast the many features offered by TCP, such as error checking and reliability. In fact, any data that gets sent via UDP is sent to the computer whether it gets there or not. There is no synchronisation between the two devices or guarantee.

| **Advantages of UDP**                                                                                                 | **Disadvantages of UDP**                                                           |
| --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| UDP is much faster than TCP.                                                                                          | UDP doesn't care if the data is received.                                          |
| UDP leaves the application layer (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense.                         |
| UDP does not reserve a continuous connection on a device as TCP does.                                                 | This means that unstable connections result in a terrible experience for the user. |

- **Session :** Once data has been correctly translated or formatted from the presentation layer (layer 6), the session layer (layer 5) will begin to create and maintain the connection to other computer for which the data is destined. When a connection is established, a session is created. Whilst this connection is active, so is the session. The session layer is also responsible for closing the connection if it hasn't been used in a while or if it is lost. Additionally, a session _can_ contain "checkpoints," where if the data is lost, only the newest pieces of data are required to be sent, saving bandwidth.

- **Presentation :** Layer 6 of the OSI model is the layer in which standardisation starts to take place. Because software developers can develop any software such as an email client differently, the data still needs to be handled in the same way — no matter how the software works. This layer acts as a translator for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.  Examples of the session layer are Network File System (NFS) and Remote Procedure Call (RPC).

- **Application :** Application Layer of OSI (Open System Interconnection) model, is the top layer in this model and takes care of network communication. It provides the functionality to send and receive data from users. It acts as the interface between the user and the application.

| Layer Number | Layer Name         | Main Function                                         | Example Protocols and Standards           |
| ------------ | ------------------ | ----------------------------------------------------- | ----------------------------------------- |
| Layer 7      | Application layer  | Providing services and interfaces to applications     | HTTP, FTP, DNS, POP3, SMTP, IMAP          |
| Layer 6      | Presentation layer | Data encoding, encryption, and compression            | Unicode, MIME, JPEG, PNG, MPEG            |
| Layer 5      | Session layer      | Establishing, maintaining, and synchronising sessions | NFS, RPC                                  |
| Layer 4      | Transport layer    | End-to-end communication and data segmentation        | UDP, TCP                                  |
| Layer 3      | Network layer      | Logical addressing and routing between networks       | IP, ICMP, IPSec                           |
| Layer 2      | Data link layer    | Reliable data transfer between adjacent nodes         | Ethernet (802.3), WiFi (802.11)           |
| Layer 1      | Physical layer     | Physical data transmission media                      | Electrical, optical, and wireless signals |


#### Packets and Frames

A **packet** is a piece of data from Layer 3 (Network Layer) of the OSI model, containing information such as an IP header and payload. A **frame**, however, is used at Layer 2 (Data Link) of the OSI model, which, encapsulates the packet and adds additional information such as MAC addresses.
Packets are an efficient way of communicating data across networked devices. Because this data is exchanged in small pieces, there is less chance of bottlenecking occurring across a network than large messages being sent at once.

#### TCP/IP

This protocol is very similar to the OSI model. The TCP/IP protocol consists of four layers and is arguably just a summarised version of the OSI model. These layers are:

| Layer Number | ISO OSI Model      | TCP/IP Model (RFC 1122) | Protocols                                        |
| ------------ | ------------------ | ----------------------- | ------------------------------------------------ |
| 7            | Application Layer  | Application Layer       | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH, |
| 6            | Presentation Layer |                         |                                                  |
| 5            | Session Layer      |                         |                                                  |
| 4            | Transport Layer    | Transport Layer         | TCP, UDP                                         |
| 3            | Network Layer      | Internet Layer          | IP, ICMP, IPSec                                  |
| 2            | Data Link Layer    | Link Layer              | Ethernet 802.3, WiFi 802.11                      |
| 1            | Physical Layer     |                         |                                                  |

One defining feature of TCP is that it is connection-based, which means that TCP must establish a connection between both a client and a device acting as a server before data is sent.

TCP packets contain various sections of information known as headers that are added from encapsulation. Let's explain some of the crucial headers in the table below:

| Header                 | Description                                                                                                                                                                                                                                         |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source Port            | This value is the port opened by the sender to send the TCP packet from. This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time).                                                                      |
| Destination Port       | This value is the port number that an application or service is running on the remote host (the one receiving data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random.                       |
| Source IP              | This is the IP address of the device that is sending the packet.                                                                                                                                                                                    |
| Destination IP         | This is the IP address of the device that the packet is destined for.                                                                                                                                                                               |
| Sequence Number        | When a connection occurs, the first piece of data transmitted is given a random number. We'll explain this more in-depth further on.                                                                                                                |
| Acknowledgement Number | After a piece of data has been given a sequence number, the number for the next piece of data will have the sequence number + 1. We'll also explain this more in-depth further on.                                                                  |
| Checksum               | This value is what gives TCP integrity. A mathematical calculation is made where the output is remembered. When the receiving device performs the mathematical calculation, the data must be corrupt if the output is different from what was sent. |
| Data                   | This header is where the data, i.e. bytes of a file that is being transmitted, is stored.                                                                                                                                                           |
| Flag                   | This header determines how the packet should be handled by either device during the handshake process. Specific flags will determine specific behaviours, which is what we'll come on to explain below.                                             |
_Three-way handshake -_ the term given for the process used to establish a connection between two devices. The Three-way handshake communicates using a few special messages - the table below highlights the main ones:

| **Step** | **Message** | **Description**                                                                                                                                                                                                                                    |
| -------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1        | SYN         | A SYN message is the initial packet sent by a client during the handshake. This packet is used to initiate a connection and synchronise the two devices together (we'll explain this further later on).                                            |
| 2        | SYN/ACK     | This packet is sent by the receiving device (server) to acknowledge the synchronisation attempt from the client.                                                                                                                                   |
| 3        | ACK         | The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received.                                                                                            |
| 4        | DATA        | Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message.                                                                                                                                             |
| 5        | FIN         | This packet is used to _cleanly (properly)_ close the connection after it has been complete.                                                                                                                                                       |
| #        | RST         | This packet abruptly ends all communication. This is the last resort and indicates there was some problem during the process. For example, if the service or application is not working correctly, or the system has faults such as low resources. |

#### UDP/IP
The **U**ser **D**atagram **P**rotocol (**UDP**) is another protocol that is used to communicate data between devices.
Unlike its brother TCP, UDP is a **stateless** protocol that doesn't require a constant connection between the two devices for data to be sent.

  
UDP packets are much simpler than TCP packets and have fewer headers. However, both protocols share some standard headers, which are what is annotated in the table below:

| **Header**          | **Description**                                                                                                                                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time to Live (TTL)  | This field sets an expiry timer for the packet, so it doesn't clog up your network if it never manages to reach a host or escape!                                                                                                 |
| Source Address      | The IP address of the device that the packet is being sent from, so that data knows where to return to.                                                                                                                           |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next.                                                                                                                                      |
| Source Port         | This value is the port that is opened by the sender to send the UDP packet from. This value is randomly chosen (out of the ports from 0-65535 that aren't already in use at the time).                                            |
| Destination Port    | This value is the port number that an application or service is running on the remote host (the one receiving the data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random. |
| Data                | This header is where data, i.e. bytes of a file that is being transmitted, is stored.                                                                                                                                             |

#### Ports
Ports are virtual places within an operating system where network connections start and end. Ports are a numerical value between **0** and **65535** (65,535).

| **Protocol**                                                       | **Port Number** | **Description**                                                                                                                                            |
| ------------------------------------------------------------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **F**ile **T**ransfer **P**rotocol (**FTP**)                       | 21              | This protocol is used by a file-sharing application built on a client-server model, meaning you can download files from a central location.                |
| **S**ecure **Sh**ell (**SSH**)                                     | 22              | This protocol is used to securely login to systems via a text-based interface for management.                                                              |
| **H**yper**T**ext Transfer Protocol (**HTTP**)                     | 80              | This protocol powers the World Wide Web (WWW)! Your browser uses this to download text, images and videos of web pages.                                    |
| **H**yper**T**ext **T**ransfer **P**rotocol **S**ecure (**HTTPS**) | 443             | This protocol does the exact same as above; however, securely using encryption.                                                                            |
| **S**erver **M**essage **B**lock (**SMB**)                         | 445             | This protocol is similar to the File Transfer Protocol (FTP); however, as well as files, SMB allows you to share devices like printers.                    |
| **R**emote **D**esktop **P**rotocol (**RDP**)                      | 3389            | This protocol is a secure means of logging in to a system using a visual desktop interface (as opposed to the text-based limitations of the SSH protocol). |
List of common ports : https://www.vmaxx.net/techinfo/ports.htm

**Port Forwarding :** Port forwarding is an essential component in connecting applications and services to the Internet. Without port forwarding, applications and services such as web servers are only available to devices within the same direct network.

#### Firewall
A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can configure a firewall to **permit** or **deny** traffic from entering or exiting a network based on numerous factors such as:

- Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
- Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
- What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
- What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is UDP, TCP or both?)

| **Firewall Category** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Stateful              | This type of firewall uses the entire information from a connection; rather than inspecting an individual packet, this firewall determines the behaviour of a device **based upon the entire connection**.<br><br>This firewall type consumes many resources in comparison to stateless firewalls as the decision making is dynamic. For example, a firewall could allow the first parts of a TCP handshake that would later fail.<br><br>If a connection from a host is bad, it will block the entire device.                                                                                                                                      |
| Stateless             | This firewall type uses a static set of rules to determine whether or not **individual packets** are acceptable or not. For example, a device sending a bad packet will not necessarily mean that the entire device is then blocked.<br><br>Whilst these firewalls use much fewer resources than alternatives, they are much dumber. For example, these firewalls are only effective as the rules that are defined within them. If a rule is not exactly matched, it is effectively useless.<br><br>However, these firewalls are great when receiving large amounts of traffic from a set of hosts (such as a Distributed Denial-of-Service attack) |

#### VPN
A **V**irtual **P**rivate **N**etwork (or **VPN** for short) is a technology that allows devices on separate networks to communicate securely by creating a dedicated path between each other over the Internet (known as a tunnel). Devices connected within this tunnel form their own private network.

| **VPN Technology** | **Description**                                                                                                                                                                                                                                                                                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PPP                | This technology is used by PPTP (explained below) to allow for authentication and provide encryption of data. VPNs work by using a private key and public certificate (similar to **SSH**). A private key & certificate must match for you to connect.<br><br>This technology is not capable of leaving a network by itself (non-routable). |
| PPTP               | The **P**oint-to-**P**oint **T**unneling **P**rotocol (**PPTP**) is the technology that allows the data from PPP to travel and leave a network. <br><br>PPTP is very easy to set up and is supported by most devices. It is, however, weakly encrypted in comparison to alternatives.                                                       |
| IPSec              | Internet Protocol Security (IPsec) encrypts data using the existing **I**nternet **P**rotocol (**IP**) framework.<br><br>IPSec is difficult to set up in comparison to alternatives; however, if successful, it boasts strong encryption and is also supported on many devices.                                                             |
#### VLAN 
**VLAN** (**V**irtual **L**ocal **A**rea **N**etwork) allows specific devices within a network to be virtually split up. This split means they can all benefit from things such as an Internet connection but are treated separately. This network separation provides security because it means that rules in place determine how specific devices communicate with each other.