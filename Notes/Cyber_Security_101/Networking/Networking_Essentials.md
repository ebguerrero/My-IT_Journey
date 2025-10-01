# Networking Essentials

Explore networking protocols from automatic configuration to routing packets to the destination.

---

## 📘 Learning Objectives
This room will teach you how to:
- Understand Dynamic Host Configuration Protocol (DHCP).
- Explore Address Resolution Protocol (ARP).
- Troubleshoot using Internet Control Message Protocol (ICMP).
- Learn routing concepts and Network Address Translation (NAT).
- Recognize how these protocols glue networks together.

---

## Task 1 – Introduction
Networking Essentials is the second room in the TryHackMe networking path.  
It builds upon Networking Concepts and prepares you for **Networking Core Protocols** and **Networking Secure Protocols**.

**Prerequisites**:  
- ISO OSI model and layers  
- TCP/IP model and layers  
- Ethernet, IP, and TCP protocols  

**Protocols covered**:  
- DHCP (Dynamic Host Configuration Protocol)  
- ARP (Address Resolution Protocol)  
- NAT (Network Address Translation)  
- ICMP (Internet Control Message Protocol)  
  - Includes **ping** and **traceroute**

---

## Task 2 – DHCP: Give Me My Network Settings
When a device connects to a network, it needs:  
- IP address (with subnet mask)  
- Router/gateway  
- DNS server  

Instead of configuring manually, networks rely on **DHCP**, an application-level protocol using **UDP**.  
- Server listens on UDP port 67  
- Client sends requests from UDP port 68  

**DHCP DORA Process**:
1. **Discover** – Client broadcasts to find DHCP server.  
2. **Offer** – Server responds with available IP.  
3. **Request** – Client requests offered IP.  
4. **Acknowledge** – Server confirms and leases IP.

Packet example shows the exchange using broadcast IP `255.255.255.255` from client IP `0.0.0.0`.

**Outputs of DHCP**:
- Leased IP address  
- Default gateway  
- DNS server  

✅ **Answers**:
- Steps: `4`  
- Destination IP (Discover): `255.255.255.255`  
- Source IP (Discover): `0.0.0.0`

---

## Task 3 – ARP: Bridging Layer 3 to Layer 2
**Why ARP?**  
- IP addresses work at Layer 3, but Ethernet/WiFi require MAC addresses (Layer 2).  
- ARP resolves IP → MAC mapping.

**How it works**:
- Device broadcasts **ARP Request** asking “Who has this IP?”  
- Target replies with its MAC address (**ARP Reply**).  

**Frame breakdown**:  
- Destination MAC  
- Source MAC  
- Type (IPv4 shown as `0x0800`)  

Tools:  
- `tshark -r arp.pcapng -Nn`  
- `tcpdump -r arp.pcapng -v`

✅ **Answers**:
- Destination MAC in ARP Request: `ff:ff:ff:ff:ff:ff`  
- Example MAC for `192.168.66.1`: `44:df:65:d8:fe:6c`

---

## Task 4 – ICMP: Troubleshooting Networks
**ICMP** is used for diagnostics and error reporting.  

**Key Commands**:
- `ping` – connectivity and round-trip time.  
- `traceroute` (Linux/Unix) or `tracert` (Windows) – trace packet route to destination.  

**Ping**:
- Sends **Echo Request (Type 8)**.  
- Receives **Echo Reply (Type 0)**.  
- Example shows `192.168.66.89` pinging `192.168.11.1`.

**Traceroute**:
- Relies on **TTL (Time To Live)** field.  
- Router decrements TTL → when it reaches 0, sends back **ICMP Time Exceeded** message.  
- Reveals each hop along the path.

✅ **Answers**:
- ICMP Echo data size: `40 bytes`  
- IP header field for traceroute: `TTL`

---

## Task 5 – Routing
Routers connect networks together. They decide paths for packet delivery using algorithms.  

**Protocols**:
- **OSPF (Open Shortest Path First)** – link-state, finds best paths.  
- **EIGRP (Enhanced Interior Gateway Routing Protocol)** – Cisco proprietary, hybrid protocol.  
- **BGP (Border Gateway Protocol)** – backbone of the Internet, connects ISPs.  
- **RIP (Routing Information Protocol)** – distance-vector, counts hops.

✅ **Answer**:
- Cisco proprietary protocol: `EIGRP`

---

## Task 6 – NAT
**Why NAT?**  
- IPv4 address space limited (~4 billion).  
- NAT maps many private IPs → one public IP.  

**How it works**:  
- Router translates internal IP + port to external IP + port.  
- Maintains translation table to track active sessions.  
- External servers only see the public IP.

**Example**:  
- Internal: `192.168.0.129:15401`  
- External mapping: `212.3.4.5:19273`  

✅ **Answers**:
- Public IP phone uses: `212.3.4.5`  
- Approx simultaneous TCP connections: `65,000`

---

## Task 7 – Closing Notes
We covered:  
- **DHCP** for automatic addressing  
- **ARP** for IP→MAC resolution  
- **ICMP** for troubleshooting (ping, traceroute)  
- **Routing** to connect networks  
- **NAT** for conserving IPv4 space  

**Mini-Quiz – Help the Computer**:
1. Ping pong exchange of packets → **ICMP**  
2. Discover route path → **ICMP**  
3. Find DNS/default route automatically → **DHCP**  
4. Obtain IP to communicate with others → **DHCP**

Flag: `THM{computer_is_happy}`

