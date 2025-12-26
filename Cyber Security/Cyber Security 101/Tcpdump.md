 The Tcpdump tool and its `libpcap` library are written in C and C++ and were released for Unix-like systems in the late 1980s or early 1990s. Consequently, they are very stable and offer optimal speed. The `libpcap` library is the foundation for various other networking tools today. Moreover, it was ported to MS Windows as `winpcap`.

|Option|Description|
|---|---|
|`-i <iface>`|Capture packets on a specific interface|
|`-n`|Disable DNS name resolution|
|`-nn`|Disable DNS and port name resolution|
|`-c <count>`|Stop after capturing specified number of packets|
|`-v`|Verbose output|
|`-vv`|More verbose output|
|`-vvv`|Maximum verbosity|
|`-A`|Print packet contents in ASCII|
|`-X`|Show packet contents in hex and ASCII|
|`-XX`|Show packet contents with Ethernet header|
|`-e`|Display link-level (MAC) headers|
|`-q`|Less verbose (quiet) output|
|`-tttt`|Print full timestamp with date|
|`-S`|Print absolute TCP sequence numbers|
|`-l`|Line-buffered output (useful for piping)|
|`-D`|List available interfaces|
|`-w <file>`|Write captured packets to a file|
|`-r <file>`|Read packets from a capture file|
|`-s <size>`|Set snapshot length (bytes captured per packet)|
|`-B <size>`|Set capture buffer size|
|`-p`|Disable promiscuous mode|
|`--immediate-mode`|Capture packets immediately|
|`inbound`|Capture only incoming traffic|
|`outbound`|Capture only outgoing traffic|
|`tcp`|Capture only TCP packets|
|`udp`|Capture only UDP packets|
|`icmp`|Capture only ICMP packets|
|`arp`|Capture only ARP packets|
|`host <ip>`|Capture traffic to/from a specific host|
|`src host <ip>`|Capture traffic from a source host|
|`dst host <ip>`|Capture traffic to a destination host|
|`port <port>`|Capture traffic on a specific port|
|`portrange a-b`|Capture traffic within a port range|
|`net <cidr>`|Capture traffic from a network|