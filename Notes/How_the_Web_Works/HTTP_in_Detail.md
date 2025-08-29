# HTTP in Detail

---

## What is HTTP?  
- **HTTP (HyperText Transfer Protocol):** Rules for communication between web browsers and servers.  
- Developed by Tim Berners-Lee (1989–1991).  
- Transmits webpage data (HTML, images, videos, etc.).  

---

## What is HTTPS?  
- **HTTPS (HyperText Transfer Protocol Secure):** Encrypted version of HTTP.  
- Provides confidentiality and integrity.  
- Prevents eavesdropping and impersonation.  

---

## HTTP Requests & Responses  

### Requests  
- A **URL (Uniform Resource Locator)** specifies how to access a resource.  
- Components:  
  - **Scheme:** Protocol (HTTP, HTTPS, FTP).  
  - **User:** Optional login info.  
  - **Host/Domain:** Server name or IP.  
  - **Port:** Usually 80 (HTTP) or 443 (HTTPS).  
  - **Path:** Resource being requested.  
  - **Query String:** Extra data (`?id=1`).  
  - **Fragment:** Reference to section within resource.  

**Example Request:**  
```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/

Line Breakdown:
Line 1: Request method (GET), path (/), protocol version (HTTP/1.1).
Line 2: Host = requested website.
Line 3: User-Agent = Browser type/version.
Line 4: Referer = Previous page link.
Line 5: Blank line → end of request.
------------------------------------------------------------
Example Response:
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
  <head><title>TryHackMe</title></head>
  <body>Welcome To TryHackMe.com</body>
</html>

Line Breakdown:
Line 1: Protocol + status code (200 OK = success).
Line 2: Web server software/version.
Line 3: Current date/time.
Line 4: Content-Type (what data is sent).
Line 5: Content-Length (size of response).
Line 6: Blank line → end of headers.
Lines 7–14: Actual content (HTML page).
-----------------------------------------------------------------
**HTTP Methods**
GET: Retrieve data (e.g., view webpage).
POST: Send data (e.g., create account, submit form).
PUT: Update data.
DELETE: Remove data.

**HTTP Status Codes**
*Categories:*
100–199: Informational.
200–299: Success.
300–399: Redirection.
400–499: Client errors.
500–599: Server errors.

*Common Codes:*
200 OK: Request succeeded.
201 Created: Resource created.
301 Moved Permanently: Resource moved.
302 Found: Temporary redirect.
400 Bad Request: Invalid request.
401 Unauthorized: Authentication required.
403 Forbidden: No permission.
404 Not Found: Resource doesn’t exist.
405 Method Not Allowed: Wrong request type used.
500 Internal Server Error: Server crashed.
503 Service Unavailable: Server overloaded or under maintenance.

**HTTP Headers**
*Request Headers (client → server):*
Host: Website requested.
User-Agent: Browser/software info.
Content-Length: Length of data sent.
Accept-Encoding: Compression supported.
Cookie: Data stored for sessions/preferences.

*Response Headers (server → client):*
Set-Cookie: Stores cookie on client.
Cache-Control: How long to store response locally.
Content-Type: Type of returned data.
Content-Encoding: Compression method used.

*Cookies*
Small data files stored on client computer.
Sent back with each request.
Used for authentication and preferences.

*Flow Example:*
Client requests webpage.
Server responds with *Set-Cookie.*
Client stores cookie.
On future requests, client sends cookie back.
Server recognizes cookie → personalized response.

**Practice (Examples)**
GET /room → THM{YOU'RE_IN_THE_ROOM}
GET /blog?id=1 → THM{YOU_FOUND_THE_BLOG}
DELETE /user/1 → THM{USER_IS_DELETED}
PUT /user/2 (username=admin) → THM{USER_HAS_UPDATED}
POST /login (username=thm, password=letmein) → THM{HTTP_REQUEST_MASTER}
