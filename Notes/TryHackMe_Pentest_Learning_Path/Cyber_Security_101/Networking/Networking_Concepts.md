# Networking Concepts

Learn about the ISO OSI model and the TCP/IP protocol suite.

---

## 🧭 Learning Objectives
By completing this room, I learned:
- The ISO OSI network model
- The TCP/IP model
- IP addresses, subnets, and routing
- The role of TCP, UDP, and port numbers
- How to connect to an open TCP port from the command line

---

## Task 1 – Introduction
Have you ever wondered why you need an IP address to access the Internet? Or if an IP address can uniquely identify the user? Or what the life of a packet looks like?  

This room is the first in a series dedicated to introducing core networking concepts and the most common protocols:  
- Networking Concepts  
- Networking Essentials  
- Networking Core Protocols  
- Networking Secure Protocols  

**Room prerequisites**: familiarity with IP addresses and TCP/port numbers.  

---

## Task 2 – OSI Model
The **OSI (Open Systems Interconnection)** model is a conceptual framework that describes how communications occur in a computer network. It consists of **seven layers**, from bottom to top:

1. **Physical Layer** – physical transmission of data (cables, radio, binary signal 0/1). Examples: Ethernet cables, WiFi 2.4/5/6 GHz.
2. **Data Link Layer** – protocols for data transfer between adjacent nodes; defines MAC addresses. Examples: Ethernet 802.3, WiFi 802.11.
3. **Network Layer** – routing between networks, logical addressing. Examples: IP, ICMP, VPN.
4. **Transport Layer** – end-to-end communication, error correction, segmentation. Examples: TCP, UDP.
5. **Session Layer** – maintains sessions, synchronizes communication. Examples: NFS, RPC.
6. **Presentation Layer** – data encoding, encryption, compression. Examples: Unicode, JPEG, MIME.
7. **Application Layer** – services for end users. Examples: HTTP, DNS, SMTP, IMAP.

📌 Mnemonic for remembering layers (bottom → top):  
**“Please Do Not Throw Sausage Pizza Away.”**

**Summary Table:**

| Layer | Name             | Function                                | Examples |
|-------|------------------|-----------------------------------------|----------|
| 7     | Application      | Interfaces & services for applications  | HTTP, FTP, DNS, SMTP |
| 6     | Presentation     | Data encoding, encryption, compression  | MIME, JPEG, PNG |
| 5     | Session          | Establish, maintain, synchronize comms  | RPC, NFS |
| 4     | Transport        | End-to-end comms, segmentation, control | TCP, UDP |
| 3     | Network          | Routing, logical addressing             | IP, ICMP, IPSec |
| 2     | Data Link        | Reliable transfer between nodes         | Ethernet, WiFi |
| 1     | Physical         | Transmission media                      | Electrical, optical, radio |

---

## Task 3 – TCP/IP Model
The **TCP/IP (Transmission Control Protocol / Internet Protocol)** model is an implemented version of the OSI concept. Created by the DoD, it ensures communication across networks, even if parts of the network are down.  

**Layers of TCP/IP:**
1. **Link Layer** – maps to OSI Data Link; Ethernet, WiFi.
2. **Internet Layer** – maps to OSI Network; IP, ICMP, IPSec.
3. **Transport Layer** – maps to OSI Transport; TCP, UDP.
4. **Application Layer** – maps to OSI Session/Presentation/Application; HTTP, DNS, SMTP, SSH.

Some textbooks extend this to 5 layers by adding the **Physical Layer**.  

📌 Example mapping: HTTP belongs to the **Application Layer**.  

---

## Task 4 – IP Addresses and Subnets
An **IP address** uniquely identifies a host in a network. IPv4 addresses are 32-bit values, divided into four octets (0–255).  

- **Network address** – identifies the network (e.g., `192.168.1.0`).  
- **Broadcast address** – used to reach all devices (e.g., `192.168.1.255`).  
- **Host address** – identifies a specific device (e.g., `192.168.1.10`).  

**Private IP Ranges (RFC 1918):**
- 10.0.0.0 – 10.255.255.255 (/8)
- 172.16.0.0 – 172.31.255.255 (/12)
- 192.168.0.0 – 192.168.255.255 (/16)

📌 Subnet mask defines the network/host split:  
- Example: `255.255.255.0` → `/24`

**Routing** – Routers forward data between networks, inspecting the destination IP and passing it closer to its destination (like a postal service).  

---

## Task 5 – UDP and TCP
The **Transport Layer** protocols:

### UDP (User Datagram Protocol)
- Connectionless; no guarantee of delivery.  
- Fast, lightweight.  
- Example: video streaming, online gaming, DNS lookups.  

### TCP (Transmission Control Protocol)
- Connection-oriented; ensures reliable delivery.  
- Uses **three-way handshake**:  
  1. SYN (synchronize)  
  2. SYN-ACK (acknowledge + synchronize)  
  3. ACK (final acknowledge)  
- Example: web browsing, email, file transfers.  

📌 Port numbers: range **1 – 65535** (0 reserved).  

---

## Task 6 – Encapsulation
**Encapsulation** is the process of wrapping data with protocol headers at each layer:  

1. **Application data** → passed to transport.  
2. **Transport Layer** → adds TCP segment or UDP datagram.  
3. **Network Layer** → adds IP header, creating an IP packet.  
4. **Data Link Layer** → adds Ethernet/WiFi header and trailer, creating a frame.  

On receiving end, the process is reversed (decapsulation).  

📌 Example:  
- UDP data unit = **Datagram**  
- TCP data unit = **Segment**  
- IP data unit = **Packet**  
- Ethernet/WiFi data unit = **Frame**

---

## Task 7 – Telnet
**Telnet (Teletype Network)** is a text-based protocol that allows connecting to remote systems using TCP. It is insecure and outdated but useful for demonstrations.  

- Default ports:  
  - Echo server: 7  
  - Daytime server: 13  
  - Web server (HTTP): 80  

📌 Example session:  
```bash
telnet 10.201.92.3 80
GET / HTTP/1.1
Host: telnet.thm
````

**Output:** returns HTTP response (e.g., `lighttpd/1.4.63`).

⚠️ Security Note: Telnet sends data (including credentials) in plaintext → replaced by SSH in secure environments.

---

## Task 8 – Conclusion

In this room, I learned:

* The OSI and TCP/IP models and how they map to each other.
* How IP addresses and subnets define networks and routing.
* The differences between TCP and UDP.
* The role of encapsulation in packet delivery.
* How Telnet works as a basic example of TCP connectivity.

➡️ Next room: **Networking Essentials**.

