[[Networking Fundamentals]]
[[How Web Works]]
#### Types of Ip addreses :
- Public IP addresses
- Private IP addresses

RFC 1918 defines the following three ranges of private IP addresses:

- `10.0.0.0` - `10.255.255.255` (`10/8`)
- `172.16.0.0` - `172.31.255.255` (`172.16/12`)
- `192.168.0.0` - `192.168.255.255` (`192.168/16`)

#### TELNET
The TELNET (Teletype Network) protocol is a network protocol for remote terminal connection. In simpler words, `telnet`, a TELNET client, allows you to connect to and communicate with a remote system and issue text commands. Although initially it was used for remote administration, we can use `telnet` to connect to any server listening on a TCP port number.

On the target virtual machine, different services are running. We will experiment with three of them:

- Echo server: This server echoes everything you send it. By default, it listens on port 7.
- Daytime server: This server listens on port 13 by default and replies with the current day and time.
- Web (HTTP) server: This server listens on TCP port 80 by default and serves web pages.

### Traceroute

It is used to discover the routes between our system and a domain.
Some routers don’t respond; in other words, they drop the packet without sending any ICMP messages. Routers that belong to our ISP might respond, revealing their private IP address. Moreover, some routers respond and show their public IP address, and this would let us look up their domain name and discover their geographic location. Finally, there is always a possibility that an ICMP Time Exceeded message gets blocked and never reaches us.

**TTL :** The Internet protocol has a field called Time-to-Live (TTL) that indicates the maximum number of routers a packet can travel through before it is dropped. The router decrements the packet’s TTL by one before it sends it across. When the TTL reaches zero, the router drops the packet and sends an ICMP Time Exceeded message (ICMP Type `11`).

#### Routing Algorithm 

- **OSPF (Open Shortest Path First)**: OSPF is a routing protocol that allows routers to share information about the network topology and calculate the most efficient paths for data transmission. It does this by having routers exchange updates about the state of their connected links and networks. This way, each router has a complete map of the network and can determine the best routes to reach any destination.
- **EIGRP (Enhanced Interior Gateway Routing Protocol)**: EIGRP is a Cisco proprietary routing protocol that combines aspects of different routing algorithms. It allows routers to share information about the networks they can reach and the cost (like bandwidth or delay) associated with those routes. Routers then use this information to choose the most efficient paths for data transmission.
- **BGP (Border Gateway Protocol)**: BGP is the primary routing protocol used on the Internet. It allows different networks (like those of Internet Service Providers) to exchange routing information and establish paths for data to travel between these networks. BGP helps ensure data can be routed efficiently across the Internet, even when traversing multiple networks.
- **RIP (Routing Information Protocol)**: RIP is a simple routing protocol often used in small networks. Routers running RIP share information about the networks they can reach and the number of hops (routers) required to get there. As a result, each router builds a routing table based on this information, choosing the routes with the fewest hops to reach each destination.

#### NAT (Network Address Translation)
The idea behind NAT lies in using **one public IP address** to provide Internet access to **many private IP addresses**. In other words, if you are connecting a company with twenty computers, you can provide Internet access to all twenty computers by using a single public IP address instead of twenty public IP addresses.
Unlike routing, which is the natural way to route packets to the destination host, routers that support NAT must find a way to track ongoing connections. Consequently, NAT-supporting routers maintain a table translating network addresses between internal and external networks. Generally, the internal network would use a private IP address range, while the external network would use a public IP address.

#### Whois
WHOIS record provides information about the entity that registered a domain name, including name, phone number, email, and address. In the screenshot shown below, you can see when the record was first created and when it was last updated. Moreover, you can find the registrant’s name, address, phone, and email.

## Networking Protocols

#### FTP
File Transfer Protocol (FTP) is designed to transfer files. As a result, FTP is very efficient for file transfer, and when all conditions are equal, it can achieve higher speeds than HTTP.
FTP server listens on TCP port 21 by default; data transfer is conducted via another connection from the client to the server.

#### SMTP
Simple Mail Transfer Protocol (SMTP) defines how a mail client talks with a mail server and how a mail server talks with another.

#### POP3
The Post Office Protocol version 3 (POP3) is designed to allow the client to communicate with a mail server and retrieve email messages.

#### IMAP
Internet Message Access Protocol allows synchronizing read, moved, and deleted messages. IMAP is quite convenient when you check your email via multiple clients. Unlike POP3, which tends to minimize server storage as email is downloaded and deleted from the remote server, IMAP tends to use more storage as email is kept on the server and synchronized across the email clients.

## Networking Security protocol

#### TLS
In the early 1990s, Netscape Communications recognised the need for secure communication on the World Wide Web. They eventually developed SSL (Secure Sockets Layer) and released SSL 2.0 in **1995** as the first public version. In **1999**, the Internet Engineering Task Force (IETF) developed TLS (Transport Layer Security). Although very similar, TLS 1.0 was an upgrade to SSL 3.0 and offered various improved security measures. In **2018**, TLS had a significant overhaul of its protocol and TLS 1.3 was released. The purpose is not to remember the exact dates but to realise the amount of work and time put into developing the current version of TLS, i.e., TLS 1.3. Over more than two decades, there have been many things to learn from and improve with every version.

