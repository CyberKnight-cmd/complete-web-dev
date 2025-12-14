# Computer Networking Notes from Kunal Kushwaha's Video

## Table of Contents
1.  [Introduction](#1-introduction)
    * [What is a Computer Network?](#what-is-a-computer-network)
    * [The Internet vs. The Web](#the-internet-vs-the-web)
2.  [History of the Internet](#2-history-of-the-internet)
    * [Cold War & Sputnik](#cold-war--sputnik)
    * [ARPA & ARPANET](#arpa--arpanet)
    * [Packet Switching vs. Circuit Switching](#packet-switching-vs-circuit-switching)
    * [Standardization (TCP/IP)](#standardization-tcpip)
    * [Invention of the Web (WWW)](#invention-of-the-web-www)
    * [Internet Governance (ISOC & RFCs)](#internet-governance-isoc--rfcs)
3.  [Physical Infrastructure of the Internet](#3-physical-infrastructure-of-the-internet)
    * [Submarine Cables](#submarine-cables)
    * [Cable Myths vs. Reality](#cable-myths-vs-reality)
    * [ISP Hierarchy (Tier 1, 2, 3)](#isp-hierarchy-tier-1-2-3)
4.  [Network Classifications](#4-network-classifications)
    * [PAN (Personal Area Network)](#pan-personal-area-network)
    * [LAN (Local Area Network)](#lan-local-area-network)
    * [MAN (Metropolitan Area Network)](#man-metropolitan-area-network)
    * [WAN (Wide Area Network)](#wan-wide-area-network)
    * [SAN (Storage Area Network)](#san-storage-area-network)
5.  [Network Topologies](#5-network-topologies)
    * [Bus Topology](#bus-topology)
    * [Ring Topology](#ring-topology)
    * [Star Topology](#star-topology)
    * [Tree Topology](#tree-topology)
    * [Mesh Topology (Full & Partial)](#mesh-topology-full--partial)
6.  [Network Devices (Hardware)](#6-network-devices-hardware)
    * [Repeater](#repeater)
    * [Hub (Collision & Broadcast Domains)](#hub-collision--broadcast-domains)
    * [Bridge](#bridge)
    * [Switch (CAM Table)](#switch-cam-table)
    * [Router (Routing Table)](#router-routing-table)
    * [Gateway](#gateway)
    * [Modem](#modem)
7.  [The OSI Model Overview](#7-the-osi-model-overview)
    * [The 7 Layers Mnemonic](#the-7-layers-mnemonic)
    * [Sender's Perspective (Encapsulation)](#senders-perspective-encapsulation)
    * [Receiver's Perspective (Decapsulation)](#receivers-perspective-decapsulation)
8.  [The TCP/IP Model](#8-the-tcpip-model)
    * [Comparison with OSI](#comparison-with-osi)
9.  [Deep Dive: Layer 7 - Application Layer](#9-deep-dive-layer-7---application-layer)
    * [Client-Server Architecture](#client-server-architecture)
    * [Peer-to-Peer (P2P) Architecture](#peer-to-peer-p2p-architecture)
    * [HTTP & HTTPS](#http--https)
    * [HTTP Methods (GET, POST, PUT, DELETE)](#http-methods-get-post-put-delete)
    * [HTTP Status Codes](#http-status-codes)
    * [Statelessness & Cookies](#statelessness--cookies)
    * [DNS (Domain Name System)](#dns-domain-name-system)
    * [Email Protocols (SMTP, POP3, IMAP)](#email-protocols-smtp-pop3-imap)
    * [Other Protocols (SSH, FTP, Telnet)](#other-protocols-ssh-ftp-telnet)
10. [Deep Dive: Layer 6 - Presentation Layer](#10-deep-dive-layer-6---presentation-layer)
    * [Translation](#translation)
    * [Encryption (SSL/TLS)](#encryption-ssltls)
    * [Compression](#compression)
11. [Deep Dive: Layer 5 - Session Layer](#11-deep-dive-layer-5---session-layer)
    * [Session Management](#session-management)
    * [Authentication & Authorization](#authentication--authorization)
    * [Dialog Control](#dialog-control)
12. [Deep Dive: Layer 4 - Transport Layer](#12-deep-dive-layer-4---transport-layer)
    * [Multiplexing & Demultiplexing](#multiplexing--demultiplexing)
    * [Port Numbers (Well-known, Ephemeral)](#port-numbers-well-known-ephemeral)
    * [Sockets](#sockets)
    * [TCP (Connection-Oriented, Reliable)](#tcp-connection-oriented-reliable)
    * [The 3-Way Handshake](#the-3-way-handshake)
    * [Flow Control & Error Control](#flow-control--error-control)
    * [UDP (Connection-less, Fast)](#udp-connection-less-fast)
    * [Checksums](#checksums)
13. [Deep Dive: Layer 3 - Network Layer](#13-deep-dive-layer-3---network-layer)
    * [Logical Addressing (IP Addresses)](#logical-addressing-ip-addresses)
    * [IPv4 vs IPv6](#ipv4-vs-ipv6)
    * [Packet Structure & TTL](#packet-structure--ttl)
    * [IP Classes (A, B, C, D, E)](#ip-classes-a-b-c-d-e)
    * [Subnetting & Subnet Masks](#subnetting--subnet-masks)
    * [CIDR Notation](#cidr-notation)
    * [Public vs. Private IPs](#public-vs-private-ips)
    * [NAT (Network Address Translation)](#nat-network-address-translation)
    * [Routing & Forwarding Tables](#routing--forwarding-tables)
    * [Control Plane vs. Data Plane](#control-plane-vs-data-plane)
14. [Deep Dive: Layer 2 - Data Link Layer](#14-deep-dive-layer-2---data-link-layer)
    * [Physical Addressing (MAC Addresses)](#physical-addressing-mac-addresses)
    * [Packet vs. Frame](#packet-vs-frame)
    * [ARP (Address Resolution Protocol)](#arp-address-resolution-protocol)
    * [Error Detection](#error-detection)
15. [Deep Dive: Layer 1 - Physical Layer](#15-deep-dive-layer-1---physical-layer)
    * [Bits & Signaling](#bits--signaling)
    * [Transmission Media (Copper, Fiber, Radio)](#transmission-media-copper-fiber-radio)

---

## 1. Introduction

### What is a Computer Network?
In simple terms, a **network** is just two or more computers connected together so they can share things like files, printers, or messages.

### The Internet vs. The Web
* **The Internet:** This is often called a "Network of Networks." It isn't a magic cloud above our heads; it is a massive physical mesh of wires, cables, and routers connecting billions of devices globally. It is the infrastructure (the roads).
* **The World Wide Web (WWW):** This is a service that runs *on top* of the internet. It is the collection of web pages and documents connected by hyperlinks. It is the traffic (cars/trucks) on the roads.

---

## 2. History of the Internet

The internet wasn't built for Instagram or Netflix. It started as a survival tool.

### Cold War & Sputnik
* **Context:** In the 1950s, the USA and the Soviet Union (Russia) were enemies.
* **The Catalyst:** The USSR launched the first satellite, *Sputnik*, in 1957.
* **The Fear:** The US military realized their communication lines were centralized. If the USSR nuked a central hub, the entire US communication system would collapse. They needed a decentralized network that could survive a bomb.

### ARPA & ARPANET
* **ARPA (Advanced Research Projects Agency):** The US government created this agency to lead scientific development.
* **ARPANET (1969):** This was the "Grandfather of the Internet."
    * It connected just 4 computers initially: **UCLA, Stanford (SRI), UCSB, and University of Utah**.
    * **The First Message:** A student at UCLA tried to type "LOGIN" to send to Stanford. He typed "L"... success. He typed "O"... success. Then the whole system crashed. So, the first message on the internet was just **"LO"**.

### Packet Switching vs. Circuit Switching
* **Circuit Switching (Old Way):** Like old telephones. You had to physically keep a line open between two people. If the wire broke, the call ended.
* **Packet Switching (New Way):** The breakthrough of ARPANET. Data is chopped into small "packets." Each packet can take a different route to the destination. If one road is blocked, the packet finds another way.

### Standardization (TCP/IP)
* **The Problem:** By the 80s, there were many small networks, but they spoke different languages.
* **The Solution (1983):** Vint Cerf and Bob Kahn created **TCP/IP** (Transmission Control Protocol/Internet Protocol). This was the "Universal Translator" that allowed all different networks to connect. This moment is often considered the birth of the modern Internet.

### Invention of the Web (WWW)
* **Who:** Tim Berners-Lee, a scientist at CERN.
* **When:** 1990s.
* **What:** He invented HTML (the language of webpages), the URL (address), and HTTP (the protocol).
* **First Website:** `info.cern.ch`.
* **Search Engines:** In the early days, you couldn't "Google" anything. You had to know the exact address. Yahoo! started as a manually curated list of websites.

### Internet Governance (ISOC & RFCs)
* **Internet Society (ISOC):** An organization that facilitates the open development of standards.
* **RFC (Request for Comments):** These are the formal technical documents that define how the internet works. Anyone can submit an RFC to propose a new rule, but it undergoes strict peer review.

---

## 3. Physical Infrastructure of the Internet

Many people think the internet works via satellites. **This is false.**
**99% of internet traffic travels through underwater submarine cables.**

### Submarine Cables
* **What are they?** Massive fiber-optic cables, about the thickness of a garden hose, laid on the bottom of the ocean floor connecting continents (e.g., from Mumbai to UAE, or New York to London).
* **Why cables and not satellites?**
    * **Speed:** Light travels through fiber optic glass incredibly fast. Signals to satellites have to go to space and back, causing a delay (latency).
    * **Capacity:** A single cable can carry terabits of data per second (millions of Netflix streams at once).

### Cable Myths vs. Reality
* **Myth:** "Sharks bite the cables."
* **Reality:** This used to happen rarely, but modern cables are shielded with steel armor. Most damage actually comes from ship anchors or fishing trawlers.
* **Resource:** You can see every cable connecting the world at `submarinecablemap.com`.

### ISP Hierarchy (Tier 1, 2, 3)
If the internet is a global web, who sells it to you?
1.  **Tier 1 ISPs (The Kings):** These are massive companies (like Tata Communications, AT&T) that own the actual undersea cables. They connect countries. They don't pay anyone for internet; they *are* the internet. They "peer" with each other for free.
2.  **Tier 2 ISPs (The Middlemen):** Regional companies (like Airtel or Vodafone in some contexts). They pay Tier 1 companies to access the global cables.
3.  **Tier 3 ISPs (The Local Guys):** The local provider who runs a cable to your house. You pay them, they pay Tier 2, and Tier 2 pays Tier 1.

---

## 4. Network Classifications

We categorize networks based on how much physical area they cover.

### PAN (Personal Area Network)
* **Range:** A few meters around you.
* **Example:** Connecting your Bluetooth headphones to your phone, or a USB connection.

### LAN (Local Area Network)
* **Range:** A room, a house, or an office building.
* **Characteristics:** Very fast speeds, low error rates.
* **Example:** Your home Wi-Fi or the ethernet cables connecting computers in a lab.

### MAN (Metropolitan Area Network)
* **Range:** A city or a large campus.
* **Example:** A city-wide public Wi-Fi network, or a Cable TV network connecting a whole town. Technologies like WiMAX are used here.

### WAN (Wide Area Network)
* **Range:** Countries and Continents.
* **Example:** The Internet itself is the biggest WAN. It connects multiple LANs and MANs together.

### SAN (Storage Area Network)
* **Purpose:** A specialized, high-speed network used in data centers.
* **Function:** It connects servers to massive hard drives (storage arrays) so the servers can access data incredibly fast, as if the hard drive was plugged directly into them.

---

## 5. Network Topologies

Topology refers to the shape or layout of how computers are connected.

### Bus Topology
* **Layout:** One long main cable (backbone) with computers hanging off it via drop lines.
* **Analogy:** A bus line where passengers (data) get off at stops.
* **Flaw:** If the main backbone cable snaps, the **entire** network dies. Also, only one computer can talk at a time; otherwise, data collides.

### Ring Topology
* **Layout:** Computers connected in a closed circle.
* **Method:** A digital "token" is passed around. You can only talk if you have the token.
* **Flaw:** If one computer crashes or a wire breaks, the circle is broken, and the network fails (unless you have a dual ring). It is inefficient because data must pass through every intermediate computer.

### Star Topology
* **Layout:** Every computer connects to a central box (a Hub or Switch). **Most common today.**
* **Benefit:** If your computer's wire breaks, only *you* lose internet; everyone else is fine.
* **Flaw:** If the central box (Switch) breaks, everyone goes offline.

### Tree Topology
* **Layout:** Hierarchical, like a "Star of Stars."
* **Example:** A main switch for the building connects to switches for each floor, which connect to computers.

### Mesh Topology (Full & Partial)
* **Full Mesh:** Every single device has a direct wire to every other device. (Super expensive, massive wiring, but impossible to disconnect).
* **Partial Mesh:** The Internet uses this. Routers have multiple connections to other routers, but not to *all* of them. If one path fails, traffic reroutes.

---

## 6. Network Devices (Hardware)

### Repeater
* **Problem:** Signals get weak over long distances (attenuation).
* **Solution:** A repeater receives a weak, fading signal and regenerates it to full strength so it can travel further.
* **Note:** It does *not* amplify the signal (which would amplify noise too); it recreates the original bit pattern.

### Hub (Collision & Broadcast Domains)
* **The "Dumb" Box:** It connects multiple computers in a LAN.
* **Function:** When data comes in one port, the Hub blindly broadcasts (shouts) it to **everyone** connected (C, D, E...).
* **Flaw:** It creates a single **Collision Domain** (only one device can talk at a time) and is a security risk (everyone sees everyone's data).

### Bridge
* **Function:** Connects two LAN segments together.
* **Intelligence:** It can filter traffic based on MAC addresses (e.g., "I won't let this packet pass to the other side because the recipient is on the same side as the sender").

### Switch (CAM Table)
* **The "Smart" Hub:** It connects devices in a LAN.
* **Intelligence:** It has a memory called a **CAM Table**. It learns the physical address (MAC address) of every device plugged into it.
* **Benefit:** If Computer A messages Computer B, the Switch sends data **only** to B. This allows full-duplex communication (talking and listening at the same time).

### Router (Routing Table)
* **The Traffic Cop:** It connects **different** networks (e.g., your Home Network to the ISP Network).
* **Function:** It uses **IP Addresses** to decide the best path for data to travel across the world.
* **Intelligence:** It maintains a **Routing Table** to know which path leads to which destination.

### Gateway
* **Function:** A passage to connect two networks that might be using completely different protocols. It acts as a translator/converter between them.

### Modem
* **Name:** Modulator-Demodulator.
* **Function:** Your computer speaks "Digital" (1s and 0s). The telephone/cable wire speaks "Analog" (waves). The Modem translates between these two languages.

---

## 7. The OSI Model Overview

This is the most important concept in networking. It is a theoretical framework that divides networking into **7 Layers**.

### The 7 Layers Mnemonic
**P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way.
*(Physical, Data Link, Network, Transport, Session, Presentation, Application)*

### Sender's Perspective (Encapsulation)
**Going Down (Layer 7 -> Layer 1):**
* You start at the Application layer with your data.
* As data moves down, each layer adds its own "header" (wrapper) to the data. This is like putting a letter in an envelope, then putting that envelope in a box, then putting the box in a truck.
* **L4:** Adds Port numbers (Segment).
* **L3:** Adds IP addresses (Packet).
* **L2:** Adds MAC addresses (Frame).
* **L1:** Converts to bits.

### Receiver's Perspective (Decapsulation)
**Going Up (Layer 1 -> Layer 7):**
* You receive raw signals (Bits).
* As data moves up, each layer removes its specific header and passes the remaining payload up.
* It strips the MAC, then the IP, then the Port, until the raw data is given to the application.

---

## 8. The TCP/IP Model

The OSI model is theory; the TCP/IP model is what the internet actually uses. It condenses the layers into 4 (or sometimes 5).

### Comparison with OSI
1.  **Application Layer:** Combines OSI Layers 7, 6, and 5 (Application, Presentation, Session).
2.  **Transport Layer:** Same as OSI Layer 4.
3.  **Internet Layer:** Same as OSI Layer 3 (Network).
4.  **Network Access Layer:** Combines OSI Layers 2 and 1 (Data Link, Physical).

---

## 9. Deep Dive: Layer 7 - Application Layer

**Role:** This is the layer closest to the user. It provides the interface for us to use the network.

### Client-Server Architecture
* **Client:** The requester (Your Browser, Mobile App).
* **Server:** The provider (A powerful computer in a data center).
* **Process:** The client sends a **Request**, the server processes it (looks in database, runs logic), and sends back a **Response**.

### Peer-to-Peer (P2P) Architecture
* **Concept:** No central server. Every computer is both a client and a server.
* **Example:** BitTorrent. If you download a movie, you are downloading bits of it from 50 other people's computers, and you are uploading bits to others at the same time.

### HTTP & HTTPS
* **HTTP (HyperText Transfer Protocol):** The set of rules for transferring web pages (text, images).
    * *Flaw:* It sends data in plain text. If you type a password, a hacker on the same Wi-Fi can read it.
* **HTTPS (Secure):** HTTP + SSL/TLS Encryption. It locks the data so only the server can read it. It runs on **Port 443** (HTTP is Port 80).

### HTTP Methods (GET, POST, PUT, DELETE)
* **GET:** "Hey Server, give me this data." (e.g., Opening a page).
* **POST:** "Hey Server, take this data." (e.g., Submitting a login form).
* **PUT:** "Hey Server, update/replace this data."
* **DELETE:** "Hey Server, delete this data."

### HTTP Status Codes
* **2xx (e.g., 200 OK):** Success.
* **3xx:** Redirection (The page moved somewhere else).
* **4xx (e.g., 404 Not Found):** Client Error (You typed the wrong URL).
* **5xx (e.g., 500 Internal Server Error):** Server Error (The website code crashed).

### Statelessness & Cookies
* **Stateless:** HTTP is stateless. This means the server doesn't "remember" you. Every request is treated as a new stranger.
* **The Cookie Solution:** To allow things like "Logging In" or "Shopping Carts," the server sends a tiny file called a **Cookie** to your browser. Your browser saves it and sends it back with every future request. This tells the server, "Hey, it's me again, Kunal."

### DNS (Domain Name System)
* **The Concept:** Computers don't understand "google.com"; they only understand numbers (IP Addresses like `142.250.1.1`).
* **The Phonebook:** DNS maps human names to IP addresses.
* **The Lookup Process:**
    1.  **Local Cache:** Your PC checks if it already knows the IP.
    2.  **Recursive Resolver:** Your PC asks your ISP.
    3.  **Root Server (.):** The ISP asks the Root "Who manages .com?"
    4.  **TLD Server (.com):** The ISP asks the TLD "Who manages google?"
    5.  **Authoritative Server:** The ISP asks Google's server "What is the IP?" and gets the answer.

### Email Protocols (SMTP, POP3, IMAP)
* **SMTP (Simple Mail Transfer Protocol):** Used to **SEND** emails (Push). Used by client to server, and between servers.
* **POP3 (Post Office Protocol):** Used to **RECEIVE**. It downloads email to your device and deletes it from the server. (Bad for multi-device users).
* **IMAP (Internet Message Access Protocol):** Used to **RECEIVE**. It syncs email. If you read/delete it on your phone, it happens on the server too.

### Other Protocols
* **SSH (Secure Shell):** For securely logging into remote computers (Terminals).
* **FTP (File Transfer Protocol):** Old way of sending files.
* **Telnet:** Very old, insecure way of connecting to remote computers (sends text in open).

---

## 10. Deep Dive: Layer 6 - Presentation Layer

**Role:** Making sure the data is in a readable format for the application.

### Translation
* Computers use different encoding methods. If Computer A sends ASCII (text) and Computer B expects EBCDIC, this layer translates between them. It converts string/integers into machine-readable binary.

### Encryption (SSL/TLS)
* This is where data gets scrambled so hackers can't read it. The protocol **SSL** (Secure Sockets Layer) or its successor **TLS** lives here.

### Compression
* It shrinks large files so they travel faster over the network. (e.g., video streaming services compress data here before sending).

---

## 11. Deep Dive: Layer 5 - Session Layer

**Role:** Setting up, managing, and closing the conversation (Session) between two devices.

### Session Management
* It tracks the "dialogue." It ensures that if you are downloading a file and the internet flickers, the download can resume instead of restarting from zero.

### Authentication & Authorization
* **Authentication:** Verifying who you are (Username/Password check happens here conceptually).
* **Authorization:** Verifying permissions (Are you an Admin or a Guest?).

### Dialog Control
* Decides whose turn it is to talk.
    * **Simplex:** One way only (Radio).
    * **Half-Duplex:** One at a time (Walkie-Talkie).
    * **Full-Duplex:** Both at once (Telephone).

---

## 12. Deep Dive: Layer 4 - Transport Layer

**Role:** End-to-end delivery. It ensures data gets to the right **Application** on the computer. It separates the "Network" (getting to the computer) from the "App" (getting to the software).

### Multiplexing & Demultiplexing
* **Multiplexing:** Your computer combines data from Chrome, Spotify, and Steam into one stream of packets to send out.
* **Demultiplexing:** When packets arrive, this layer sorts them: "This packet is for Chrome," "This one is for Spotify."

### Port Numbers (Well-known, Ephemeral)
* An IP Address gets data to the **House** (Computer). A Port Number gets data to the **Room** (Application).
* **Total Ports:** 65,535.
* **Well-Known Ports (0-1023):** Reserved for major protocols (HTTP=80, HTTPS=443, SSH=22).
* **Ephemeral Ports:** Temporary ports assigned to your browser tabs (e.g., Port 54321) so the server knows which tab to reply to.

### Sockets
* A **Socket** is the combination of an IP Address + A Port Number (e.g., `192.168.1.5:80`). It represents a unique endpoint in a connection.

### TCP (Connection-Oriented, Reliable)
* **Transmission Control Protocol.** The "Reliable" delivery service.
* **Ordered:** It numbers packets (1, 2, 3...) so they can be reassembled in order, even if they arrive mixed up.
* **Retransmission:** If a packet is missing, TCP asks the sender to resend it.

### The 3-Way Handshake
Before TCP sends data, it establishes a connection:
1.  **SYN:** Client sends a "Synchronize" flag ("Hi, I want to connect").
2.  **SYN-ACK:** Server sends "Synchronize-Acknowledge" ("Hi, I see you. Let's connect").
3.  **ACK:** Client sends "Acknowledge" ("Great, we are connected").

### Flow Control & Error Control
* **Flow Control:** If the server is sending too fast for the client to handle, TCP tells the server to slow down (Windowing).
* **Error Control:** Uses checksums to verify if data corrupted.

### UDP (Connection-less, Fast)
* **User Datagram Protocol.** The "Fast" delivery service.
* **Characteristics:** It throws packets at the destination without checking if they arrive. No handshake, no retransmission.
* **Use Cases:** Video Streaming, Online Gaming, Voice Calls. (Speed > Accuracy. If you lose a frame in a live game, it's better to skip it than pause the game to get it back).

### Checksums
* A math calculation performed on the data. The sender calculates a value (Checksum) and sends it. The receiver calculates it again. If the numbers don't match, the data is corrupted.

---

## 13. Deep Dive: Layer 3 - Network Layer

**Role:** Moving data between **different** networks. This is where **Routers** live.

### Logical Addressing (IP Addresses)
* Used to identify devices globally. Unlike physical addresses, logical addresses can change (e.g., if you join a different Wi-Fi).

### IPv4 vs IPv6
* **IPv4:** The old standard. 32-bits long (e.g., `192.168.1.1`). Can only generate ~4.3 billion addresses, which we have run out of.
* **IPv6:** The new standard. 128-bits long, Hexadecimal (e.g., `2001:0db8...`). Can generate $3.4 \times 10^{38}$ addresses (virtually infinite).

### Packet Structure & TTL
* **Packet:** The data unit at Layer 3. Contains Source IP and Dest IP.
* **TTL (Time To Live):** A number in the packet header (e.g., 64). Every time the packet passes a router (hops), this number decreases by 1. If it hits 0, the packet is killed. This prevents packets from looping forever in the internet.

### IP Classes (A, B, C, D, E)
* **Class A:** For massive networks (Range: 0-127).
* **Class B:** Medium networks (Range: 128-191).
* **Class C:** Small/Home networks (Range: 192-223).
* **Class D:** Multicast.
* **Class E:** Experimental.
* *Note: Loopback Address (Localhost) is `127.0.0.1`.*

### Subnetting & Subnet Masks
* **Subnetting:** Splitting a large network into smaller, secure pieces.
* **Subnet Mask:** A code (e.g., `255.255.255.0`) that tells the computer which part of the IP is the **Network** (Street) and which part is the **Host** (House).

### CIDR Notation
* **Classless Inter-Domain Routing.** The modern way to denote subnets.
* Example: `192.168.1.1/24`. The `/24` means the first 24 bits are the network.

### Public vs. Private IPs
* **Public IP:** Global. Provided by ISP. Unique across the internet.
* **Private IP:** Local. Used inside your home/office (e.g., `192.168.x.x`). Not visible to the internet.

### NAT (Network Address Translation)
* **The Problem:** We don't have enough Public IPs for every phone and laptop.
* **The Solution:** Your router has **one** Public IP. All your devices have Private IPs.
* **Process:** When you send data, the router swaps your Private IP with its Public IP. It keeps a **NAT Table** to remember who sent what, so when the reply comes back, it swaps it back to your Private IP.

### Routing & Forwarding Tables
* **Routing Table:** A map inside the router. It lists routes to different networks and the "cost" (distance/speed) to get there.
* **Forwarding Table:** A simplified version used for fast lookups to send packets to the next hop.

### Control Plane vs. Data Plane
* **Control Plane:** The brain. It runs algorithms (like OSPF, BGP) to build the map of the network.
* **Data Plane:** The muscle. It actually moves the packets based on the map.

---

## 14. Deep Dive: Layer 2 - Data Link Layer

**Role:** Moving data between devices on the **same** network (e.g., PC to Switch, Switch to Router).

### Physical Addressing (MAC Addresses)
* **Media Access Control.**
* **Format:** 48-bit Hexadecimal (e.g., `00:1A:2B:3C:4D:5E`).
* **Permanence:** Burned into the hardware (NIC). It theoretically never changes (though can be spoofed).
* **Structure:** First half identifies the Manufacturer (OUI), second half is the unique ID.

### Packet vs. Frame
* **Packet (Layer 3):** Has IP addresses.
* **Frame (Layer 2):** The packet is placed inside a Frame. The Frame adds the Source MAC and Destination MAC.
* **The Hop:** As data travels the world, the **IP Address** stays the same (mostly), but the **MAC Address** changes at every hop (from Router A to Router B).

### ARP (Address Resolution Protocol)
* **The Gap:** You know the IP (Logical) you want to talk to, but the switch only understands MACs (Physical).
* **The Protocol:**
    1.  **Request:** Broadcasts "Who has IP 192.168.1.5?"
    2.  **Reply:** The device with that IP replies "I do! Here is my MAC address."
    3.  **ARP Cache:** The computer saves this pair so it doesn't have to shout again.

### Error Detection
* The frame includes a **Trailer** (FCS/CRC). It checks if bits were flipped during transmission (e.g., due to electrical interference). If corrupted, the frame is dropped.

---

## 15. Deep Dive: Layer 1 - Physical Layer

**Role:** The actual hardware transmission of raw data.

### Bits & Signaling
* At this layer, everything is just **1s and 0s**.
* The Physical layer converts these bits into signals:
    * **Electrical Voltage:** For Copper cables (Ethernet).
    * **Light Pulses:** For Fiber Optics.
    * **Radio Waves:** For Wi-Fi.

### Transmission Media
* **Twisted Pair (Copper):** Uses electricity. Susceptible to interference.
* **Fiber Optic:** Uses light. Extremely fast, goes long distances, immune to electrical interference.
* **Wireless:** Uses radio spectrum. Convenient but prone to interference and signal loss.