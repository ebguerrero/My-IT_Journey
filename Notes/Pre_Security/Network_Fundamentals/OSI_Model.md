# OSI Model (TryHackMe)

## What is the OSI Model?
- OSI = **Open Systems Interconnection** model.  
- Framework for how networked devices send, receive, and interpret data.  
- Ensures devices with different functions/designs can communicate reliably.  
- Process used: **encapsulation** (data gains headers/info as it travels down layers).  
- **7 Layers total**, each with distinct responsibilities:

1. **Physical**  
2. **Data Link**  
3. **Network**  
4. **Transport**  
5. **Session**  
6. **Presentation**  
7. **Application**

---

## Layer 1 – Physical
- Concerned with physical hardware: cables, switches, NICs.  
- Uses **binary (1s and 0s)** to transmit data.  
- Example: **Ethernet cables**.

**Key Q&A**  
- What is the numbering system of 0’s and 1’s? → **Binary**  
- What cables connect devices? → **Ethernet cables**

---

## Layer 2 – Data Link
- Handles **physical addressing** (via **MAC addresses**).  
- Every NIC (Network Interface Card) has a unique burned-in MAC.  
- Provides addressing for where to send info on the physical network.  
- Can be **spoofed** for attacks.  

**Key Q&A**  
- What piece of hardware do all devices come with? → **NIC**  

---

## Layer 3 – Network
- Responsible for **routing** and **IP addressing**.  
- Chooses best path for data (shortest, most reliable, fastest).  
- Protocols include **OSPF** and **RIP**.  
- Devices working here: **Routers**.  

---

## Layer 4 – Transport
- Ensures proper **delivery of data** across networks.  
- Uses **TCP** (reliable, error checking, ordered, slower)  
- Uses **UDP** (faster, no guarantees, used for streaming/games).  

**TCP Advantages**  
- Accurate, reliable, synchronizes devices.  

**TCP Disadvantages**  
- Slower, requires connection.  

**UDP Advantages**  
- Fast, low overhead, good for streaming/VoIP.  

**UDP Disadvantages**  
- Doesn’t guarantee delivery or order.  

---

## Layer 5 – Session
- Creates, manages, and ends **sessions** between devices.  
- Keeps communication organized and may add **checkpoints** to resume after data loss.  
- Sessions are **unique**, cannot cross between different ones.  

---

## Layer 6 – Presentation
- Acts as a **translator** for data.  
- Ensures data is in a usable format regardless of software differences.  
- Handles **encryption/decryption** (e.g., HTTPS).  

---

## Layer 7 – Application
- Closest to the user.  
- Defines **protocols and rules** for how applications interact with data.  
- Examples: **DNS, FTP, email clients, browsers**.  
- Provides **GUI (Graphical User Interface)** for interaction.  

---

## Quick Recap Mnemonic
"**Please Do Not Throw Sausage Pizza Away**"  
- Physical  
- Data Link  
- Network  
- Transport  
- Session  
- Presentation  
- Application  

**Key Takeaway:**  
The OSI Model standardizes networking → ensures all devices can communicate, troubleshoot issues at specific layers, and define responsibilities.
