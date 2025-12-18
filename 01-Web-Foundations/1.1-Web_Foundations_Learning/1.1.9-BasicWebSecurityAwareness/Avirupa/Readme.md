# Basic Web Security Awareness: XSS, CSRF, CORS, and Secrets

## 1. Core Concepts: How the Web Talks
Before understanding attacks, you must understand how data moves on the web.

### GET vs. POST Requests
The web relies on sending data back and forth. There are two main ways browsers do this:

* **GET Request:** Designed for **fetching** data.
    * Data is visible in the URL (e.g., `youtube.com/watch?v=123xyz`).
    * It is "idempotent," meaning you can refresh the page without changing anything on the server.
    * **Risk:** You can copy-paste this URL to a friend. If the URL contained a command like `?transfer_money=1000`, and you sent it to a friend, they might accidentally trigger it just by clicking.

* **POST Request:** Designed for **writing** or changing data (submitting forms, logging in).
    * Data is bundled inside the request body, not the URL.
    * It is meant to happen once. (This is why browsers warn you if you refresh a page after submitting a form).
    * **Security Rule:** Never use GET requests for actions that change data (like deleting an account or sending money).

### The Cookie and The Session
When you log into a website (like a bank), the server gives your browser a "Session Cookie." This is like an ID card. Every time you click a link on the bank's website, your browser automatically shows this ID card so the bank knows it is you.

**The Vulnerability:** Browsers are helpful. If you are logged into Bank.com, and you visit a completely different site, your browser might *still* send your Bank.com ID card if that other site tries to talk to the bank. This leads us to CSRF.

---

## 2. CSRF (Cross-Site Request Forgery)
*Topic heavily featured in transcript.*

### What is it?
CSRF is an attack where a malicious website tricks a user's browser into performing an unwanted action on a trusted site where the user is currently logged in.

### The Mental Model
Imagine you send a letter to your bank asking to transfer money. You sign it and put it in the mailbox.
CSRF is like a thief putting a pre-written letter in *your* mailbox. The postman (your browser) sees it in your mailbox, assumes you wrote it because it uses your stamp (cookie), and delivers it to the bank. The bank processes it because the signature looks real.

### Real-World Example
1.  **The User** logs into their online bank (`bad-bank.com`). The bank gives them a session cookie.
2.  **The User**, in a new tab, visits `my-awesome-blog.com` (a malicious site).
3.  **The Attack:** `my-awesome-blog.com` has a hidden form or a script that runs automatically in the background.
4.  **The Execution:** This script sends a POST request to `bad-bank.com/transfer` sending money to the hacker.
5.  **The Failure:** The browser sees the request going to `bad-bank.com`, automatically attaches the user's session cookie, and the bank processes the transaction thinking the user intended to do it.

### Defense: Anti-CSRF Tokens (The "Nonce")
The transcript mentions a "One Time Key" or "Nonce". This is the standard defense.

1.  **Generation:** When the user visits the transfer form on the real bank site, the server generates a random, secret string (e.g., `a82b9c...`).
2.  **Embedding:** This string is hidden inside the HTML form as a hidden input field: `<input type="hidden" name="csrf_token" value="a82b9c...">`.
3.  **Verification:** When the user clicks "Submit", the server checks if the token in the form matches the one it gave the user.

**Why this works:** The malicious blog cannot see the real bank's website content due to browser security rules (Same-Origin Policy). Therefore, the hacker cannot guess or steal this random token. They can send the request, but without the correct token, the bank rejects it.

---

## 3. XSS (Cross-Site Scripting)
*Topic mentioned in transcript.*

### What is it?
XSS allows an attacker to inject malicious code (usually JavaScript) into a website, which is then executed by the browser of another user.

### The Mental Model
The browser trusts whatever code the website sends it. If a hacker can trick the website into displaying the hacker's text as code, the browser will run it. It is like writing "Kick me" on a sticky note and sticking it on someone's back; the victim displays the message, and others react to it.

### Types of XSS
1.  **Stored XSS:** The hacker posts a comment containing a script (e.g., `<script>stealCookies()</script>`). This script is saved in the database. Every user who views that comment runs the script.
2.  **Reflected XSS:** The hacker sends a link like `site.com/search?q=<script>...`. If the site displays the search term back to the user without cleaning it, the script runs.

### Defense: Sanitization and Escaping
Never trust user input. Before displaying text on the screen, convert special characters into HTML entities.
* Convert `<` to `&lt;`
* Convert `>` to `&gt;`
This ensures the browser treats the input as text, not code. Modern frameworks like React and Vue do this automatically.

---

