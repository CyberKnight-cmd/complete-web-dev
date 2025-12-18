# HTTP in Details

Notes made from [HTTP Crash Course & Exploration by Traversy Media](https://www.youtube.com/watch?v=iYM2zFP3Zn0&t=85s)

## 1. What is HTTP?

**HTTP** stands for **Hypertext Transfer Protocol**. It is the set of rules (protocol) responsible for communication between web servers (where the website lives) and clients (your browser or mobile app).

### The Request / Response Cycle
Every interaction on the web typically follows this cycle:
1.  **The Client** (Browser) sends a **Request** to the Server.
2.  **The Server** processes the request.
3.  **The Server** sends back a **Response** (HTML, JSON, CSS, Images, etc.).

### Key Concept: Statelessness
HTTP is a **Stateless Protocol**.
* **Definition:** The server does not retain any memory of the previous request. Every request is treated as a completely new, independent transaction.
* **Implication:** If you log in on Page A, and click a link to Page B, HTTP doesn't natively know you are the same person.
* **Workarounds:** We use cookies, sessions, and local storage to "fake" state and remember users across different requests.

### HTTP vs. HTTPS
* **HTTP:** Data is sent in "plain text." If a hacker intercepts the data between you and the server, they can read your passwords and credit card numbers.
* **HTTPS (Secure):** Uses **SSL (Secure Sockets Layer)** or **TLS (Transport Layer Security)** to encrypt the data.
    * **How it works:** An encrypted "tunnel" is created. If a hacker intercepts the data, it looks like gibberish.
    * **Requirement:** You need an SSL Certificate installed on your web host. Modern web standards practically enforce HTTPS for all sites.

---

## 2. HTTP Methods (The Verbs)

When a client talks to a server, it must indicate *what* it wants to do. These are defined by **HTTP Methods**.

| Method | Description | Safe/Idempotent | Usage Example |
| :--- | :--- | :--- | :--- |
| **GET** | Fetches data from the server. Used for loading pages, images, and CSS. Data is NOT sent in the body, but in the URL. | **Safe** (Read-only) | `GET /api/users` |
| **POST** | Sends data to the server to create a new resource. Data is hidden in the **Request Body**. | **Unsafe** (Changes data) | `POST /api/users` (Submitting a sign-up form) |
| **PUT** | Updates an existing resource. Usually replaces the entire entry. | **Unsafe** | `PUT /api/users/1` (Update user ID 1) |
| **DELETE** | Removes a resource from the server. | **Unsafe** | `DELETE /api/users/1` (Delete user ID 1) |

> **Note on Forms:** HTML Forms naturally support GET and POST.
> * **GET Forms:** Search bars (filters appear in the URL: `?search=cat`).
> * **POST Forms:** Login/Register (sensitive data is hidden in the body).

---

## 3. HTTP Headers (The Metadata)

Headers are key-value pairs sent with both the Request and the Response. They provide "metadata" (data about the data).



### Three Categories of Headers:
1.  **General Headers:** Apply to both request and response (e.g., `Date`).
2.  **Request Headers:** Info about the client (e.g., "I am using Chrome").
3.  **Response Headers:** Info about the server (e.g., "Here is a JSON file").

### Common Header Fields
* **Request URL:** The specific path being requested.
* **Status Code:** (Response only) Did it succeed or fail?
* **Remote Address:** The IP address of the remote computer.
* **Authorization:** Used to send credentials (tokens/passwords) to prove identity.
* **User-Agent:** A string identifying the OS and Browser of the client (e.g., `Mozilla/5.0 (Macintosh; Intel Mac OS X...)`).
* **Content-Type:** **(Crucial)** Tells the receiver what type of data is being sent.
    * `text/html`: HTML web page.
    * `text/css`: Style sheet.
    * `application/json`: JSON data (APIs).
    * `application/x-www-form-urlencoded`: Standard form data.
    * `image/png`: An image.
* **Content-Length:** The size of the data in octets (8-bit bytes).
* **Set-Cookie:** Sent by the server to tell the browser to save a cookie.

---

## 4. HTTP Status Codes

When a server responds, it gives a 3-digit number indicating the result.

### The Ranges
* **1xx:** Informational (Request received, processing).
* **2xx:** Success (The action was successfully received and understood).
* **3xx:** Redirection (Further action must be taken).
* **4xx:** Client Error (The request contains bad syntax or cannot be fulfilled).
* **5xx:** Server Error (The server failed to fulfill a valid request).

### Important Codes to Memorize

| Code | Meaning | Context |
| :--- | :--- | :--- |
| **200** | **OK** | Standard success for GET, PUT, or PATCH. |
| **201** | **Created** | Success specifically for POST when a new resource is made. |
| **301** | **Moved Permanently** | This URL has moved; go here instead. |
| **304** | **Not Modified** | The data is cached in your browser and hasn't changed on the server. No new data sent. |
| **400** | **Bad Request** | You sent invalid data (e.g., missing a required field). |
| **401** | **Unauthorized** | You are not logged in or provided a bad password/token. |
| **403** | **Forbidden** | You are logged in, but you don't have permission to see this. |
| **404** | **Not Found** | The resource/URL does not exist. |
| **500** | **Internal Server Error** | The server crashed or had a bug. It's not the user's fault. |

---

## 5. HTTP Versions: 1.1 vs 2.0

* **HTTP/1.1:** The standard for a long time. It loads assets (images, scripts) sequentially (one after another), which can cause "blocking."
* **HTTP/2:** The modern standard.
    * **Multiplexing:** It can send multiple files (HTML, CSS, JS) over a single connection simultaneously.
    * **Efficiency:** Compressed headers and binary format make it much faster.
    * **Note:** Changes are mostly under the hood; developers write code the same way.

---

## 6. Practical Implementation: Node.js & Express

The following is a complete guide to building a server that handles HTTP requests, demonstrating how to manipulate status codes, headers, and body data manually.

### Prerequisites
1.  Install Node.js.
2.  Initialize a project: `npm init -y`
3.  Install Express: `npm install express`

### The Server Code (`server.js`)

```javascript
const express = require('express');
const app = express();
const PORT = 5000;

// --- MIDDLEWARE ---
// Express needs middleware to understand the 'body' of a request.
// Without these lines, req.body will be undefined.

// 1. To parse JSON data (application/json)
app.use(express.json()); 
// 2. To parse Form data (application/x-www-form-urlencoded)
app.use(express.urlencoded({ extended: false }));

// --- STATIC FILES ---
// Serves HTML/CSS/JS from a folder named 'public' automatically
app.use(express.static('public'));


// --- ROUTES ---

/**
 * GET Request
 * Access via browser: http://localhost:5000/
 */
app.get('/', (req, res) => {
    // res.send automatically detects content type. 
    // Sending a string sets 'Content-Type': 'text/html'
    res.send('<h1>Hello from Express!</h1>');
});

/**
 * POST Request - Receiving Data
 * Best tested via Postman
 */
app.post('/contact', (req, res) => {
    // req.body contains the data sent by the client
    const { name, email } = req.body;

    // VALIDATION (Manual Status Codes)
    if (!name) {
        // sending a 400 Bad Request
        return res.status(400).send('Name is required');
    }

    // SUCCESS (201 Created)
    // res.status chains the code, .send sends the body
    res.status(201).send(`Thank you ${name}, we received your email: ${email}`);
});

/**
 * HEADERS & AUTHENTICATION
 * Checking for a specific token in the request headers
 */
app.post('/login', (req, res) => {
    // Access header values using req.header('key')
    const token = req.header('x-auth-token');

    // 1. Check if token exists
    if (!token) {
        return res.status(400).send('No Token Included');
    }

    // 2. Validate token (Simulated)
    if (token !== '123456') {
        return res.status(401).send('Not Authorized (Invalid Token)');
    }

    // 3. Success
    res.send('Logged In Successfully');
});

/**
 * PUT Request - Updating Data
 * Uses URL Parameters (e.g., /post/99)
 */
app.put('/post/:id', (req, res) => {
    // req.params accesses the URL variables (:id)
    const postId = req.params.id;
    const newTitle = req.body.title;

    // Simulate database update
    res.json({
        id: postId,
        title: newTitle,
        status: 'updated'
    });
});

/**
 * DELETE Request
 */
app.delete('/post/:id', (req, res) => {
    const postId = req.params.id;
    res.send(`Post ${postId} has been deleted.`);
});


// Start Server
app.listen(PORT, () => console.log(`Server started on port ${PORT}`));
```
---

## 7. Tools for Inspecting HTTP

### 1. Browser DevTools (Chrome/Firefox)
This is the best way to see what your browser is doing.
1.  Press `F12` or Right Click -> `Inspect`.
2.  Go to the **Network** Tab.
3.  Refresh the page.
4.  **Analyze:**
    * **Name:** The file requested.
    * **Status:** The code (e.g., 200, 304).
    * **Type:** The content type (document, stylesheet, script).
    * **Waterfall:** Shows load order (HTTP/1.1 vs HTTP/2 visualization).
5.  **Click a Request:** You can view the **Headers** tab to see specific Request/Response metadata.

### 2. Postman (API Client)
Browsers are great for GET requests, but hard to use for testing POST/PUT/DELETE without building a frontend form. **Postman** solves this.

**How to simulate a POST request in Postman:**
1.  Set method to **POST**.
2.  Enter URL (e.g., `localhost:5000/contact`).
3.  Go to the **Body** tab.
4.  Select **raw** and ensure the dropdown is set to **JSON**.
5.  Enter JSON data:
    ```json
    {
      "name": "Brad",
      "email": "brad@gmail.com"
    }
    ```
6.  Click **Send**.
7.  View the status code and response body in the bottom pane.

---

## Summary Checklist
* **HTTP** is the language of the web.
* **HTTPS** encrypts that language using SSL/TLS.
* **Headers** carry metadata (Content-Type, Auth Tokens).
* **Body** carries the actual data (HTML files, JSON form data).
* **GET** is for reading, **POST** is for writing.
* **200** is good, **400** is your fault (client), **500** is the server's fault.
* **Stateless** means the server forgets you immediately after responding; use tokens/cookies to remind it who you are.