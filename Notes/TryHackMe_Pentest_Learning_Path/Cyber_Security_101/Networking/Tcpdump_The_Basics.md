# Tcpdump: The Basics

## Overview
**Room Objective:** Learn how to use Tcpdump to capture, filter, and display packets for network analysis.  
**Duration:** ~60 min  
**Difficulty:** Beginner  

Tcpdump is a command-line packet analyzer used to capture and inspect network traffic in real time. It’s lightweight, scriptable, and ideal for quickly examining network behavior or troubleshooting issues without a GUI tool like Wireshark.

---

## Task 1: Introduction

### Overview
When studying network protocols, we rarely see the "conversations" between devices directly. Tcpdump allows you to observe these interactions by capturing packets at the network level.

Tcpdump relies on the **libpcap** library (written in C/C++) for packet capture and filtering, originally developed for UNIX systems and later ported to Windows as **WinPcap**.

### Learning Objectives
In this room, you learned how to:
- Capture packets and save them to a file.  
- Set filters on captured packets.  
- Control how captured packets are displayed.  

**Room Prerequisites:**  
- Basic understanding of the **TCP/IP model** and related protocols.  
- Familiarity with TryHackMe’s “Networking” rooms (Concepts, Essentials, Core Protocols, Secure Protocols).  

**Credentials:**  
```

Username: user
Password: THM123

````

**Question:**  
- What is the name of the library associated with Tcpdump? → `libpcap` ✅  

---

## Task 2: Basic Packet Capture

### Specify the Network Interface
Before capturing, identify which interface to listen on:
```bash
sudo tcpdump -i INTERFACE
````

or list available interfaces:

```bash
ip a s
```

Example output:

```
lo: <LOOPBACK,UP,LOWER_UP>
ens5: <BROADCAST,MULTICAST,UP,LOWER_UP>
```

---

### Save the Captured Packets

Capture and save packets to a file (usually `.pcap`):

```bash
sudo tcpdump -w capture.pcap
```

Saved files can later be inspected using Wireshark.

---

### Read Captured Packets from a File

Read saved captures:

```bash
tcpdump -r capture.pcap
```

---

### Limit the Number of Captured Packets

Stop after a specific count:

```bash
sudo tcpdump -c 50
```

---

### Don’t Resolve IP Addresses or Port Numbers

Avoid DNS and service name lookups for clarity:

```bash
sudo tcpdump -n
sudo tcpdump -nn
```

Example:

```bash
sudo tcpdump -i ens5 -c 5 -nn
```

This shows source and destination IPs without resolving them.

---

### Verbose Output

Increase verbosity for deeper inspection:

```bash
-v     # Verbose
-vv    # More verbose
-vvv   # Maximum verbosity
```

---

### Summary and Examples

| Command                | Explanation                                     |
| ---------------------- | ----------------------------------------------- |
| `tcpdump -i INTERFACE` | Capture on a specific network interface.        |
| `tcpdump -w FILE`      | Write captured packets to file.                 |
| `tcpdump -r FILE`      | Read captured packets from file.                |
| `tcpdump -c COUNT`     | Limit number of packets captured.               |
| `tcpdump -n`           | Don’t resolve IP addresses.                     |
| `tcpdump -nn`          | Don’t resolve IPs or protocol names.            |
| `tcpdump -v`           | Verbose output (`-vv`, `-vvv` for more detail). |

**Examples:**

```bash
tcpdump -i eth0 -c 50 -v
tcpdump -i wlan0 -w data.pcap
tcpdump -i any -nn
```

**Question:**

* What option displays addresses only in numeric format? → `-n` ✅

---

## Task 3: Filtering Expressions

Filters refine what packets you capture.

### Filtering by Host

Capture packets to/from a specific host:

```bash
sudo tcpdump host example.com -w http.pcap
```

or:

```bash
tcpdump src host 192.168.1.10
tcpdump dst host example.com
```

---

### Filtering by Port

Capture only traffic for specific ports (e.g., DNS uses port 53):

```bash
sudo tcpdump -i ens5 port 53 -n
```

---

### Filtering by Protocol

Filter specific protocols:

```bash
tcpdump ip
tcpdump tcp
tcpdump udp
tcpdump icmp
```

