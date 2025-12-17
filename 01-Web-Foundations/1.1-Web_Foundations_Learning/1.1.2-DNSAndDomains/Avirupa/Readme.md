# DNS (Domain Name System) in Details
*Based on notes from NetworkChuck's "What is DNS?"*
[What is DNS? (and how it makes the Internet work) by NetworkChuck][def]

## 1. What is DNS? (The Phonebook of the Internet)
**Concept:**
Your web browser (Chrome, Firefox, Safari) is technically "dumb." It does not know where websites live physically.
* **Humans** remember names (e.g., `google.com`, `academy.networkchuck.com`).
* **Computers** need IP addresses (e.g., `142.250.190.46`).

**The Analogy:**
Imagine an old-school phone. You cannot dial "Bernard" directly on a rotary phone. You must look up Bernard in your contacts list to find his number (`555-0199`).
* **Contact Name** = Domain Name (`google.com`)
* **Phone Number** = IP Address (`8.8.8.8`)
* **Contacts App** = DNS Server

**Definition:**
**DNS (Domain Name System)** is the protocol that maps human-readable domain names to machine-readable IP addresses. Without it, you would have to memorize the IP address of every website you want to visit.

---

## 2. The Players: Stub Resolver vs. DNS Resolver

**What is the difference between a stub resolver and a DNS resolver?**

* **Stub Resolver:**
    The client-side component (inside your OS/computer) that initiates the query. It is a simple "messenger." It doesn't know how to search the internet; it only knows how to ask for help.
* **DNS Resolver (Recursive Resolver):**
    The server-side component (typically provided by your ISP or a service like Google `8.8.8.8` or Cloudflare `1.1.1.1`). This is the "investigator" that performs the actual lookup work by talking to other servers.

**Relationship:**
The two work together, with the stub resolver forwarding requests to the recursive DNS resolver.

---

## 3. The Anatomy of a URL & Domain Structure

To understand DNS, you often read a URL from **Right to Left**.
Example: `blog.example.com.` (Note the silent dot at the end representing the Root).

### The Hierarchy
1.  **Root (`.`):** The invisible starting point.
2.  **TLD (Top Level Domain):** `.com`, `.org`, `.net`, `.gov`.
3.  **SLD (Second Level Domain):** The name you buy (`example`, `google`, `networkchuck`).

### What is a Subdomain?
An add-on to your primary domain name. It appears **before** the main domain name in a URL and is used to organize different sections or functions of a website.

**Real World Examples:**
* `store.playstation.com` -> Separates the shop from the main site.
* `mail.google.com` -> Separates the email service from the search engine.
* `dev.example.com` -> A testing environment for developers.

---

## 4. The DNS Workflow (The Journey of a Query)

Here is the step-by-step process of what happens when you try to visit a website.

**Step 1: The Request**
-> You type `www.example.com` into the browser.

**Step 2: The Local Check (Stub Resolver)**
-> **Stub Resolver** checks the local cache (memory).
    * **If found:** It gives the IP to the browser immediately. (e.g., You just visited the site 5 minutes ago).
    * **If not:** It asks the **Recursive Resolver** (ISP/Google) to find it.

**Step 3: The Recursive Search Begins**
-> **Recursive Resolver** checks its own cache. If empty, it starts the hunt.

**Step 4: The Root (The "Mafia Bosses")**
-> **Recursive Resolver** asks the **Root Server** (There are 13 logical root clusters worldwide).
    * **Root replies:** "I don't know the IP for example.com, but I know who handles all `.com` websites. Here is the address for the **.com TLD server**."

**Step 5: The TLD (Top Level Domain)**
-> **Recursive Resolver** (not the Root) goes to the **TLD Server**.
    * **TLD replies:** "I don't know the specific IP for `www.example.com`, but I know who owns that domain name. Here is the address for the **Authoritative Nameserver** (e.g., AWS Route53, GoDaddy, Cloudflare)."

**Step 6: The Authority (The Source of Truth)**
-> **Recursive Resolver** goes to the **Authoritative Server** (SLD Server).
    * **Authoritative replies:** "Yes, I have it. The IP address is `93.184.216.34`."

**Step 7: The Return Trip**
-> **Recursive Resolver** sends that IP back to the **Stub Resolver**, which gives it to the **Browser**.

**Step 8: The Connection**
-> **Browser** uses the IP (`93.184.216.34`) to finally connect to the website and download the page.

---

## 5. DNS Security: Spoofing & DoH

### What is DNS Spoofing?
DNS Spoofing (often called **Cache Poisoning**) relies on the fact that standard DNS is "gullible."

When your computer asks, "What is the IP for `facebook.com`?", it shouts this question out in plain text using a protocol called **UDP**. UDP is fast but insecure—it’s like sending a postcard.

* **The Vulnerability:** Your computer accepts the **first** answer it gets. It doesn't verify who sent it.
* **The Attack:** A hacker on your Wi-Fi network (or a compromised router) sees your request. They immediately race to send a fake reply: *"I am the server! Facebook is at IP 6.6.6.6"* (which is actually a virus site).
* **The Result:** Your computer believes the hacker, saves (caches) that fake IP, and sends you to the fake site.

### What is DoH? (The Defense)
**DNS over HTTPS (DoH)** changes the rules. Instead of shouting the question in plain text, your browser wraps the DNS query inside an encrypted **HTTPS packet**—the same secure protocol used for online banking.

It sends this packet to a specific, trusted provider (like Google or Cloudflare) over **port 443** (the standard web traffic port).

### How DoH Prevents Spoofing
DoH stops spoofing not just by hiding the data, but by verifying the source. It kills the attack in three ways:

