# HTTP & HTTPS Protocols

This repository contains detailed documentation on the fundamental protocols of the web: **HTTP** and **HTTPS**. Below is a brief overview of each, with links to the comprehensive guides located in this folder.

## Overview

### HTTP (HyperText Transfer Protocol)
**HTTP** is the foundation of data communication on the World Wide Web. It defines how messages are formatted and transmitted, and what actions web servers and browsers should take in response to various commands.

* **Key Characteristic:** Stateless protocol.
* **Security:** Sends data in plain text (unencrypted).
* **Use Case:** General web browsing where security is not a concern (becoming obsolete).
* ** Read the full guide:** [HTTP.md](HTTP.md)

### HTTPS (HyperText Transfer Protocol Secure)
**HTTPS** is the secure version of HTTP. It uses encryption (TLS/SSL) to secure the communication channel between the client and the server, ensuring that data cannot be intercepted or tampered with.

* **Key Characteristic:** Encrypted communication using Public/Private keys.
* **Security:** Uses TLS/SSL certificates to verify server identity.
* **Use Case:** Banking, login pages, shopping, and modern standard web browsing.
* ** Read the full guide:** [HTTPS.md](HTTPS.md)

---

##  File Structure

* `HTTP.md` - In-depth notes on the Request/Response cycle, Methods, Headers, and Status Codes.
* `HTTPS.md` - Comprehensive guide on Encryption, Handshakes, Certificates, and the Chain of Trust.