Example:

```bash
sudo tcpdump -i ens5 icmp -n
```

---

### Logical Operators

| Operator | Description           | Example                        |
| -------- | --------------------- | ------------------------------ |
| `and`    | Both conditions true  | `tcpdump host 1.1.1.1 and tcp` |
| `or`     | Either condition true | `tcpdump udp or icmp`          |
| `not`    | Negates condition     | `tcpdump not tcp`              |

---

### Summary and Examples

| Command                        | Explanation                 |
| ------------------------------ | --------------------------- |
| `tcpdump host IP`              | Filter by specific host.    |
| `tcpdump src host IP`          | Filter by source host.      |
| `tcpdump dst host IP`          | Filter by destination host. |
| `tcpdump port PORT_NUMBER`     | Filter by port.             |
| `tcpdump src port PORT_NUMBER` | Filter by source port.      |
| `tcpdump dst port PORT_NUMBER` | Filter by destination port. |
| `tcpdump PROTOCOL`             | Filter by protocol.         |

**Example Commands:**

```bash
tcpdump -i any tcp port 22
tcpdump -i wlan0 udp port 123
tcpdump -i eth0 host example.com and tcp port 443
```

**Questions:**

* How many packets in `traffic.pcap` use ICMP? → `26` ✅
* IP address that requested MAC address of 192.168.124.137? → `192.168.124.148` ✅
* DNS hostname in first query? → `mirrors.rockylinux.org` ✅

---

## Task 4: Advanced Filtering

### Filtering by Length

* `greater LENGTH` → packets ≥ specified length.
* `less LENGTH` → packets ≤ specified length.

---

### Binary Operations

Tcpdump supports bitwise operations:

| Operator | Meaning |    |
| -------- | ------- | -- |
| `&`      | AND     |    |
| `        | `       | OR |
| `!`      | NOT     |    |

---

### Header Bytes

Advanced users can filter based on header bytes:

```
proto[expr:size]
```

Examples:

```bash
ether[0] & 1 != 0      # Multicast packets
ip[6] & 0x1F != 0      # Non-fragmented IP packets
```

---

### TCP Flags

Tcp flags can be filtered directly:

| Command    | Description       |
| ---------- | ----------------- |
| `tcp-syn`  | SYN (Synchronize) |
| `tcp-ack`  | ACK (Acknowledge) |
| `tcp-fin`  | FIN (Finish)      |
| `tcp-rst`  | RST (Reset)       |
| `tcp-push` | PSH (Push)        |

Examples:

```bash
tcpdump "tcp[tcpflags] == tcp-syn"
tcpdump "tcp[tcpflags] & tcp-syn != 0"
tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"
```

**Questions:**

* How many packets have the TCP RST flag set? → `57` ✅
* IP of host that sent packets >15,000 bytes? → `185.117.80.53` ✅

---

## Task 5: Displaying Packets

Tcpdump provides multiple ways to format captured output.

| Option | Description                         |
| ------ | ----------------------------------- |
| `-q`   | Quick view: brief info only.        |
| `-e`   | Include MAC addresses.              |
| `-A`   | Display packet contents in ASCII.   |
| `-xx`  | Display packet data in hexadecimal. |
| `-X`   | Show data in both hex and ASCII.    |

### Examples

```bash
tcpdump -r TwoPackets.pcap -q
tcpdump -r TwoPackets.pcap -e
tcpdump -r TwoPackets.pcap -A
tcpdump -r TwoPackets.pcap -xx
tcpdump -r TwoPackets.pcap -X
```

**Question:**

* What is the MAC address of the host that sent an ARP request? → `52:54:00:7c:d3:5b` ✅

---

## Task 6: Conclusion

In this room, you learned:

* How to capture and save packets using Tcpdump.
* How to filter by host, port, and protocol.
* How to apply advanced filters with binary operations and TCP flags.
* How to display packets in multiple formats for analysis.

---

# 🧠 Key Takeaways

* Tcpdump is ideal for **CLI-based packet analysis** and scripting.
* Combine it with **Wireshark** for deeper investigation.
* Filters help you capture only what matters.
* Use verbosity and display options to control the level of detail.
* Always use `sudo` when capturing live network traffic.