Nowadays, tens of protocols have received security upgrades with the simple addition of TLS. Examples include HTTP, DNS, MQTT, and SIP, which have become HTTPS, DoT (DNS over TLS), MQTTS, and SIPS, where the appended “S” stands for Secure due to the use of SSL/TLS. In the following tasks, we will visit HTTPS, SMTPS, POP3S, and IMAPS.

#### HTTP over TLS
HTTPS stands for Hypertext Transfer Protocol Secure. It is basically HTTP over TLS. Consequently, requesting a page over HTTPS will require the following three steps (after resolving the domain name):

1. Establish a TCP three-way handshake with the target server
2. Establish a TLS session
3. Communicate using the HTTP protocol; for example, issue HTTP requests, such as `GET / HTTP/1.1`

Adding TLS to HTTP leads to all the packets being encrypted. We can no longer see the contents of the exchanged packets unless we get access to the private key.

#### SMTPS, POP3S, and IMAPS
Adding TLS to SMTP, POP3, and IMAP is no different than adding TLS to HTTP. Similar to how HTTP gets an appended S for _Secure_ and becomes HTTPS, SMTP, POP3, and IMAP become SMTPS, POP3S, and IMAPS, respectively.

The insecure versions use the default TCP port numbers shown in the table below:

|Protocol|Default Port Number|
|---|---|
|HTTP|80|
|SMTP|25|
|POP3|110|
|IMAP|143|

The secure versions, i.e., over TLS, use the following TCP port numbers by default:

|Protocol|Default Port Number|
|---|---|
|HTTPS|443|
|SMTPS|465 and 587|
|POP3S|995|
|IMAPS|993|

#### SSH
Secure Shell (SSH) protocol and released SSH-1 in **1995** as freeware. (Interestingly, it was the same year that Netscape Communications released the SSL 2.0 protocol.) A more secure version, SSH-2, was defined in 1996. In **1999**, the OpenBSD developers released OpenSSH, an open-source implementation of SSH. Nowadays, when you use an SSH client, it is most likely based on OpenSSH libraries and source code.

OpenSSH offers several benefits. We will list a few key points:

- **Secure authentication**: Besides password-based authentication, SSH supports public key and two-factor authentication.
- **Confidentiality**: OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it notifies you of new server keys to protect against man-in-the-middle attacks.
- **Integrity**: In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
- **Tunneling**: SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a VPN-like connection.
- **X11 Forwarding**: If you connect to a Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.

#### SFTP and FTPS
SFTP stands for SSH File Transfer Protocol and allows secure file transfer. It is part of the SSH protocol suite and shares the same port number, 22. If enabled in the OpenSSH server configuration, you can connect using a command such as `sftp username@hostname`. Once logged in, you can issue commands such as `get filename` and `put filename` to download and upload files, respectively. Generally speaking, SFTP commands are Unix-like and can differ from FTP commands.

SFTP should not be confused with FTPS. You are right to think that FTPS stands for File Transfer Protocol Secure. How is FTPS secured? Yes, you are correct to estimate that it is secured using TLS, just like HTTPS. While FTP uses port 21, FTPS usually uses port 990. It requires certificate setup, and it can be tricky to allow over strict firewalls as it uses separate connections for control and data transfer.

#### VPN

A **Virtual Private Network (VPN)** is a networking technology that creates a **secure, encrypted tunnel** over an untrusted network (typically the Internet) to allow private data transmission as if the device were directly connected to a private network.

- **Tunneling:** VPNs encapsulate original IP packets inside new packets using tunneling protocols, enabling secure transport across public networks.
- **Encryption:** Data confidentiality is ensured using cryptographic algorithms such as **AES-128/256**, **ChaCha20**, or **3DES**.
- **Authentication:** VPN endpoints authenticate using **pre-shared keys (PSK)**, **digital certificates (X.509)**, or **username/password** mechanisms.
- **Protocols:**
    
    - **IPsec (IKEv1/IKEv2):** Operates at the network layer; provides encryption, integrity, and authentication.
    - **SSL/TLS VPN:** Works at the transport layer; commonly used for remote access via browsers.
    - **OpenVPN:** Open-source, uses TLS and supports UDP/TCP.
    - **WireGuard:** Modern, lightweight protocol using state-of-the-art cryptography.
- **Key Exchange:** Secure key negotiation is handled using **Diffie–Hellman (DH)** or **Elliptic Curve Diffie–Hellman (ECDH)**.

- **Modes of Operation:**
    
    - **Site-to-Site VPN:** Connects entire networks.
    - **Remote Access VPN:** Connects individual clients to a private network.
- **Network Effects:** VPNs can change the client’s **virtual IP address**, enable **secure routing**, and provide **access control** via firewall rules.

VPNs are widely used for **secure remote access**, **data protection**, **privacy enhancement**, and **bypassing network restrictions** in enterprise and personal networking environments.