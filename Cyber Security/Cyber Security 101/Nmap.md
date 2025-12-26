### 🔹 Basic Scans

|Command|Comment|
|---|---|
|`nmap target`|Default scan (top ports + host discovery)|
|`nmap 192.168.1.1`|Scan single IP|
|`nmap example.com`|Scan domain|
|`nmap 192.168.1.0/24`|Scan subnet|
|`nmap -iL targets.txt`|Scan targets from file|

---

### 🔹 Host Discovery

|Command|Comment|
|---|---|
|`nmap -sn target`|Ping scan only (no port scan)|
|`nmap -Pn target`|Skip host discovery (assume up)|
|`nmap -PS target`|TCP SYN ping|
|`nmap -PA target`|TCP ACK ping|
|`nmap -PU target`|UDP ping|
|`nmap -PE target`|ICMP echo request|
|`nmap -PP target`|ICMP timestamp|
|`nmap -PM target`|ICMP netmask|

---

### 🔹 Port Scanning

|Command|Comment|
|---|---|
|`nmap -p 80 target`|Scan specific port|
|`nmap -p 1-65535 target`|Scan all ports|
|`nmap -p- target`|Shortcut for all ports|
|`nmap --top-ports 100 target`|Scan top 100 ports|
|`nmap -F target`|Fast scan (top ports)|

---

### 🔹 Scan Types

|Command|Comment|
|---|---|
|`nmap -sS target`|TCP SYN (stealth) scan|
|`nmap -sT target`|TCP connect scan|
|`nmap -sU target`|UDP scan|
|`nmap -sA target`|ACK scan (firewall rules)|
|`nmap -sW target`|Window scan|
|`nmap -sM target`|Maimon scan|
|`nmap -sN target`|TCP Null scan|
|`nmap -sF target`|TCP FIN scan|
|`nmap -sX target`|TCP Xmas scan|

---

### 🔹 Service & Version Detection

|Command|Comment|
|---|---|
|`nmap -sV target`|Detect service versions|
|`nmap -sV --version-intensity 9 target`|Aggressive version detection|
|`nmap -sV --version-light target`|Light version detection|
|`nmap -sV --version-all target`|Try all probes|

---

### 🔹 OS Detection

|Command|Comment|
|---|---|
|`nmap -O target`|OS detection|
|`nmap -O --osscan-guess target`|Aggressive OS guessing|
|`nmap -O --osscan-limit target`|OS detection only on promising targets|

---

### 🔹 NSE Scripts

|Command|Comment|
|---|---|
|`nmap --script default target`|Default safe scripts|
|`nmap --script vuln target`|Vulnerability scan|
|`nmap --script auth target`|Auth related scripts|
|`nmap --script discovery target`|Service discovery|
|`nmap --script safe target`|Non-intrusive scripts|
|`nmap --script intrusive target`|Intrusive scripts|

---

### 🔹 Common NSE Examples

|Command|Comment|
|---|---|
|`nmap --script http-enum target`|Enumerate HTTP services|
|`nmap --script smb-os-discovery target`|SMB OS discovery|
|`nmap --script ftp-anon target`|FTP anonymous login|
|`nmap --script ssh-brute target`|SSH brute force|

---

### 🔹 Aggressive / Combined

|Command|Comment|
|---|---|
|`nmap -A target`|OS, version, scripts, traceroute|
|`nmap -sS -sV -O target`|SYN + version + OS|

---

### 🔹 Firewall / IDS Evasion

|Command|Comment|
|---|---|
|`nmap -f target`|Fragment packets|
|`nmap --mtu 24 target`|Custom MTU|
|`nmap -D RND:10 target`|Decoy scan|
|`nmap --spoof-mac 0 target`|Random MAC|
|`nmap --randomize-hosts`|Random scan order|
|`nmap --data-length 50`|Append random data|

---

### 🔹 Timing & Performance

|Command|Comment|
|---|---|
|`nmap -T0 target`|Paranoid (very slow)|
|`nmap -T1 target`|Sneaky|
|`nmap -T2 target`|Polite|
|`nmap -T3 target`|Normal|
|`nmap -T4 target`|Aggressive|
|`nmap -T5 target`|Insane (very fast)|

---

### 🔹 Output & Debugging

|Command|Comment|
|---|---|
|`nmap -oN out.txt target`|Normal output|
|`nmap -oX out.xml target`|XML output|
|`nmap -oG out.gnmap target`|Grepable output|
|`nmap -oA out target`|All formats|
|`nmap -v target`|Verbose|
|`nmap -vv target`|Very verbose|
|`nmap -d target`|Debug|
|`nmap --reason target`|Show reasons|

---

### 🔹 Misc

|Command|Comment|
|---|---|
|`nmap -6 target`|IPv6 scan|
|`nmap --traceroute target`|Traceroute|
|`nmap --open target`|Show open ports only|

## Scanning (TCP)
#### Connect Scan

The connect scan can be triggered using `-sT`. It tries to complete the TCP three-way handshake with every target TCP port. If the TCP port turns out to be open and Nmap connects successfully, Nmap will tear down the established connection.

#### SYN Scan (Stealth)  

Unlike the connect scan, which tries to **connect** to the target TCP port, i.e., complete a three-way handshake, the SYN scan only executes the first step: it sends a TCP SYN packet. Consequently, the TCP three-way handshake is never completed. The advantage is that this is expected to lead to fewer logs as the connection is never established, and hence, it is considered a relatively stealthy scan. You can select the SYN scan using the `-sS` flag.

## Scanning (UDP)
Nmap offers the option `-sU` to scan for UDP services. Because UDP is simpler than TCP, we expect the traffic to differ.

### OS Detection

You can enable OS detection by adding the `-O` option. As the name implies, the OS detection option triggers Nmap to rely on various indicators to make an educated guess about the target OS.

### Service and Version Detection

You discovered several open ports and want to know what services are listening on them. `-sV` enables version detection.

### Forcing the Scan

When we run our port scan, such as using `-sS`, there is a possibility that the target host does not reply during the host discovery phase (e.g. a host doesn’t reply to ICMP requests).

## Timing
|Timing|Total Duration|
|---|---|
|T0 (paranoid)|9.8 hours|
|T1 (sneaky)|27.53 minutes|
|T2 (polite)|40.56 seconds|
|T3 (normal)|0.15 seconds|
|T4 (aggressive)|0.13 seconds|

|Option|Explanation|
|---|---|
|`-T<0-5>`|Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)|
|`--min-parallelism <numprobes>` and `--max-parallelism <numprobes>`|Minimum and maximum number of parallel probes|
|`--min-rate <number>` and `--max-rate <number>`|Minimum and maximum rate (packets/second)|
|`--host-timeout`|Maximum amount of time to wait for a target host|
