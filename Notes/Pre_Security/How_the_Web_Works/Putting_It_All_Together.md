
````markdown
# Putting It All Together

## Overview
When you request a website, multiple systems and components work together behind the scenes to deliver the final page.  

---

## Lifecycle of a Web Request
1. **Request Website** → Browser sends request.  
2. **DNS Lookup** → Browser checks DNS for the server’s IP.  
3. **Connect to Web Server** → Communication begins via HTTP/HTTPS.  
4. **Server Response** → Webserver returns HTML, CSS, JS, images, etc.  
5. **Browser Rendering** → Browser interprets and displays the website.  

---

## Load Balancers
- Distribute traffic across multiple servers.  
- **Algorithms:**  
  - **Round-Robin** → Sends requests in order.  
  - **Weighted** → Routes based on server capacity/load.  
- Perform **health checks** to ensure servers are alive.  
- Provide **failover** if one server goes down.  

---

## Content Delivery Network (CDN)
- Hosts **static files** (HTML, CSS, JS, images, videos).  
- Delivers from the **nearest server** to reduce latency.  
- Improves website **speed** and **availability**.  

---

## Databases
- Store and retrieve application data.  
- Range from **flat text files** to **complex distributed systems**.  
- Examples: **MySQL, PostgreSQL, MongoDB, MSSQL**.  

---

## Web Application Firewall (WAF)
- Filters traffic before it reaches the web server.  
- Protects against:  
  - **DoS/DDoS attacks**  
  - **Injection attacks**  
  - **Excessive requests** (rate limiting)  

---

## Web Servers
- Run software like **Apache, Nginx, IIS, Node.js**.  
- Can host multiple sites using **virtual hosts**.  
- Serve:  
  - **Static Content** → Files that don’t change (images, CSS, JS).  
  - **Dynamic Content** → Generated on demand (blogs, search results).  

**Example (PHP dynamic page):**
```php
<html>
  <body>
    Hello <?php echo $_GET["name"]; ?>
  </body>
</html>
````

Browser only sees:

```html
<html>
  <body>Hello adam</body>
</html>
```

---

## Full Request Flow

1. Browser requests website (e.g., `tryhackme.com`).
2. Check **local cache** for IP address.
3. Query **recursive DNS server**.
4. Query **root server** → find authoritative DNS.
5. Authoritative DNS returns IP.
6. Request passes through **Web Application Firewall (WAF)**.
7. Request passes through **Load Balancer**.
8. Webserver receives request (port 80/443).
9. Webserver may query a **Database**.
10. Webserver responds with HTML/CSS/JS.
11. Browser renders the page into a viewable website.

---

## Summary

* A single web request involves **DNS, WAFs, load balancers, servers, and databases**.
* CDNs improve performance by delivering static content faster.
* Web servers handle both **static** and **dynamic** content.
* Security layers like **WAFs** protect applications from attacks.

```

---

