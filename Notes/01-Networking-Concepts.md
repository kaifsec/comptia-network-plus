# Domain 1: Networking Concepts


## Video: Introduction to the OSI Model

The OSI model is a 7-layer framework that handles how data moves across a network. It is used to troubleshoot network issues.

### My Core Takeaways:
* It is a conceptual framework, not a physical thing.
* Layer 7 (Application) is closest to the user (like a web browser).

### The 7 Layers Mnemonic (Bottom to Top):
* **P**lease -> Layer 1: Physical (Cables, Hubs)
* **D**o -> Layer 2: Data Link (Switches)
* **N**ot -> Layer 3: Network (Routers, IP addresses)
* **T**hrow -> Layer 4: Transport (TCP/UDP)
* **S**ausage -> Layer 5: Session (Control protocols)
* **P**izza -> Layer 6: Presentation (Encryption)
* **A**way -> Layer 7: Application (HTTP, Browsers)


## Video: Network Devices

These are the core hardware components used to connect devices and secure data across a network.

### Key Devices and Their Functions:

* **Router:** Connects different networks together. It routes data packets based on IP addresses (Layer 3).

* **Switch:** Connects devices within the same network. It forwards data frames based on MAC addresses (Layer 2).

* **Firewall:** Filters network traffic based on security rules. It blocks malicious traffic from entering your network.

* **IDS / IPS:** Intrusion Detection (IDS) monitors and alerts you of threats. Intrusion Prevention (IPS) actively blocks those threats.

* **Load Balancer:** Distributes incoming network traffic evenly across multiple servers so no single server gets overwhelmed.

* **NAS / SAN:** Network Attached Storage (NAS) is a file storage device connected to the network. Storage Area Network (SAN) is a dedicated high-speed network for block-level storage.

* **Access Point:** Allows wireless devices (like phones or laptops) to connect to a wired network using Wi-Fi.

* **Wireless LAN Controller:** A centralized device used by network administrators to manage multiple Wireless Access Points easily.


## Video: Networking Functions

These are core services and mechanisms used to optimize, secure, and control how data flows across a network.

### Key Concepts to Know:

* **CDN (Content Delivery Network):** Caches website data on servers all over the world. It brings data geographically closer to the user so websites load faster.
* **VPN (Virtual Private Network):** Creates an encrypted tunnel over the public internet to protect data privacy.
* **QoS (Quality of Service):** Prioritizes certain types of network traffic over others. (For example, making sure voice calls stay clear even if someone else is downloading a massive file).
* **TTL (Time to Live) & Routing Loops:** A mechanism that prevents data packets from circulating infinitely in a loop between routers if a route misconfiguration occurs.

### How to Check TTL (Command Line Basics):
A router can accidentally send a packet back and forth to another router forever (a **Routing Loop**). To stop this, every packet starts with a **TTL number** (like 64 or 128). Every time the packet passes through a router, that number drops by 1. If it hits 0, the packet drops dead.

Following commands can be used to test and see this behavior live in your command prompt:
1. `ping [IP or Website]` -> It shows you the remaining TTL of the packet when it returns to you.
2. `traceroute [IP or Website]` -> It intentionally uses increasing TTL values (starting at 1) to force each router along the path to drop the packet and report back, mapping the exact path to a destination. If there is a routing loop, you will see the same two IP addresses bouncing back and forth over and over.

