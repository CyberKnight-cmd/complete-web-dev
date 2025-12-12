# Computer Networking Notes from Sheryians Coding School's Video

## Table of Contents
1.  [1. What is the Internet?](#1-what-is-the-internet)
    * [Core Function](#core-function)
    * [The Language (TCP/IP)](#the-language)
2.  [2. History of the Internet](#2-history-of-the-internet)
    * [ARPA (Advanced Research Projects Agency)](#arpa-advanced-research-projects-agency)
    * [The Goal](#the-goal)
    * [1969 - The First Message (ARPANET)](#1969---the-first-message)
    * [1983 - Standardization (TCP/IP)](#1983---standardization)
    * [1990s - The Web (Tim Berners-Lee)](#1990s---the-web)
3.  [3. How Is Data Transferred?](#3-how-is-data-transferred)
    * [A. IP Address (The Home Address)](#a-ip-address-the-home-address)
        * [Definition](#definition)
        * [Versions (IPv4 & IPv6)](#versions)
    * [B. Port Numbers (The Apartment Number)](#b-port-numbers-the-apartment-number)
        * [Analogy](#analogy)
        * [Range (Well-Known, Registered, Dynamic)](#range)
    * [C. Example: How WhatsApp Transmits a Message](#c-example-how-whatsapp-transmits-a-message)
4.  [4. Domain Name System (DNS)](#4-domain-name-system-dns)
    * [Function](#function)
    * [The DNS Resolution Process (Step-by-Step)](#the-dns-resolution-process-step-by-step)
5.  [5. Types of Networks](#5-types-of-networks)
    * [PAN (Personal Area Network)](#pan-personal-area-network)
    * [LAN (Local Area Network)](#lan-local-area-network)
    * [CAN (Campus Area Network)](#can-campus-area-network)
    * [MAN (Metropolitan Area Network)](#man-metropolitan-area-network)
    * [WAN (Wide Area Network)](#wan-wide-area-network)
    * [VPN (Virtual Private Network)](#vpn-virtual-private-network)
6.  [6. Network Topologies](#6-network-topologies)
    * [A. Bus Topology](#a-bus-topology)
    * [B. Ring Topology](#b-ring-topology)
    * [C. Star Topology](#c-star-topology)
    * [D. Mesh Topology](#d-mesh-topology)
    * [E. Tree Topology](#e-tree-topology)
    * [F. Hybrid Topology](#f-hybrid-topology)
7.  [7. OSI Model](#7-osi-model)
    * [Mnemonic to remember](#mnemonic-to-remember)
    * [Layers (Sender's & Receiver's Perspective)](#layers-top--bottom-the-senders-perspective-and-bottom--top-the-receivers-perspective)
        * [7. Application Layer](#7-application-layer)
        * [6. Presentation Layer](#6-presentation-layer)
        * [5. Session Layer](#5-session-layer)
        * [4. Transport Layer](#4-transport-layer)
        * [3. Network Layer](#3-network-layer)
        * [2. Data Link Layer](#2-data-link-layer)
        * [1. Physical Layer](#1-physical-layer)
8.  [8. Client-Server vs. Peer-to-Peer](#8-client-server-vs-peer-to-peer)
    * [Client-Server Architecture](#client-server-architecture)
        * [Request-Response Cycle](#request-response-cycle)
    * [Peer-to-Peer (P2P) Architecture](#peer-to-peer-p2p-architecture)
        * [Concept & Usage](#concept)
9.  [9. Key Internet Protocols](#9-key-internet-protocols)
    * [HTTP vs. HTTPS](#http-vs-https)
    * [IP (Internet Protocol)](#ip-internet-protocol)
    * [TCP (Transmission Control Protocol)](#tcp-transmission-control-protocol)
    * [UDP (User Datagram Protocol)](#udp-user-datagram-protocol)
10. [Appendix](#appendix)

---

## 1. What is the Internet?

The **Internet** is not a single cloud or magic box; it is a global system of interconnected computer networks. It is essentially a massive web of physical cables (fiber optics under the ocean) and wireless signals that allow billions of devices to talk to each other.

* **Core Function:** It enables data transfer between electronic devices (computers, phones, servers, IoT devices) worldwide.
* **The Language:** To communicate, all these different devices must speak the same language. This "language" is a set of standardized protocols known as **TCP/IP** (Transmission Control Protocol/Internet Protocol).

---

## 2. History of the Internet

The Internet started as a military project, not a public utility.

* **ARPA (Advanced Research Projects Agency):** Created by the US Department of Defense after WWII to ensure the US stayed ahead in technology during the Cold War.
* **The Goal:** Move away from "Centralized Computing" (one giant mainframe that, if destroyed, kills the network) to "Distributed Networking" (a mesh where if one node dies, the rest survive).
* **1969 - The First Message:** The network was called **ARPANET**. The first message was sent from UCLA to SRI (Stanford). The message was meant to be "LOGIN," but the system crashed after the first two letters, sending only "LO."
* **1983 - Standardization:** Vint Cerf and Bob Kahn created **TCP/IP**. This was the pivotal moment that allowed different types of networks to connect, technically creating the "Internet."
* **1990s - The Web:** Tim Berners-Lee invented the **World Wide Web (WWW)**, HTML, and the first browser. This put a graphical interface on top of the internet, allowing regular people to use it.

---

## 3. How Is Data Transferred?

Data transfer is the process of breaking information down into small chunks and sending it across the world.

### A. IP Address (The Home Address)
Every device connected to the internet needs a unique address so others can find it.
* **Definition:** A numerical label assigned to each device connected to a computer network.
* **Versions:**
    * **IPv4:** 32-bit address (e.g., `192.168.1.1`). We have run out of these (limit is ~4.3 billion).
    * **IPv6:** 128-bit address (e.g., `2001:0db8...`). Virtually infinite addresses to support the future.

### B. Port Numbers (The Apartment Number)
An IP address gets data to the correct *computer*, but a Port Number gets data to the correct *application* inside that computer.
* **Analogy:** IP is the building address; Port is the specific apartment number.
* **Range:** 0 to 65535.
    * **Well-Known Ports (0-1023):** Reserved for system functions (Web=80, Secure Web=443, Mail=25).
    * **Registered/Dynamic Ports:** Used by temporary applications (like a Chrome tab or a video game).

### C. Example: How WhatsApp Transmits a Message
This describes the journey of a message from "Sender" to "Receiver."

1.  **Application Layer:** You type "Hello." WhatsApp encrypts it using End-to-End Encryption (E2EE) so only the receiver can read it.
2.  **Transport Layer:** The app wraps the message in a secure tunnel (TLS) to hide metadata from hackers/ISPs. It adds Port numbers.
3.  **Network Layer:** The Operating System adds IP addresses (Source & Destination).
4.  **Data Link Layer:** The OS adds MAC addresses to talk to the local Router.
5.  **Transmission:** The Wi-Fi card turns digital bits into radio waves.
6.  **The Router:** It receives the signal, swaps your private IP for a public IP (NAT), and sends it to the ISP.
7.  **The Server:** WhatsApp's server receives the packet. It cannot read the message (E2EE), but it reads the "metadata" to know who the recipient is.
8.  **Delivery:** The server pushes the packet to the recipient's phone, where the process reverses (Decapsulation) until the text "Hello" appears.

---

## 4. Domain Name System (DNS)

The Internet works on numbers (IP Addresses), but humans work on names (Domain Names). DNS is the phonebook that bridges this gap.

* **Function:** Maps human-readable names (e.g., `google.com`) to machine-readable IP addresses (e.g., `142.250.190.46`).

### The DNS Resolution Process (Step-by-Step)
1.  **Local Cache:** You type a URL. Your computer checks if it already knows the IP from a recent visit.
2.  **Resolver:** If not found, it asks your ISP's DNS Resolver.
3.  **Root Server (.):** The ISP asks the Root Server, "Who manages `.com`?"
4.  **TLD Server (.com):** The Root sends the ISP to the Top-Level Domain server. The ISP asks, "Who manages `google`?"
5.  **Authoritative Server:** The TLD sends the ISP to Google's specific name server. This server says, "I am Google. Here is my specific IP address."
6.  **Connection:** Your computer gets the IP and connects to the website.

---

## 5. Types of Networks

Networks are categorized by how large of a physical area they cover.

* **PAN (Personal Area Network):**
    * **Range:** Very small (within arm's reach).
    * **Example:** Bluetooth connecting headphones to a phone; USB connecting a mouse.
* **LAN (Local Area Network):**
    * **Range:** Small geographic area (Room, House, Office Building).
    * **Speed:** Very high speed, low latency.
    * **Example:** Home Wi-Fi, Ethernet cables in an office.
* **CAN (Campus Area Network):**
    * **Range:** A collection of LANs within a specific location.
    * **Example:** A University campus or a Corporate headquarters spanning multiple buildings.
* **MAN (Metropolitan Area Network):**
    * **Range:** Covers a city or a large town.
    * **Example:** Cable TV networks, City-wide public Wi-Fi.
* **WAN (Wide Area Network):**
    * **Range:** No limit (Country, Continent, Globe).
    * **Characteristics:** Connects multiple LANs/MANs together. Slower than LANs.
    * **Example:** The Internet itself is the largest WAN.
* **VPN (Virtual Private Network):**
    * **Function:** A "tunnel" over the public internet. It masks your IP address and encrypts your data so you appear to be in a different location.

---

## 6. Network Topologies

Topology refers to the physical or logical layout of devices (nodes) and how they connect to one another.

### A. Bus Topology
* **Layout:** All devices connect to a single central cable called the "backbone."
* **Pro:** Cheap and easy to install for small networks.
* **Con:** If the main cable breaks, the *entire* network goes down.

### B. Ring Topology
* **Layout:** Each device connects to exactly two other devices, forming a closed circle. Data travels in one direction.
* **Pro:** Organized data flow (Token Ring).
* **Con:** If one computer or cable fails, the loop breaks, and the network fails.

### C. Star Topology
* **Layout:** All devices connect individually to a central hub or switch. This is the most common Wi-Fi/Ethernet setup today.
* **Pro:** If one cable breaks, only that one device goes offline. Easy to troubleshoot.
* **Con:** If the central switch fails, the whole network stops.

### D. Mesh Topology
* **Layout:** Devices are interconnected with many redundant connections.
    * **Full Mesh:** Every device connects to every other device.
    * **Partial Mesh:** Some devices connect to all others, some don't.
* **Pro:** Extremely reliable. If one path is blocked, data finds another way.
* **Con:** Very expensive due to cabling costs. Used for critical infrastructure (Internet backbone).

### E. Tree Topology
* **Layout:** A hierarchical "Star of Stars." A root node connects to switches, which connect to other switches or devices.
* **Usage:** Used in large office buildings (Floor switch -> Building switch -> Main Router).

### F. Hybrid Topology
* **Layout:** A combination of two or more different topologies (e.g., a Star backbone connecting multiple Bus networks).
* **Usage:** Very common in large institutions (e.g., a university might have a Star topology in labs, but buildings are connected via a Bus or Ring).
* **Pro:** Flexible and scalable.
* **Con:** Complex design and management.         

---

## 7. OSI Model

The **OSI (Open Systems Interconnection)** Model is a conceptual framework used to understand network interactions in seven layers, developed by ISO in 1984.

**Mnemonic to remember:** **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way (Physical -> Application).

### Layers (Top → Bottom: The Sender's Perspective and Bottom → Top: The Receiver's Perspective)

#### 7. Application Layer
* **Role:** The interface between the human user and the software. It generates the data.
* **Protocols:** HTTP (Web), SMTP (Email), FTP (Files).

#### 6. Presentation Layer
* **Role:** The "Translator." It ensures the data is in a usable format. It handles encryption (SSL/TLS) and compression (zipping files).
* **Functions:** Translation, Encryption, Compression.

#### 5. Session Layer
* **Role:** The "Manager." It establishes, maintains, and terminates connections between applications.
* **Functions:** Authentication, Permissions, Session Restoration (reconnecting if internet drops).

#### 4. Transport Layer
* **Role:** The "Post Office Box." It decides how much data to send and ensures it gets there.
* **Functions:** Segmentation (chopping data), Port Addressing, Error Control.
* **Key Decisions:** Reliability (TCP) vs. Speed (UDP).

#### 3. Network Layer
* **Role:** The "GPS." It determines the best physical path for data to travel across the internet.
* **Functions:** Logical Addressing (IP Addresses), Routing.
* **Data Unit:** Packets.

#### 2. Data Link Layer
* **Role:** The "Local Delivery." It handles the transfer of data between two physically connected devices (e.g., PC to Router).
* **Functions:** Physical Addressing (MAC Addresses), Error Detection.
* **Data Unit:** Frames.

#### 1. Physical Layer
* **Role:** The "Hardware." It transmits raw raw binary data over the physical medium.
* **Functions:** Converts bits (1s and 0s) into electrical signals, light pulses, or radio waves.
* **Hardware:** Cables, Hubs, Wi-Fi radios.

![Demo animation from GeeksforGeeks](OSI-Model.gif) [Read the full article on OSI Model by GeeksforGeeks here](https://www.geeksforgeeks.org/computer-networks/open-systems-interconnection-model-osi/)

---

## 8. Client-Server vs. Peer-to-Peer

### Client-Server Architecture
The standard model of the web. It is Centralized.
* **Client (Requester):** Your phone/laptop. It has limited power and asks for resources.
* **Server (Provider):** A powerful computer in a data center. It waits for requests and serves resources.
* **Request-Response Cycle:**
    1.  Client sends a request (e.g., "Get me Google.com").
    2.  Server processes logic and finds data.
    3.  Server sends a response (e.g., "Here is the HTML file").
    4.  Client renders the file.

### Peer-to-Peer (P2P) Architecture
A decentralized model.
* **Concept:** There is no central boss. Every computer (node) acts as both a Client and a Server simultaneously.
* **Usage:** BitTorrent, Blockchain.
* **Advantage:** If one node goes down, the network survives because the data is distributed.

---

## 9. Key Internet Protocols

A protocol is a set of rules. Here are the most critical ones:

### HTTP vs. HTTPS
* **HTTP (HyperText Transfer Protocol):** Sends data in plain text. Uses Port 80. Insecure (anyone on the network can read the data).
* **HTTPS (HTTP Secure):** Sends data in an encrypted tunnel (using SSL/TLS). Uses Port 443. Secure (hackers only see random code).

### IP (Internet Protocol)
* **Role:** Addressing and Routing packets across networks. It is the core of the Layer 3 Network Layer.

### TCP (Transmission Control Protocol)
* **Type:** Connection-Oriented.
* **Philosophy:** "Reliability first."
* **Mechanism:** It establishes a connection (3-way handshake), numbers every packet, and checks if they arrived. If a packet is lost, it resends it.
* **Use Cases:** Browsing the web, Email, Messaging (where accuracy matters).

### UDP (User Datagram Protocol)
* **Type:** Connectionless.
* **Philosophy:** "Speed first."
* **Mechanism:** "Fire and forget." It streams data instantly without checking if the receiver got it. No retransmission of lost packets.
* **Use Cases:** Online Gaming, Live Video Streaming, VoIP (where speed matters more than perfection).

## Appendix

- This document is based on the referenced video and the official notes linked at the top.  
- Diagrams above are ASCII for quick inclusion in text files; replace with images/SVGs for visual documentation if desired.

---



