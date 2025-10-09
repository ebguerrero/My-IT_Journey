

# How Websites Work

## Overview
Websites are made up of **frontend (client-side)** code and **backend (server-side)** code.  
When you access a website, your browser communicates with a server, retrieves resources, and renders them.

---

## Frontend (Client-Side)
- Runs in the **browser**.  
- Built using:
  - **HTML** → Structure/content  
  - **CSS** → Styling and layout  
  - **JavaScript (JS)** → Interactivity  

**Example (HTML snippet):**
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>Welcome to my site!</p>
  </body>
</html>
````

---

## Backend (Server-Side)

* Runs on a **server**.
* Processes requests, performs logic, interacts with databases, then sends responses to the client.
* Common backend languages: **Python, PHP, Node.js, Ruby, Java, Go**

**Example (PHP snippet):**

```php
<?php
  echo "Hello, " . $_GET['name'];
?>
```

---

## JavaScript Interactivity

JavaScript allows pages to update dynamically without reloading.

**Example:**

```html
<p id="demo">Original text</p>
<button onclick="document.getElementById('demo').innerHTML='Button Clicked';">
  Click Me
</button>
```

---

## Sensitive Data Exposure

Developers sometimes accidentally leave sensitive data in code.

**Bad Example:**

```html
<!-- TODO: Remove admin test credentials: username=admin, password=12345 -->
```

⚠️ If visible in source, attackers can exploit it.

**Mitigation:** Always sanitize and remove sensitive info before deployment.

---

## HTML Injection

Occurs when user input is not sanitized and is reflected back into a page.

**Malicious Example:**

```html
<script>document.location='http://attacker.com'</script>
```

⚠️ This could redirect a user or steal cookies.

**Mitigation:**

* Validate and sanitize user input.
* Use output encoding.

---

## Lifecycle of a Website Request

1. User types a URL into the browser.
2. Browser sends a request to the server.
3. Server processes the request.
4. Server sends back resources (HTML, CSS, JS).
5. Browser renders the website.

---

## Summary

* **Frontend** → HTML, CSS, JS (what the user sees)
* **Backend** → Server-side logic and databases
* JavaScript enables interactivity
* Poor coding practices can expose sensitive data
* Input must be validated to prevent HTML injection




