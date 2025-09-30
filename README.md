# Wireshark Cheat Sheet

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Raj%20Bhatia-blue)](https://www.linkedin.com/in/raj-bhatia-1790901a8/)

## Overview

Wireshark is a popular network protocol analyzer for recording and analyzing network traffic in real time. It's a free, open-source program that works with Linux, macOS, and Windows, making it an effective tool for cybersecurity investigation, performance optimization, and network troubleshooting.

### Key Features

- **Multi-protocol support**: HTTP, TCP, UDP, DNS, and more
- **Real-time packet capture**: Records data packets moving over wired or wireless network interfaces
- **Deep packet inspection**: Decodes packets into structured, readable formats
- **Advanced filtering**: Filter and search packets by IP addresses, protocol types, or port numbers
- **Visualization tools**: Flow graphs, I/O graphs, and comprehensive data views
- **Extensible**: Supports scripts and plugins
- **Export capabilities**: Save packets in common formats like PCAP and PCAPNG

## Real-World Uses

- **IT Support**: Resolving client or staff connectivity problems
- **Cybersecurity**: Monitoring for vulnerabilities or intrusion attempts
- **DevOps**: Improving service-to-service connectivity in microservices frameworks
- **Education**: Teaching networking and cybersecurity concepts

---

## Basic Operations

| Action | Description | Shortcut/Command |
|--------|-------------|------------------|
| Open a PCAP File | Load a .pcap or .pcapng file for analysis | `File > Open` or `Ctrl + O` |
| Save Filtered Packets | Export filtered packets to a new file | `File > Export Specified Packets` |
| View Detailed Packet Information | Select a packet to see details in the middle and bottom panes | N/A |

---

## Display Filters

### Network Layer Filters

| Filter | Purpose |
|--------|---------|
| `ip.addr == 192.168.1.1` | Display all traffic involving a specific IP address |
| `frame contains "example.com"` | Filter packets containing a specific string |
| `icmp` | Display ICMP traffic (e.g., ping requests) |
| `arp` | Show ARP requests and responses |
| `arp.duplicate-address-frame` | Look for duplicate ARP responses (potential spoofing) |

### Transport Layer Filters

| Filter | Purpose |
|--------|---------|
| `tcp.port == 80` | Show traffic on a specific TCP port (e.g., HTTP) |
| `udp.port == 53` | Show DNS traffic (UDP port 53) |
| `tcp.flags.syn == 1` | Show TCP SYN packets (connection attempts) |
| `tcp.flags.reset == 1` | Display TCP RST packets (connection resets) |

### Application Layer Filters

| Filter | Purpose |
|--------|---------|
| `http` | Display HTTP traffic |
| `ssl` or `tls` | Show SSL/TLS encrypted traffic |
| `dns.flags.response == 1` | Show only DNS responses |

### Troubleshooting Filters

| Filter | Purpose |
|--------|---------|
| `tcp.analysis.retransmission` | Display TCP retransmissions (possible network issues) |
| `tcp.analysis.flags` | Show TCP packets with issues (e.g., retransmissions, resets) |

---

## Analysis Tools

| Tool | Location | Description |
|------|----------|-------------|
| **Protocol Hierarchy** | `Statistics > Protocol Hierarchy` | View breakdown of all protocols in the capture |
| **Conversations** | `Statistics > Conversations` | List all conversations (by IP, MAC, or transport layer) |
| **Endpoints** | `Statistics > Endpoints` | Show endpoints (e.g., IPs, MACs) involved in the traffic |
| **Flow Graph** | `Statistics > Flow Graph` | Visualize the flow of packets between endpoints |
| **I/O Graphs** | `Statistics > I/O Graph` | Plot network traffic over time |
| **Resolved Addresses** | `Statistics > Resolved Addresses` | View hostnames for IPs (if resolved) |
| **Expert Information** | `Analyze > Expert Information` | Highlight errors, warnings, and noteworthy packets |

---

## Follow Stream

| Stream Type | Action | Purpose |
|-------------|--------|---------|
| **TCP Stream** | Right-click a packet > `Follow > TCP Stream` | Reconstruct a TCP conversation between endpoints |
| **UDP Stream** | Right-click a packet > `Follow > UDP Stream` | Reconstruct a UDP conversation |
| **HTTP Stream** | Right-click a packet > `Follow > HTTP Stream` | View HTTP headers and body content in readable format |

---

## Statistics and Analysis

| Analysis Task | Command/Shortcut | Purpose |
|---------------|------------------|---------|
| **Protocol Usage Breakdown** | `Statistics > Protocol Hierarchy` | Identify which protocols dominate the traffic |
| **Communication Details** | `Statistics > Conversations` | See detailed info about communication between hosts |
| **Packet Flow** | `Statistics > Flow Graph` | Analyze the sequence of packets and detect anomalies |
| **Response Times (DNS, HTTP)** | `Statistics > Service Response Time` | Measure response times for DNS and HTTP requests |

---

## Graphing and Visualization

| Tool | Usage | Purpose |
|------|-------|---------|
| **I/O Graphs** | `Statistics > I/O Graph` | Visualize packet rates, bandwidth usage, or custom filters |
| **TCP Stream Graphs** | Right-click a TCP packet > `TCP Stream Graphs` | Analyze round-trip time, throughput, and window scaling |

---

## Common Analysis Scenarios

| Scenario | Filter or Approach |
|----------|-------------------|
| **Detect Port Scanning** | `ip.src == 192.168.1.1 && tcp.flags.syn == 1` |
| **Analyze Slow Connections** | Look for retransmissions: `tcp.analysis.retransmission` or use I/O Graphs |
| **Identify Suspicious Traffic** | Filter for unusual IPs: `!(ip.addr == <trusted network>)` |
| **Examine Downloads** | Follow the HTTP Stream or use `http.file_data` to view file contents |
| **Inspect ARP Spoofing** | Look for duplicate ARP responses: `arp.duplicate-address-frame` |

---

## Keyboard Shortcuts

### File Operations
- **Open Capture File**: `Ctrl + O`
- **Save Capture File**: `Ctrl + S`
- **Close Wireshark**: `Ctrl + Q`

### Capture Control
- **Start/Stop Capture**: `Ctrl + E`
- **Restart Capture**: `Ctrl + R`

### Filters
- **Apply Display Filter**: Press `Enter` in the Filter Bar
- **Clear Display Filter**: `Ctrl + Shift + X`
- **Toggle Between Capture and Display Filters**: `Shift + Ctrl + T`

### Navigating Packets
- **Move to Next Packet**: `↓`
- **Move to Previous Packet**: `↑`
- **Go to First Packet**: `Ctrl + Home`
- **Go to Last Packet**: `Ctrl + End`
- **Jump to Packet**: `Ctrl + G`

### Expand/Collapse Packet Details
- **Expand Packet Details**: `→`
- **Collapse Packet Details**: `←`
- **Expand All Details**: `Shift + →`
- **Collapse All Details**: `Shift + ←`

### View and Layout
- **Show/Hide Packet Details Pane**: `Ctrl + Shift + D`
- **Show/Hide Packet Bytes Pane**: `Ctrl + Shift + B`
- **Zoom In**: `Ctrl + =`
- **Zoom Out**: `Ctrl + -`
- **Reset Zoom**: `Ctrl + 0`

### Find and Search
- **Find Packet**: `Ctrl + F`
- **Repeat Find (Next)**: `Ctrl + N`
- **Repeat Find (Previous)**: `Ctrl + Shift + N`

---

## Contributing

Feel free to submit issues or pull requests to improve this cheat sheet.

## License

This cheat sheet is provided as-is for educational purposes.

## Author

**Raj Bhatia**  
[LinkedIn Profile](https://www.linkedin.com/in/raj-bhatia-1790901a8/)

---

⭐ **Star this repository if you find it helpful!**
