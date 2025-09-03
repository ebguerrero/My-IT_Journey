 How Websites Work

---

## Overview  
When you visit a website:  
1. **Your browser (client-side)** makes a request to a web server.  
2. **The server (back-end)** processes the request and sends a response.  
3. **The browser (front-end)** renders the response as a web page for you to view.  

---

## Components of a Website  
- **Front End (Client-Side):** How the browser renders the website (HTML, CSS, JS).  
- **Back End (Server-Side):** Where the request is processed and a response is generated.  

---

## HTML (HyperText Markup Language)  
HTML is the **structure** of a webpage.  

Example HTML Document:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
</head>
<body>
  <h1>Example Heading</h1>
  <p>Example paragraph..</p>
</body>
</html>

Key Elements:
<!DOCTYPE html> → Defines HTML5 document.
<html> → Root element of the page.
<head> → Metadata (title, info).
<body> → Main content shown in the browser.
<h1> → Heading.
<p> → Paragraph.

Attributes:
<img src="img/cat.jpg"> → Adds images.
<p class="bold-text">...</p> → Adds styles.
<p id="example">...</p> → Unique identifiers.

CSS (Cascading Style Sheets)
CSS defines the look and feel of a website.
Controls layout, colors, fonts.
Works alongside HTML to style content.

JavaScript (JS)
JavaScript adds interactivity to websites.
Example: document.getElementById("demo").innerHTML = "Hack the Planet";

Events:
onclick → Triggered when an element is clicked.
Example: <button onclick='document.getElementById("demo").innerHTML="Button Clicked";'>Click Me!</button>

Sensitive Data Exposure
Occurs when websites don’t properly remove sensitive data from frontend code.
Example: credentials left in HTML comments or JavaScript variables. 
<!-- TODO: remove test credentials admin:password123 -->
⚠️ Always check source code for hidden login credentials or links.

HTML Injection
Happens when unfiltered input from users is injected into a webpage.
Example: attacker adds malicious HTML or JavaScript.
const name = document.getElementById('name').value;
document.getElementById('welcome-msg').innerHTML = "Welcome " + name;

If input is not sanitized, a user could inject: <h1>Hacked!</h1>

⚠️ Rule: Never trust user input. Always sanitize before rendering.

Summary
Front End → Rendered by browser (HTML, CSS, JS).
Back End → Processes requests and sends responses.
HTML → Structure.
CSS → Style.
JavaScript → Interactivity.
Sensitive Data Exposure → Avoid leaving secrets in source code.
HTML Injection → Prevent with strong input sanitization.
