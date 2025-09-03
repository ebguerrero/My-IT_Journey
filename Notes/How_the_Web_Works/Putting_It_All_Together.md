# Putting It All Together

---

## Summary
When you request a website, several processes happen behind the scenes:

1. **Request Website** → Browser sends request.
2. **DNS Lookup** → Browser checks DNS for the server’s IP.
3. **Connect to Web Server** → Communication begins via HTTP/HTTPS.
4. **Server Response** → Webserver returns HTML, CSS, JS, images, etc.
5. **Browser Rendering** → Browser displays the website to you.

---

## Other Components

### Load Balancers
- Distribute traffic across multiple servers.  
- Algorithms:  
  - **Round-Robin** → Sends requests in turn.  
  - **Weighted** → Sends requests based on load.  
- Perform **health checks** to ensure servers are alive.  
- Provide failover if one server goes down.  

### CDN (Content Delivery Network)
- Hosts **static files** (HTML, CSS, JS, images, videos).  
- Delivers from the **nearest server** to reduce latency.  
- Improves website speed and availability.  

### Databases
- Store and retrieve application data.  
- Range from **flat text files** to **complex distributed systems**.  
- Examples: MySQL, PostgreSQL, MongoDB, MSSQL.  

### WAF (Web Application Firewall)
- Filters traffic before it reaches the web server.  
- Protects against:  
  - **DoS/DDoS attacks**  
  - **Injection attacks**  
  - Excessive requests (rate limiting).  

---

## How Web Servers Work

- **Web Server Software:** Apache, Nginx, IIS, Node.js.  
- **Virtual Hosts:** Allow multiple domains to run on the same server.  
- **Static Content:** Files that don’t change (images, CSS, JS).  
- **Dynamic Content:** Generated on demand (blogs, search results).  
- **Backend Languages:** PHP, Python, Ruby, Node.js, etc.  

**Example:**  
```php
<html><body>Hello <?php echo $_GET["name"]; ?></body></html>

Browser only sees: <html><body>Hello adam</body></html>

Full Request Flow
Request website in browser (tryhackme.com).
Check local cache for IP address.
Query recursive DNS server.
Query root server → find authoritative DNS.
Authoritative DNS returns IP.
Request passes through Web Application Firewall.
Request passes through Load Balancer.
Webserver receives request (port 80/443).
Webserver may query a Database.
Webserver responds with HTML/CSS/JS.
Browser renders into a viewable website.
