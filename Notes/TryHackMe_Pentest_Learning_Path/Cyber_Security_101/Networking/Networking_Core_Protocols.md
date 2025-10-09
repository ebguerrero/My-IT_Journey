# Networking Core Protocols

This room covered the fundamental TCP/IP protocols that enable everyday internet communication. By the end, I gained hands-on experience with DNS, WHOIS, HTTP(S), FTP, SMTP, POP3, and IMAP through interactive labs.

---

## Task 1: Introduction
- Prerequisites: OSI model, TCP/IP layers, Ethernet/IP/TCP basics.
- Objectives: Learn WHOIS, DNS, HTTP/HTTPS, FTP, SMTP, POP3, and IMAP.

---

## Task 2: DNS – Remembering Addresses
DNS maps domain names to IP addresses.

**Record types:**
- **A record** – IPv4 address
- **AAAA record** – IPv6 address
- **CNAME record** – Alias of another domain
- **MX record** – Mail exchange server

**Example commands:**
```bash
nslookup www.example.com
tshark -r dns-query.pcapng -Nn
````

**Key Takeaways:**

* DNS uses UDP/53 by default (TCP/53 as fallback).
* AAAA = IPv6, MX = mail server.

---

## Task 3: WHOIS

* WHOIS provides registration details of domains (owner, registrar, creation/expiration).
* Useful for gathering metadata like contact info and dates.

**Example command:**

```bash
whois example.com
```

**Takeaways:**

* x.com created: `1993-04-02`
* twitter.com created: `2000-01-21`

---

## Task 4: HTTP(S) – Accessing the Web

* HTTP = Hypertext Transfer Protocol (TCP/80)
* HTTPS = Secure HTTP (TCP/443)

**Common Methods:**

* **GET** – Retrieve data
* **POST** – Send data
* **PUT** – Create/replace data
* **DELETE** – Remove resource

**Lab:**

* Inspected HTTP request/response in Wireshark.
* Used Telnet to manually GET `file.html`.

**Flag:** `THM{TELNET-HTTP}`

---

## Task 5: FTP – Transferring Files

* FTP = File Transfer Protocol (TCP/21).
* Used to transfer files between client/server.

**Commands:**

* `USER` – login
* `PASS` – password
* `LIST` – directory listing
* `RETR` – download
* `STOR` – upload

**Lab:**

* Connected via FTP with `anonymous` login.
* Retrieved `flag.txt`.

**Flag:** `THM{FAST-FTP}`

---

## Task 6: SMTP – Sending Email

* SMTP = Simple Mail Transfer Protocol (TCP/25).
* Defines how clients send email to servers.

**Commands:**

* `HELO/EHLO` – start session
* `MAIL FROM` – sender address
* `RCPT TO` – recipient address
* `DATA` – begin message body
* `.` – end of message

**Lab:** Sent test email via Telnet.

**Q&A:**

* Command to start message body: `DATA`
* End of message: `.`

---

## Task 7: POP3 – Receiving Email

* POP3 = Post Office Protocol v3 (TCP/110).
* Downloads mail to client.

**Commands:**

* `USER` / `PASS` – login
* `STAT` – message count
* `LIST` – list messages
* `RETR <id>` – retrieve message
* `DELE <id>` – delete message
* `QUIT` – close session

**Lab:** Retrieved email over Telnet.

* Server: `Dovecot`
* Flag: `THM{TELNET_RETR_EMAIL}`

---

## Task 8: IMAP – Synchronizing Email

* IMAP = Internet Message Access Protocol (TCP/143).
* Allows synchronization of mail across devices (read, delete, move, copy).

**Commands:**

* `LOGIN user pass`
* `SELECT inbox`
* `FETCH <id> body[]`
* `LOGOUT`

**Lab:** Used Telnet to fetch message.

* Command for 4th message: `FETCH 4 body[]`

---

## Task 9: Conclusion

**Protocol Summary Table:**

| Protocol | Transport | Default Port |
| -------- | --------- | ------------ |
| TELNET   | TCP       | 23           |
| DNS      | UDP/TCP   | 53           |
| HTTP     | TCP       | 80           |
| HTTPS    | TCP       | 443          |
| FTP      | TCP       | 21           |
| SMTP     | TCP       | 25           |
| POP3     | TCP       | 110          |
| IMAP     | TCP       | 143          |

---

## Key Takeaways

* DNS resolves names → IPs; WHOIS reveals domain registration.
* HTTP/HTTPS enable web traffic; HTTPS ensures encryption.
* FTP transfers files; insecure if plaintext.
* SMTP sends email; POP3 downloads email; IMAP synchronizes email across devices.
* Ports are critical identifiers (HTTP 80, HTTPS 443, FTP 21, SMTP 25, POP3 110, IMAP 143).
* Many protocols tested with Telnet to show raw communication.
