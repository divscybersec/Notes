Wireshark is one of the most potent traffic analyser tools available in the wild. There are multiple purposes for its use:

- Detecting and troubleshooting network problems, such as network load failure points and congestion.
- Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
- Investigating and learning protocol details, such as response codes and payload data.

Note: Wireshark is not an Intrusion Detection System (IDS). It only allows analysts to discover and investigate the packets in depth. It also doesn't modify packets; it reads them. Hence, detecting any anomaly or network problem highly relies on the analyst's knowledge and investigation skills.

## GUI and Data

Wireshark GUI opens with a single all-in-one page, which helps users investigate the traffic in multiple ways. At first glance, five sections stand out.

| **Toolbar**                       | The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging.                                                                         |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Display Filter Bar**            | The main query and filtering section.                                                                                                                                                                                                |
| **Recent Files**                  | List of the recently investigated files. You can recall listed files with a double-click.                                                                                                                                            |
| **Capture Filter and Interfaces** | Capture filters and available sniffing points (network interfaces).  The network interface is the connection point between a computer and a network. The software connection (e.g., lo, eth0 and ens33) enables networking hardware. |
| **Status Bar**                    | Tool status, profile and numeric packet information.                                                                                                                                                                                 |

Packet details are shown in three different panes, which allow us to discover them in different formats. 

| Packet List Pane     | Summary of each packet (source and destination addresses, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels. |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Packet Details Panel | Detailed protocol breakdown of the selected packet.                                                                                                                                                                                  |
| Packet Bytes Pane    | Hex and decoded ASCII representation of the selected packet. It highlights the packet field depending on the clicked section in the details pane.                                                                                    |

## Layers of packets
`frame/packet`,`source [MAC]`,`source [IP]`,`protocol`,`protocol errors`, `application protocol`, and `application data`

## Packet Navigation

- Packet Number 
- Go to packet
- find packets
- mark packets
- packet comments
- export packets
- Export Objects (Files)
#### Expert Info

Wireshark also detects specific states of protocols to help analysts easily spot possible anomalies and problems. Note that these are only suggestions, and there is always a chance of having false positives/negatives. Expert info can provide a group of categories in three different severities. Details are shown in the table below.

|              |            |                                                          |
| ------------ | ---------- | -------------------------------------------------------- |
| **Severity** | **Colour** | **Info**                                                 |
| **Chat**     | **Blue**   | Information on usual workflow.                           |
| **Note**     | **Cyan**   | Notable events like application error codes.             |
| **Warn**     | **Yellow** | Warnings like unusual error codes or problem statements. |
| **Error**    | **Red**    | Problems like malformed packets.                         |

Frequently encountered information groups are listed in the table below. You can refer to [Wireshark's official documentation](https://www.wireshark.org/docs/) for more information on the expert information entries.

|              |                          |                |                            |
| ------------ | ------------------------ | -------------- | -------------------------- |
| **Group**    | **Info**                 | **Group**      | **Info**                   |
| **Checksum** | Checksum errors          | **Deprecated** | Deprecated protocol usage  |
| **Comment**  | Packet comment detection | **Malformed**  | Malformed packet detection |
## Packet Navigation

- Apply as filter
- Conversation filter
- colourise conversation
- prepare as filter
- apply as column
- follow stream!@#