# Extending Your Network (TryHackMe)

---

## Task 1: Introduction to Port Forwarding
- Port forwarding connects internal services (like web servers) to external networks (the Internet).  
- Without port forwarding, applications are only accessible within the same LAN (intranet).  
- Configured at the **router** level.  

**Key Point:**  
- Port forwarding opens specific ports → but a **firewall** decides if traffic can travel through them.  

---

## Task 2: Firewalls 101
A firewall = border security for a network. It determines what traffic can **enter/exit** based on:  
- Source (where it’s coming from).  
- Destination (where it’s going).  
- Port (what service it uses, e.g., port 80).  
- Protocol (TCP vs UDP).  

**Types of Firewalls:**  
- **Stateful:** Inspects entire connections (dynamic, resource-heavy).  
- **Stateless:** Uses static rules, only checks individual packets (faster, but “dumber”).  

---

## Task 3: Practical – Firewall
- Lab: Block **malicious packets** to IP `203.0.110.1` on **port 80**.  
- Correct flag: `THM{FIREWALLS_RULE}`   

---

## Task 4: VPN Basics
**VPN (Virtual Private Network):**  
- Creates a secure tunnel between devices/networks over the Internet.  
- Allows remote offices or users to appear as part of the same private LAN.  
- Provides:  
  - **Privacy** (encryption hides traffic from ISPs/sniffers).  
  - **Anonymity** (protects identity/logs).  
  - **Security** (safe use of vulnerable services like TryHackMe labs).  

**VPN Technologies:**  
- **PPP** – Encryption + authentication, but non-routable.  
- **PPTP** – Easy setup, weak encryption.  
- **IPSec** – Strong encryption using IP framework, harder to configure.  

---

## Task 5: LAN Networking Devices
### Routers
- Connect networks, forward packets between them.  
- OSI Layer 3.  
- Choose paths based on shortest, most reliable, or fastest link.  

### Switches
- **Layer 2 switch**: forwards frames using MAC addresses.  
- **Layer 3 switch**: can also route packets using IP addresses.  
- VLANs (Virtual LANs): segment networks for security/isolation.  

---

## Task 6: Practical – Network Simulator
- Used the simulator to send a TCP packet from `computer1 → computer3`.  
- Observed handshake and packet delivery.  
- Flag: `THM{YOU'VE_GOT_DATA}` 
- **Handshake count:** 5  

---

## Module Takeaways
- Port forwarding exposes services externally.  
- Firewalls control *what* can pass through.  
- VPNs create secure tunnels.  
- Routers & switches handle data forwarding inside LANs.  
- Hands-on practice reinforces real-world packet flow & firewall rules.  
