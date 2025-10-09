# Wireshark: The Basics

## Overview
**Room Objective:** Learn the basics of Wireshark, a network protocol analyzer, and how to inspect and analyze captured network packets (PCAPs).  


---

## Task 1: Introduction
- Wireshark is an open-source, cross-platform **network packet analyzer** used for capturing and analyzing live or stored network traffic.  
- Capable of inspecting **PCAP** (packet capture) files and displaying detailed protocol-level information.  
- This room uses two capture files:
  - `http1.pcapng` — used to simulate screenshots.  
  - `Exercise.pcapng` — used to answer challenge questions.  

**Questions:**
- Which file is used to simulate the screenshots? → `http1.pcapng` ✅  
- Which file is used to answer the questions? → `Exercise.pcapng` ✅  

---

## Task 2: Tool Overview

### Use Cases
Wireshark is used to:
- Detect and troubleshoot network problems (congestion, loss, etc.).  
- Detect anomalies or suspicious traffic.  
- Analyze host communication and data flows.  
- Study protocol structures and behavior.  

> ⚠️ Note: Wireshark is **not** an Intrusion Detection System (IDS). It only analyzes — it does not alert or block.

---

### GUI Overview
| Section | Description |
|----------|--------------|
| **Toolbar** | Contains menus and shortcuts for starting/stopping capture, filtering, exporting, and analyzing data. |
| **Display Filter Bar** | Allows users to filter packets based on queries. |
| **Recent Files** | Shows recently analyzed capture files. |
| **Capture Filter and Interfaces** | Displays available network interfaces for live capture. |
| **Status Bar** | Shows profile, packet count, and status info. |

**Traffic Sniffing:**
- Start capture → blue *shark* icon.  
- Stop → red square.  
- Restart → green arrow.  
- Captures are shown in the lower status bar (`ens33: live capture in progress`).  

---

### Loading PCAP Files
- Load via *File → Open* or drag-drop.  
- Displays:
  - **Packet List Pane:** Summary view (source, destination, protocol).  
  - **Packet Details Pane:** Detailed breakdown by protocol layers.  
  - **Packet Bytes Pane:** Raw hex and ASCII data.  

---

### Colouring Packets
- Helps identify packet types and anomalies quickly.
- Found under `View → Coloring Rules`.  
- Default permanent color scheme shows:
  - Green → TCP ACK  
  - Red → TCP Errors  
  - Blue → DNS / HTTP  
- Temporary rules apply only during session; permanent rules are stored in profile.  

---

### Merge PCAP Files
- Combine multiple captures using `File → Merge`.  
- Useful for correlating multi-session data.  

### View File Details
- Check metadata via `Statistics → Capture File Properties`.  
- Includes:
  - Total packets: **58620**  
  - Capture comment: `TryHackMe_Wireshark_Demo`  
  - SHA256 hash: `f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaecb2da5641a6d6eb`  

---

## Task 3: Packet Dissection

### Packet Layers
Wireshark dissects network traffic using the **OSI Model**:

| Layer | Name | Description |
|--------|------|--------------|
| **1** | Frame | Physical layer details (packet size, capture length, timestamp). |
| **2** | Source MAC | Data Link layer (source/destination MAC addresses). |
| **3** | Source IP | Network layer (source/destination IP addresses). |
| **4** | Protocol (TCP/UDP) | Transport layer info: ports, flags, sequence/ack numbers. |
| **5** | Protocol Errors | TCP reassembly or retransmission details. |
| **6** | Application Protocol | HTTP, FTP, SMB, etc. |
| **7** | Application Data | Human-readable content or payload. |

---

### Example Analysis
Packet #27 (HTTP traffic):
- Frame: 214 bytes on wire.  
- MAC: `fe:ff:20:00:01:00` → `Xerox_00:00:00`.  
- IP: `216.239.59.99` → `145.254.160.237`.  
- TCP: Src Port 80 → Dst Port 3371.  
- Payload: HTML webpage.  

**Questions:**
- Markup language used: **XML** ✅  
- Arrival date: **05/13/2004** ✅  
- TTL: **47** ✅  
- TCP payload size: **424** ✅  
- E-tag value: **9a01a-496e-7e35b400** ✅  

---

## Task 4: Packet Navigation

### Packet Numbers
- Each packet has a unique sequential number.  
- Useful for pinpointing specific frames.  

### Navigation Tools
- `Go → Go to Packet` (Ctrl+G) → jump to specific packet number.  
- `Edit → Find Packet` → search by content, hex, string, or regex.  
- `Edit → Mark/Unmark Packet` (Ctrl+M) → flag key packets.  
- `Edit → Packet Comment` → add notes.  

---

### Export Packets & Objects
- Export specific packets via:
  - `File → Export Specified Packets`.  
  - Options: *All packets*, *Selected only*, *Marked only*, etc.
- Export files transferred over protocols:
  - `File → Export Objects → HTTP/FTP/IMF/SMB/TFTP`.  
- Example extracted file: `download.html`.

---

### Time Display Format
- Adjust timestamps under `View → Time Display Format`.  
- Default: *Seconds Since Beginning*.  
- Common setting: *UTC Date & Time*.  

---

### Expert Info
Wireshark highlights traffic anomalies using color codes and severities:

| Severity | Color | Meaning |
|-----------|--------|----------|
| Chat | Blue | Normal workflow |
| Note | Cyan | Informational events |
| Warn | Yellow | Minor issues |
| Error | Red | Serious problems |

**Example Info Groups:**
- `Checksum` → Invalid checksum  
- `Deprecated` → Outdated protocol use  
- `Malformed` → Packet format error  
- `Comment` → User-added note  

**Questions:**
- Artist 1 (r4vw8173) ✅  
- MD5 hash (packet 12): `911cd574a42865a956ccde2d04495ebf` ✅  
- Alien name in `.txt` file: `PACKETMASTER` ✅  
- Total warnings: `1636` ✅  

---

## Task 5: Packet Filtering

### Apply as Filter
- Quickly apply display filters with right-click → `Apply as Filter`.  
- Example: filtering for HTTP packets = `http`.  
- Total displayed packets: `1089`.  

### Conversation Filter
- Shows only packets part of the same session (IP/port-based).  
- Found under `Analyse → Conversation Filter`.

### Colourise Conversation
- Visually separates conversations with color (without filtering them).  
- Menu: `View → Colourise Conversation → [Select Layer]`.

### Prepare as Filter
- Adds but does not apply the filter yet; allows combining queries.  
- Example: `ip.src == 145.254.160.237`.

### Apply as Column
- Adds selected field (e.g., IP or TCP port) as a new column in Packet List view.

### Follow Stream
- Displays reconstructed application-layer data.  
- Menu: `Analyse → Follow TCP/UDP/HTTP Stream`.  
- Blue = server responses, Red = client requests.  

**Questions:**
- Filter applied on HTTP: `http` ✅  
- Number of displayed packets: `1089` ✅  
- Total artists: `3` ✅  
- Second artist: `Blad3` ✅  

---

## Task 6: Conclusion
**Summary:**  
You’ve learned how to:
- Load and merge PCAP files.  
- Dissect packets by OSI layers.  
- Filter, mark, and comment on network traffic.  
- Export data and analyze objects.  
- Use Expert Info and Follow Streams for deep inspection.  


---

# 🧠 Key Takeaways
- Wireshark is a **passive analysis tool**, not an IDS.  
- Use **display filters** to view targeted packets.  
- **Colouring rules** and **conversation filters** simplify analysis.  
- Always verify anomalies with **Expert Info**.  
- Combine with other tools for full network defense visibility.

