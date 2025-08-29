# Network Fundamentals – Networking Basics (TryHackMe)

## Task 1: What is Networking?
- Networking = devices connected together (from 2 to billions).
- Real-world analogies: transport systems, power grid, postal services.
- In computing, everyday devices (laptops, phones, cameras, traffic lights) communicate via networks.
- **Why it matters:** networking is foundational for cybersecurity work.

---

## Task 2: What is the Internet?
- The Internet = a giant network made of many smaller **private** networks joined together (public network).
- ARPANET (1960s) → early Internet; **World Wide Web (1989)** by Tim Berners-Lee popularized today’s use.
- Devices identify themselves with labels and follow rules to communicate.

**Network types**
- **Private network** – internal to an org/home.
- **Public network** – the Internet.

---

## Task 3: Identifying Devices on a Network
Devices must be identifiable to communicate.

**Two identifiers**
- **IP Address** – like a *name*.
  - **IPv4**: 4 **octets** (0–255 each), e.g., `192.168.1.1`
  - **IPv6**: much larger address space (2^128) → solves IPv4 exhaustion; more efficient routing methods
  - **Public vs Private**: private used inside networks; public used on the Internet
- **MAC Address** – like a *fingerprint* tied to the network card (12 hex characters, e.g., `a4:c3:f0:85:ac:2d`)
  - Can be **spoofed** to impersonate another device (common in captive portals/guest Wi-Fi).

**Lab result (MAC spoofing)** THM{YOU_GOT_ON_TRYHACKME}

## Task 4: Ping (ICMP)
- `ping` tests reachability and measures latency using **ICMP echo** request/reply.
- Example:
  ```bash
  ping 10.10.10.10
**Lab result** THM{I_PINGED_THE_SERVER}
