# Intro to LAN (Local Area Network)

## LAN Topologies

### Star Topology
- Devices are individually connected to a central device (switch/hub).  
- Most common today (scalable, reliable).  
- **Advantages:** scalable, easy to add devices, robust hardware.  
- **Disadvantages:** expensive, high maintenance, central point of failure.

### Bus Topology
- All devices share one backbone cable.  
- **Advantages:** cheap, simple to set up.  
- **Disadvantages:** prone to bottlenecks, single point of failure, hard to troubleshoot.

### Ring Topology
- Devices form a loop, passing data around.  
- **Advantages:** easier fault isolation, fewer bottlenecks than bus.  
- **Disadvantages:** inefficient for long paths, a single fault breaks the whole ring.

---

## Networking Devices

### Switch
- Aggregates devices (computers, printers, etc.).  
- More efficient than hubs: sends packets only to intended device.  
- Supports multiple ports (4, 8, 16, 24, 32, 64).  
- Improves performance, reduces traffic.

### Router
- Connects networks and passes data between them.  
- Uses **routing** to deliver data successfully across networks.  
- Useful when multiple paths exist (adds redundancy and reliability).  

---

## Subnetting Primer
- **Subnetting** = splitting a network into smaller networks.  
- Like slicing a cake into smaller portions.  
- Used in organizations to separate departments (e.g., Accounting, HR, Finance).  

### Subnet Structure
- **Network Address** → start of network (e.g., 192.168.1.0).  
- **Host Address** → identifies devices on network (e.g., 192.168.1.100).  
- **Default Gateway** → special device that sends info outside subnet (e.g., 192.168.1.254).  

**Benefits of Subnetting:**  
- Efficiency (reduced congestion).  
- Security (limits broadcast domains).  
- Full control over addressing.  

---

## ARP (Address Resolution Protocol)
- Maps **IP addresses** ↔ **MAC addresses**.  
- Each device keeps a cache of mappings.  
- Process:  
  1. Device sends **ARP Request** (“Who has IP X?”).  
  2. Owner replies with **ARP Reply** (its MAC address).  

---

## DHCP (Dynamic Host Configuration Protocol)
- Assigns IP addresses automatically to devices.  
- Process (DORA):  
  1. **Discover** – device requests IP.  
  2. **Offer** – DHCP server offers IP.  
  3. **Request** – device accepts.  
  4. **ACK** – server confirms lease.  

---

## Practical Lab Notes
- Explored vulnerabilities of LAN topologies.  
- Learned how devices can spoof addresses or rely on DHCP for assignment.  
- **Flags obtained:**  
  - Topology flaws → `THM{TOPOLOGY_FLAWS}`
