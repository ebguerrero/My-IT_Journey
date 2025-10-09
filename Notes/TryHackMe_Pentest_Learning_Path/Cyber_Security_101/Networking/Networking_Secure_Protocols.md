# Networking Secure Protocols

## Task 1: Introduction
- Insecure protocols (HTTP, POP3, SMTP, IMAP, TELNET) cannot protect **confidentiality, integrity, or authenticity**.  
- TLS (Transport Layer Security) adds protection:
  - Confidentiality → prevents eavesdropping.  
  - Integrity → prevents tampering with data.  
  - Authenticity → ensures communication with the correct server.  
- Protocols upgraded with TLS:
  - HTTP → HTTPS  
  - SMTP → SMTPS  
  - POP3 → POP3S  
  - IMAP → IMAPS  
- SSH created to replace insecure TELNET.  
- VPN allows secure network connections over an insecure medium.  

---

## Task 2: TLS
- Developed from **SSL (Secure Sockets Layer)**.  
- TLS 1.0 → released 1999. TLS 1.3 → current version (2018).  
- TLS ensures data cannot be read/modified by attackers.  
- Common protocols secured by TLS: HTTPS, SMTPS, POP3S, IMAPS, DoT, MQTT, SIP, etc.  
- **Certificate Signing Request (CSR)** → sent to Certificate Authority (CA) to get a digital certificate.  
- **CA-signed certificate** proves authenticity.  
- **Self-signed certificate** should NOT be trusted (no third-party validation).  

**Questions:**  
- Protocol TLS upgraded from → **SSL** ✅  
- Certificates that should not be used to confirm authenticity → **Self-signed certificates** ✅  

---

## Task 3: HTTPS
### HTTP
- HTTP runs on TCP port **80**.  
- HTTP traffic is **plaintext** (visible in Wireshark captures).  
- Example HTTP GET request:  
```

GET / HTTP/1.1
Host: 10.10.41.192

```
- Packets shown in capture:  
- TCP 3-way handshake.  
- HTTP GET request.  
- TCP connection termination.  

### HTTPS (HTTP over TLS)
- HTTPS = HTTP secured with TLS. Runs on **TCP port 443**.  
- Process:  
1. TCP 3-way handshake.  
2. TLS handshake (negotiate encryption).  
3. HTTP communication over TLS (encrypted).  
- Wireshark shows **“Application Data”** instead of plaintext.  

**Questions:**  
- Number of packets in TLS negotiation = **8** ✅  
- Packet with `GET /login` request = **10** ✅  

---

## Task 4: SMTPS, POP3S, and IMAPS
- SMTP, POP3, and IMAP use plaintext by default.  
- Adding TLS upgrades them:  
- SMTPS → ports **465, 587**  
- POP3S → port **995**  
- IMAPS → port **993**  

**Questions:**  
- Which protocol leaks login credentials if captured? → **IMAP** ✅  

---

## Task 5: SSH
- TELNET = insecure (sends everything in plaintext).  
- SSH (Secure Shell) = secure replacement for TELNET.  
- Provides:
- Secure authentication (password, key, 2FA).  
- Confidentiality (encrypted).  
- Integrity (cryptographic protection).  
- Tunneling (VPN-like connections).  
- X11 forwarding (GUI over SSH).  
- SSH default port = **22**.  
- Most common implementation = **OpenSSH**.  

**Question:**  
- Open-source SSH implementation → **OpenSSH** ✅  

---

## Task 6: SFTP and FTPS
- **SFTP (SSH File Transfer Protocol)**:
- Part of SSH suite.  
- Uses port **22**.  
- Commands: `get filename`, `put filename`.  

- **FTPS (FTP Secure)**:
- FTP secured with TLS.  
- Uses port **990** (default).  
- Requires TLS certificate.  

**Flag:**  
- `THM{Protocols_secur3d}` ✅  

---

## Task 7: VPN
- VPN = **Virtual Private Network**.  
- Provides a secure tunnel over the internet.  
- Encrypts traffic → prevents eavesdropping & tampering.  
- VPN client ↔ VPN server → encrypted tunnel.  
- Used for:
- Connecting remote offices.  
- Remote workers accessing main office resources.  
- Circumventing geo-restrictions.  

**Question:**  
- What would you use to connect remote sites to the main branch? → **VPN** ✅  

---

## Task 8: Closing Notes
- Approaches to securing network traffic:
1. **TLS** → secures many protocols (HTTPS, SMTPS, POP3S).  
2. **SSH** → secure remote access + tunneling.  
3. **VPN** → secure tunnels between networks/sites.  

- Wireshark challenge:
- Decrypt TLS traffic with `ssl-key.log`.  
- Extract login credentials from decrypted packet.  

**Flag:**  
- `THM{B8WM6P}` ✅  

