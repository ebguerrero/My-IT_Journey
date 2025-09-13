# Packets & Frames, TCP/UDP, and Ports

---

## Packets & Frames  
- **Packet** = Data unit at OSI Layer 3 (Network Layer). Includes IP header + payload.  
- **Frame** = Data unit at OSI Layer 2 (Data Link Layer). Encapsulates packet with extra info (e.g., MAC address).  
- Analogy:  
  - Letter = packet (content).  
  - Envelope = frame (used to carry it).  
- **Encapsulation** = Adding headers as data travels down OSI layers.  
- **Decapsulation** = Removing headers when data is received.  
- Packets reduce bottlenecks by splitting data into smaller pieces.  

**Notable Packet Headers**  
- **Time to Live (TTL):** Prevents infinite loops by setting expiry time.  
- **Checksum:** Ensures integrity (detects corruption).  
- **Source Address:** Sender’s IP.  
- **Destination Address:** Receiver’s IP.  

---

## TCP/IP (Transmission Control Protocol / Internet Protocol)  
- A 4-layer model (simplified OSI):  
  1. Application  
  2. Transport  
  3. Internet  
  4. Network Interface  
- **Connection-based:** Establishes connection *before* sending data.  
- Ensures reliability via **3-way handshake**.  

**TCP Advantages**  
- Reliable, guarantees delivery.  
- Prevents flooding/out-of-order data.  
- Integrity via error-checking.  

**TCP Disadvantages**  
- Slower than UDP (more overhead).  
- Needs reliable connection; re-sends if chunks are lost.  

---

### TCP Handshake Process  
**Step 1:** Client → SYN (initiate connection)  
**Step 2:** Server → SYN/ACK (acknowledge + synchronize)  
**Step 3:** Client → ACK (confirm connection established)  

➡ Connection established. Data transfer can begin.  

**Closing a TCP Connection**  
- Uses **FIN** + **ACK** to cleanly close.  
- **RST** = Reset (emergency termination).  

---

## UDP/IP (User Datagram Protocol)  
- **Stateless:** No connection required before sending.  
- No guarantee of delivery, order, or integrity.  
- **Faster** than TCP.  

**UDP Advantages**  
- Low overhead, very fast.  
- Good for real-time apps (streaming, VoIP, gaming).  

**UDP Disadvantages**  
- No reliability.  
- Packets can be dropped or out of order.  

**UDP Headers**  
- TTL, Source Address, Destination Address, Source Port, Destination Port, Data.  

---

## Common Ports (Ports 101)  
Ports = logical endpoints for communication. Range: **0 – 65535**  
- **0–1023:** Well-known ports.  
- **1024–49151:** Registered.  
- **49152–65535:** Dynamic/private.  

**Important Ports**  
- **21 (FTP):** File Transfer Protocol.  
- **22 (SSH):** Secure Shell.  
- **80 (HTTP):** Web browsing (insecure).  
- **443 (HTTPS):** Secure web traffic.  
- **445 (SMB):** File/Printer sharing.  
- **3389 (RDP):** Remote Desktop Protocol.  
