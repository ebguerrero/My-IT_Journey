# DNS in Detail  

---

## What is DNS?  
- **DNS (Domain Name System):** Translates human-readable names (e.g., `tryhackme.com`) into IP addresses (e.g., `104.26.10.229`).  
- Works like the “phone book” of the internet.  
- Each computer has a unique IP address (IPv4: four numbers, 0–255).  
- DNS saves us from remembering long IP strings.  

---

## Domain Hierarchy  
- **Root Domain (`.`):** The top of the hierarchy.  
- **TLD (Top-Level Domain):** Suffix of the domain name.  
  - **gTLD (Generic):** `.com`, `.org`, `.edu`.  
  - **ccTLD (Country Code):** `.uk`, `.ca`, `.us`.  
- **Second-Level Domain:** Directly before the TLD.  
  - Example: in `tryhackme.com`, “tryhackme” is the second-level domain.  
- **Subdomain:** Prefix before the second-level domain.  
  - Example: `admin.tryhackme.com` → “admin” is the subdomain.  
  - Can chain together: `jupiter.servers.tryhackme.com`.  
  - Max length: 63 characters per subdomain.  
  - Full domain max length: 253 characters.  

---

## DNS Record Types  
- **A Record:** Maps a hostname → IPv4 address. (e.g., `104.26.10.229`).  
- **AAAA Record:** Maps a hostname → IPv6 address. (e.g., `2606:4700:20::681a:be5`).  
- **CNAME Record:** Maps a hostname → another hostname.  
  - Example: `store.tryhackme.com` → `shops.shopify.com`.  
- **MX Record:** Mail Exchange. Defines mail servers for a domain.  
  - Has a **priority** value. Lower = higher priority.  
- **TXT Record:** Free-form text.  
  - Common uses: domain verification, SPF/DKIM (anti-spam), storing metadata.  

---

## How a DNS Request Works  
1. Client checks **local cache** first.  
2. If not found → query sent to **Recursive DNS Server** (usually ISP).  
3. Recursive server may have cached results. If not, it queries a **Root Server**.  
4. Root Server points to the correct **TLD Server** (e.g., `.com`).  
5. TLD Server points to the **Authoritative Server** for the domain.  
6. Authoritative Server responds with the record (e.g., IP address).  
7. Response is cached locally for quicker lookups next time (based on TTL).  

**Key Terms**  
- **TTL (Time To Live):** How long a record can be cached.  
- **Recursive Server:** Usually provided by ISP. Performs lookups on your behalf.  
- **Authoritative Server:** The final source of truth for a domain.  

---

## Practical DNS Examples  
- **CNAME Lookup:** `shop.website.thm` → `shops.myshopify.com`.  
- **TXT Lookup:** `website.thm` → `"THM{7012BBA60997F35A9516C2E16D2944FF}"`.  
- **MX Lookup:** `website.thm` → `alt4.aspmx.l.google.com` with priority `30`.  
- **A Record Lookup:** `www.website.thm` → `10.10.10.10`.  

**Common Tools**  
- `nslookup` → Built-in command to query DNS records.  
  - Example:  
    ```bash
    nslookup --type=A www.website.thm
    nslookup --type=MX website.thm
    nslookup --type=TXT website.thm
    nslookup --type=CNAME shop.website.thm
    ```  

---

## Key Takeaways  
- DNS maps names to numbers so humans don’t have to remember IPs.  
- The hierarchy flows **Root → TLD → Authoritative**.  
- **TTL** controls caching; records include **A, AAAA, CNAME, MX, TXT**.  
