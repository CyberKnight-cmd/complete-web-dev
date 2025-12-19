# Content Delivery Networks (CDN): The Complete Guide

Notes from [What is a CDN? by ByteByteGo](https://www.youtube.com/watch?v=RI9np1LWzqw)

## 1. Introduction: What is a CDN?

### The Core Problem: Speed of Light
When you host a website, it typically lives on a server in a specific physical location (e.g., Virginia, USA). If a user visits your site from Singapore, the data must travel through fiber optic cables under the ocean.
* **Distance:** ~15,000 km.
* **Latency:** Even at the speed of light, this round trip takes time (approx. 200-300ms).
* **Result:** The website feels slow and unresponsive.

### The Solution: Bring Content Closer
A **Content Delivery Network (CDN)** is a system of distributed servers (a network) that delivers pages and other web content to a user, based on the geographic locations of the user, the origin of the webpage, and the content delivery server.



---

## 2. Core Architecture

To understand CDNs, you must understand the geography of the internet.

### Point of Presence (PoP)
A PoP is a physical data center located in a specific city (e.g., London, Tokyo, Mumbai). CDNs have hundreds of PoPs worldwide.

### Edge Servers
Inside every PoP are powerful computers called **Edge Servers**. They sit at the "edge" of the network, physically close to the users.
* **Origin Server:** The main server where your website's database and logic live (The Source).
* **Edge Server:** The server that stores copies of your images, videos, and files (The Distributor).

---

## 3. How Users Find the Edge (Routing)

When a user types `www.example.com`, how does the internet know to send them to the London Edge Server instead of the New York Origin Server? There are two main methods.

### A. DNS-Based Routing
The Domain Name System (DNS) acts like a phonebook.
1.  User asks: "What is the IP address for example.com?"
2.  The DNS Server checks the user's location.
3.  DNS Server replies: "Since you are in London, here is the IP for the London PoP: 192.0.2.1."
* **Pros:** Easy to set up.
* **Cons:** DNS caching can sometimes send users to the wrong location if they moved recently.

### B. Anycast Routing
This is a more advanced networking technique.
1.  Every PoP in the world shares the **exact same IP address**.
2.  When the user sends a request to that IP, the physical routers of the internet automatically guide the packet to the nearest data center.
3.  **Analogy:** If you dial "911" in the US, you are connected to the nearest emergency center, even though everyone dials the same number.



---

## 4. Caching Mechanism

The Edge Server acts as a **Reverse Proxy** with a massive storage drive (Cache).

### The Flow
1.  **Request:** User asks for `logo.png`.
2.  **Check:** Edge Server looks in its cache.
3.  **Cache Miss:** If the file is not there, the Edge Server asks the Origin Server for it.
4.  **Store:** The Edge Server saves `logo.png`.
5.  **Serve:** The Edge Server sends the file to the user.
6.  **Cache Hit:** The next user who asks for `logo.png` gets the saved copy instantly.

### Static vs. Dynamic Content
* **Static Content:** Images, CSS, JavaScript files. These don't change often and are perfect for caching.
* **Dynamic Content:** User profiles, Shopping carts. These change per user and cannot be cached easily.

---

## 5. Advanced CDN Features

Modern CDNs do much more than just move files.

### Content Transformation
The CDN can modify your files on the fly to make them faster.
* **Minification:** Removing spaces and comments from JavaScript code to make the file smaller.
* **Image Optimization:** Converting a heavy PNG file into a modern, lightweight format like WebP or AVIF automatically, based on what browser the user is using.

### TLS Termination (The "Handshake")
Secure websites (HTTPS) require a "handshake" to establish encryption. This handshake requires several back-and-forth messages.
* **Without CDN:** The handshake travels all the way to the Origin (Slow).
* **With CDN:** The handshake happens with the Edge Server (Fast). The connection between the Edge and Origin is maintained separately and optimized.

---

## 6. Security & Availability

### DDoS Protection
A Distributed Denial of Service (DDoS) attack tries to crash your server by flooding it with traffic.
* **The Defense:** Because CDNs are huge networks with massive bandwidth, they can absorb the flood of traffic across thousands of servers, protecting your small Origin server from being overwhelmed.

### High Availability
If your single Origin server creates a hardware fault, your site goes down.
* **The Defense:** If one CDN Edge Server fails, the network simply routes traffic to the next closest one. The user never notices.

---

## 7. Related Concepts (Expanded)

### Reverse Proxy
A server that sits in front of one or more web servers, intercepting requests from clients. The CDN Edge Server is essentially a giant, global Reverse Proxy.

### Cache Eviction Policies
How does the Edge decide what to delete when it gets full?
* **LRU (Least Recently Used):** The standard algorithm. If the cache is full, delete the file that hasn't been asked for in the longest time.

### Cache Invalidation
The hard part. If you update your website logo, the CDN still has the old one. You must strictly tell the CDN to "Purge" the old file, or use file versioning (e.g., `logo-v2.png`) to force a fresh update.

---

## 8. Code Examples

### A. Simulating DNS vs. Anycast Logic
This Python script demonstrates how different routing strategies select a server.

```python
import math

# Simulating User Location (Coordinates)
user_location = {"x": 10, "y": 20}

# Available PoPs (Points of Presence)
pops = [
    {"name": "London", "x": 12, "y": 22, "ip": "192.168.1.10"},
    {"name": "New York", "x": 50, "y": 80, "ip": "192.168.1.20"},
    {"name": "Singapore", "x": 90, "y": 10, "ip": "192.168.1.30"}
]

def calculate_distance(loc1, loc2):
    return math.sqrt((loc1["x"] - loc2["x"])**2 + (loc1["y"] - loc2["y"])**2)

# 1. Simulation: DNS-Based Routing
# The system calculates the closest IP and gives it to the user.
def dns_routing(user, servers):
    closest_server = None
    min_dist = float('inf')

    for server in servers:
        dist = calculate_distance(user, server)
        if dist < min_dist:
            min_dist = dist
            closest_server = server
            
    return closest_server

# 2. Simulation: Anycast Routing
# All servers share the SAME IP. The network finds the path.
anycast_ip = "10.0.0.1" 

def anycast_routing(user, servers):
    # In reality, network routers do this via BGP (Border Gateway Protocol).
    # Functionally, the result is identical to finding the closest node.
    # The key difference: The User sees the same IP regardless of location.
    
    physical_server = dns_routing(user, servers) # Logic is similar
    return {
        "virtual_ip": anycast_ip,
        "physical_location": physical_server["name"]
    }

print("--- DNS Routing ---")
selected_pop = dns_routing(user_location, pops)
print(f"User routed to: {selected_pop['name']} (IP: {selected_pop['ip']})")

print("\n--- Anycast Routing ---")
network_route = anycast_routing(user_location, pops)
print(f"User connects to IP: {network_route['virtual_ip']}")
print(f"Network internally routes to: {network_route['physical_location']}")
```

### B. Simulating Cache Logic (LRU)
// A simple implementation of how an Edge server manages its memory.

```javascript
class EdgeCache {
    constructor(capacity) {
        this.capacity = capacity;
        this.cache = new Map(); // Map preserves insertion order in JS
    }

    get(key) {
        if (!this.cache.has(key)) {
            console.log(`[MISS] ${key} not found. Fetching from Origin...`);
            return -1;
        }
        
        // Refresh item: Delete and re-insert to mark as "Recently Used"
        const value = this.cache.get(key);
        this.cache.delete(key);
        this.cache.set(key, value);
        
        console.log(`[HIT] Serving ${key} from Edge.`);
        return value;
    }

    put(key, value) {
        if (this.cache.has(key)) {
            this.cache.delete(key);
        } else if (this.cache.size >= this.capacity) {
            // Evict the Least Recently Used (first item in Map)
            const oldestKey = this.cache.keys().next().value;
            console.log(`[EVICT] Cache full. Deleting ${oldestKey}`);
            this.cache.delete(oldestKey);
        }
        
        this.cache.set(key, value);
        console.log(`[STORE] Saved ${key} to Edge Cache.`);
    }
}

// Simulation
const cdn = new EdgeCache(2); // Small cache size of 2 items

cdn.put("logo.png", "IMAGE_DATA");
cdn.put("style.css", "CSS_DATA");

cdn.get("logo.png"); // Access logo, making it "fresh"

// We add a 3rd item, forcing eviction
cdn.put("script.js", "JS_DATA"); 
// Since 'style.css' was the least recently used, it gets deleted.

cdn.get("style.css"); // Should be a MISS
```