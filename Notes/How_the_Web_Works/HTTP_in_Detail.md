Perfect 👍 let’s start with **HTTP\_in\_detail.md**, fully reformatted so it matches the clean style of **Linux Fundamentals Part 2**.

Here’s the corrected Markdown — you can copy/paste the whole thing as-is:

````markdown
# HTTP in Detail

## Overview
HTTP (HyperText Transfer Protocol) is the foundation of communication on the web.  
It is a **stateless protocol** used for transferring data between clients (browsers) and servers.

---

## HTTP Requests
A client sends an **HTTP request** to a server.  
The request usually contains:

- **Method** → Action (GET, POST, PUT, DELETE).  
- **Path** → The resource being requested (e.g., `/index.html`).  
- **Headers** → Extra information about the request.  
- **Body** → Optional, used mainly with POST/PUT to send data.  

**Example Request:**
```http
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
````

---

## HTTP Responses

The server replies with an **HTTP response**.

**Example Response:**

```http
HTTP/1.1 200 OK
Server: Apache/2.4.1 (Unix)
Date: Tue, 20 Aug 2024 20:00:00 GMT
Content-Type: text/html
Content-Length: 100

<html>
  <body>Hello World</body>
</html>
```

### Line Breakdown

* **Line 1** → Protocol + status code (`200 OK` = success).
* **Line 2** → Web server software/version.
* **Line 3** → Current date/time.
* **Line 4** → Content-Type (what data is sent).
* **Line 5** → Content-Length (size of response).
* **Line 6** → Blank line (end of headers).
* **Line 7+** → Actual content (HTML page).

---

## HTTP Methods

* **GET** → Retrieve data (e.g., view webpage).
* **POST** → Send data (e.g., submit form).
* **PUT** → Update data.
* **DELETE** → Remove data.

---

## HTTP Status Codes

### Categories

* **100–199** → Informational.
* **200–299** → Success.
* **300–399** → Redirection.
* **400–499** → Client errors.
* **500–599** → Server errors.

### Common Codes

* `200 OK` → Request succeeded.
* `201 Created` → Resource created.
* `301 Moved Permanently` → Resource moved.
* `302 Found` → Temporary redirect.
* `400 Bad Request` → Invalid request.
* `401 Unauthorized` → Authentication required.
* `403 Forbidden` → No permission.
* `404 Not Found` → Resource doesn’t exist.
* `405 Method Not Allowed` → Wrong request type used.
* `500 Internal Server Error` → Server crashed.
* `503 Service Unavailable` → Server overloaded or under maintenance.

---

## HTTP Headers

### Request Headers (client → server)

* `Host` → Website requested.
* `User-Agent` → Browser/software info.
* `Content-Length` → Length of data sent.
* `Accept-Encoding` → Compression supported.
* `Cookie` → Data stored for sessions/preferences.

### Response Headers (server → client)

* `Set-Cookie` → Stores cookie on client.
* `Cache-Control` → How long to store response locally.
* `Content-Type` → Type of returned data.
* `Content-Encoding` → Compression method used.

---

## Cookies

* Small data files stored on client computer.
* Sent back with each request.
* Commonly used for authentication or remembering preferences.

**Example Flow:**

1. Client requests webpage.
2. Server responds with `Set-Cookie`.
3. Client stores cookie.
4. On future requests, client sends cookie back.
5. Server recognizes cookie → adjusts response.

---

## Practice Examples

```http
GET /room              → THM{YOU'RE_IN_THE_ROOM}
GET /blog?id=1         → THM{YOU_FOUND_THE_BLOG}
DELETE /user/1         → THM{USER_IS_DELETED}
PUT /user/2 (username=admin) → THM{USER_HAS_UPDATED}
POST /login (username=thm, password=letmein) → THM{HTTP_REQUEST_MASTER}
```

---

## Summary

* HTTP is stateless.
* Requests contain a **method**, **path**, **headers**, and optional **body**.
* Responses contain **status codes**, **headers**, and a **body**.
* Methods: GET, POST, PUT, DELETE.
* Status codes indicate success, errors, or redirects.
* Cookies maintain session data across requests.

```

---

✅ Now it will render just like Linux Fundamentals Part 2 — with clear headers, inline code shading, and clean fenced blocks.  

Would you like me to fix **How_Websites_Work.md** next in the same style?
```