## 4. SOP and CORS (Cross-Origin Resource Sharing)
*Related concept required for mastery.*

### Same-Origin Policy (SOP)
This is the most important security rule in a browser. It states: **A script running on Site A cannot read data from Site B.**
Without this, `my-awesome-blog.com` could simply use JavaScript to read your emails from `gmail.com` if you had Gmail open in another tab.

### What is CORS?
Sometimes, you *want* Site A to talk to Site B (e.g., your frontend accessing your API on a different domain).
CORS is a way for the server (Site B) to tell the browser: "It is okay, I trust Site A. You can let them read this data."

**The Pitfall:** Developers often get lazy and allow *anyone* to access their data.
* **Bad:** `Access-Control-Allow-Origin: *` (Allows everyone).
* **Good:** `Access-Control-Allow-Origin: https://my-trusted-site.com` (Allows only specific sites).

---

## 5. Secret Handling
*Best practice required for mastery.*

Web applications use "secrets" like API keys, database passwords, and encryption keys.

### The Golden Rules
1.  **Never commit secrets to Git:** If you push a password to GitHub, bots will find it in seconds.
2.  **Use Environment Variables:** Store secrets in a file (usually named `.env`) on your server/computer, and read them into your program.
3.  **Use .gitignore:** Tell Git to ignore the `.env` file so it is never uploaded.

---

## 6. Runnable Code Example

This is a Python example using the Flask framework. It demonstrates a secure implementation using a CSRF token and proper secret handling.

**Prerequisites:** Python installed.
**Setup:**
1.  Save the code below as `app.py`.
2.  Install Flask: `pip install flask`
3.  Run the app: `python app.py`
4.  Open your browser to `http://127.0.0.1:5000`.

### The Code (`app.py`)

```python
import os
import random
import string
from flask import Flask, request, session, render_template_string, redirect, url_for

app = Flask(__name__)

# SECURITY TIP: Secret Handling
# We get the secret key from the environment, or generate a random one if missing.
# In production, NEVER hardcode this.
app.secret_key = os.environ.get("SECRET_KEY", "dev_secret_key_do_not_use_in_prod")

# A simple "database" of money
user_balance = 1000

# HTML Template with Embedded Python (Jinja2)
# Notice the hidden input field: csrf_token
HTML_FORM = """
<!DOCTYPE html>
<html>
<head><title>Secure Bank</title></head>
<body>
    <h1>Welcome to Secure Bank</h1>
    <p>Current Balance: ${{ balance }}</p>
    
    <h2>Transfer Money</h2>
    <form method="POST" action="/transfer">
        <input type="hidden" name="csrf_token" value="{{ csrf_token }}">
        
        <label>Amount: <input type="number" name="amount" required></label>
        <button type="submit">Transfer</button>
    </form>

    {% if message %}
        <p style="color: red;">{{ message }}</p>
    {% endif %}
</body>
</html>
"""

def generate_csrf_token():
    if 'csrf_token' not in session:
        # Generate a random string of characters
        session['csrf_token'] = ''.join(random.choices(string.ascii_letters + string.digits, k=32))
    return session['csrf_token']

@app.route('/', methods=['GET'])
def home():
    token = generate_csrf_token()
    return render_template_string(HTML_FORM, balance=user_balance, csrf_token=token, message="")

@app.route('/transfer', methods=['POST'])
def transfer():
    global user_balance
    
    # SECURITY TIP: CSRF Validation
    # We check if the token sent in the form matches the token in the user's session.
    # An attacker on a different site cannot read the session or the page content,
    # so they cannot include the correct token in their forged request.
    
    form_token = request.form.get('csrf_token')
    session_token = session.get('csrf_token')

    if not form_token or form_token != session_token:
        return "CSRF Attack Detected! Request blocked.", 403

    # If token matches, proceed with logic
    amount = int(request.form.get('amount'))
    user_balance -= amount
    
    # SECURITY TIP: XSS Prevention
    # Flask/Jinja2 automatically escapes text here, preventing XSS 
    # if we were to reflect user input back to the screen.
    
    return render_template_string(HTML_FORM, balance=user_balance, csrf_token=session_token, message=f"Transferred ${amount}!")

if __name__ == '__main__':
    app.run(debug=True)
```

### Analysis of the Code
1.  **Secret Handling:** `app.secret_key` is pulled from environment variables (`os.environ`).
2.  **CSRF Protection:**
    * A random token is generated and stored in the `session` (server-side).
    * This token is passed to the HTML as a `hidden` input value.
    * When the POST request arrives, the server compares the form's token against the session's token.
3.  **HTTP Verbs:** The transfer action only accepts `POST`, never `GET`.