1.  **Authentication (The ID Check)**
    * In standard DNS, you talk to whoever answers. In DoH, your browser establishes a secure TLS connection (handshake) with the DNS server.
    * *How it stops spoofing:* The server must present a **digital certificate** to prove it really is who it says it is (e.g., "I am Google DNS"). A hacker cannot fake this certificate. If the certificate doesn't match, your browser drops the connection immediately.

2.  **Integrity (The Tamper Seal)**
    * Because the data is sent over HTTPS/TLS, the data is digitally signed.
    * *How it stops spoofing:* If a hacker tries to intercept the packet and change the IP address inside from "Real Facebook" to "Fake Facebook," the "tamper seal" breaks. The encryption check fails, and your computer rejects the corrupted packet.

3.  **Encryption (The Invisibility Cloak)**
    * Standard DNS is visible to everyone on the network.
    * *How it stops spoofing:* With DoH, the hacker looking at your traffic sees only indecipherable gibberish. They don't even know what website you are asking for, so they don't know which fake IP to send you.

### Other Security Tools
DNS Spoofing can also be handled by:
* **DoT (DNS over TLS):** Encrypts DNS, but uses a dedicated port (853) instead of hiding in web traffic.
* **DNSCrypt:** An older protocol to authenticate DNS traffic.
* **DNSSEC:** Adds a cryptographic signature to the DNS records themselves to prove they haven't been altered.
* **Quad9 (9.9.9.9):** A DNS provider that specifically blocks known malicious domains (malware/phishing).

---

## 6. Detailed Descriptions: Records, TTL & Servers

### What are DNS Records?
The "Zone File" on the Authoritative Server is like a database containing different types of information. It's not just IP addresses.

| Record Type | Name | Purpose | Example |
| :--- | :--- | :--- | :--- |
| **A** | Address | Maps a domain to an **IPv4** Address. | `google.com -> 142.250.190.46` |
| **AAAA** | Quad A | Maps a domain to an **IPv6** Address. | `google.com -> 2001:4860:4860::8888` |
| **CNAME** | Canonical Name | **Alias**. Points one domain to another domain (not an IP). | `blog.site.com -> site.com` |
| **MX** | Mail Exchange | Points to the servers that handle **Email**. | `gmail-smtp-in.l.google.com` |
| **TXT** | Text | Arbitrary text. Used for verification and email security (SPF/DKIM). | `v=spf1 include:_spf.google.com ~all` |
| **NS** | Nameserver | Tells the internet **who** is the authoritative DNS server. | `ns1.cloudflare.com` |
| **PTR** | Pointer | **Reverse DNS**. Maps an IP address back to a domain name. | `1.1.1.1 -> one.one.one.one` |

### What is TTL? (Time To Live)
**Definition:**
TTL is a setting on every DNS record that tells servers (stub resolvers and recursive resolvers) **how long to cache (remember)** that record before checking for a new one. It is measured in seconds.

* **Long TTL (e.g., 24 hours):** Good for stable sites; makes loading faster.
* **Short TTL (e.g., 5 minutes):** Good for changing sites; updates propagate quickly.

### What are DNS Nameservers?
**Definition:**
A Nameserver is a server that stores the DNS records for a domain. It answers questions from other computers about that domain.

1.  **Root Nameservers:** The 13 sets of servers at the top of the hierarchy.
2.  **TLD Nameservers:** Manage `.com`, `.org`, etc.
3.  **Authoritative Nameservers:** The final destination. If you buy a domain on GoDaddy but use Cloudflare to manage it, Cloudflare's servers (e.g., `ns1.cloudflare.com`) are your **Authoritative Nameservers**.

---

## 7. Buying a Domain (The Administrative Side)

1.  **ICANN:** The global non-profit organization that coordinates the internet's naming system.
2.  **Registrar:** Companies accredited by ICANN to sell domains (e.g., Squarespace, Namecheap, GoDaddy).
3.  **The Process:**
    * You buy `ilovecoffee.coffee` from a Registrar.
    * You choose your **Nameservers** (e.g., default Squarespace servers OR custom ones like Cloudflare).
    * The Registrar updates the TLD Registry to point to your chosen Nameservers.
    * **WHOIS:** A public database of domain owners. (You can usually pay to redact this for privacy).

---

## 8. Hands-On: How to Query DNS Yourself

You don't need a browser to check DNS. You can use the terminal.

### Using `nslookup` (Windows/Mac/Linux)
The basic tool to query a nameserver.

```bash
# Basic lookup (asks your default DNS server)
nslookup academy.networkchuck.com

# Specific lookup (ask Google's 8.8.8.8 directly)
nslookup academy.networkchuck.com 8.8.8.8

# Ask for a specific record type (e.g., Email servers)
nslookup -type=MX networkchuck.com
```

### Using `dig` (Linux/Mac - The Pro Tool)
`dig` (Domain Information Groper) gives much more detail, including the TTL and query time.

```bash
# Standard lookup
dig networkchuck.com

# Trace the hierarchy (Watch the recursive journey happen!)
# This shows the Root -> TLD -> Auth path.
dig networkchuck.com +trace
```

---

## 9. Advanced: Running Your Own DNS (Home Lab)

You can replace your router's default DNS with your own local server using a Raspberry Pi or a Docker container.

* **Pi-hole / AdGuard Home:**
    * Acts as a local DNS server.
    * **Blackholing:** If a request matches an ad server list (e.g., `ads.google.com`), it returns `0.0.0.0` (nothing).
    * Blocks ads and trackers network-wide for all devices (phones, smart TVs, etc.).

[def]: https://www.youtube.com/watch?v=NiQTs9DbtW4