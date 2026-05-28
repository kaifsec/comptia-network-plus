# Domain 1: Networking Concepts

## Introduction to the OSI Model

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

## Network Devices

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

## Networking Functions

These are core services and mechanisms used to optimize, secure, and control how data flows across a network.

### Key Concepts to Know:

* **CDN (Content Delivery Network):** Caches website data on servers all over the world. It brings data geographically closer to the user so websites load faster.
* **VPN (Virtual Private Network):** Creates an encrypted tunnel over the public internet to protect data privacy.
* **QoS (Quality of Service):** Prioritizes certain types of network traffic over others. (For example, making sure voice calls stay clear even if someone else is downloading a massive file).
* **TTL (Time to Live) & Routing Loops:** A mechanism that prevents data packets from circulating infinitely in a loop between routers if a route misconfiguration occurs.

### How to Check TTL (Command Line Basics):
A router can accidentally send a packet back and forth to another router forever (a **Routing Loop**). To stop this, every packet starts with a **TTL number** (like 64 or 128). Every time the packet passes through a router, that number drops by 1. If it hits 0, the packet drops dead.

Following commands can be used to test and see this behavior live in the command prompt:
1. `ping [IP or Website]` -> It shows you the remaining TTL of the packet when it returns to you.
2. `traceroute [IP or Website]` -> It Intentionally uses increasing TTL values (starting at 1) to force each router along the path to drop the packet and report back, mapping the exact path to a destination. If there is a routing loop, you will see the same two IP addresses bouncing back and forth over and over.

## Designing the Cloud

Cloud computing shifts networking from physical hardware to virtualized, software-defined environments that can be deployed instantly.

### Core Cloud Characteristics
* **One-Click Deployment:** Infrastructure can be spun up or torn down in seconds using cloud consoles or automation scripts.
* **Elasticity:** The network can automatically grow or shrink its resources based on real-time demand (e.g., handling a sudden spike in website traffic).
* **Scalability:** The long-term capacity of the network can easily scale up to handle massive, permanent growth without needing to buy new physical servers.
* **Multi-Tenancy:** Multiple different customers (tenants) share the same underlying physical server hardware, but their data is completely isolated from one another.

### Cloud Isolation and Connectivity
* **VPC (Virtual Private Cloud):** A private, isolated network section created inside a public cloud provider (like AWS). It acts like your own virtual data center.
* **vNF (Virtual Network Function):** Running traditional network services (like routers, firewalls, or load balancers) as virtual software machines instead of physical hardware appliances.
* **Transit Gateway:** A cloud router used to easily interconnect multiple VPCs and on-premise networks together through a single central hub.

### Cloud Gateways and Security
* **VPN Gateway:** Securely connects your physical on-premise office or home computer to your cloud VPC over an encrypted internet tunnel.
* **NAT Gateway:** Allows private devices inside a VPC to connect out to the internet (for updates, etc.) while completely blocking the internet from initiating a connection back into them.
* **VPC Endpoint:** Allows devices inside your private VPC to securely connect to other cloud provider services without their data ever leaving the private cloud network.
* **Network Security Group:** A virtual firewall that controls traffic at the **instance/host level** (like a single virtual server).
* **Network Security List (NACL):** A virtual firewall that controls traffic at the **subnet level** (protecting a whole group of virtual servers).

## Cloud Models

Cloud computing is categorized by how it is deployed and what level of management the cloud provider handles versus what you handle.

### Cloud Deployment Models
* **Public Cloud:** Infrastructure owned and operated by a third-party provider (like AWS, Microsoft Azure, or Google Cloud) and shared with multiple organizations over the public internet.
* **Private Cloud:** Virtualized infrastructure built exclusively for a single organization. It can be hosted in their own physical data center or by a third party.
* **Hybrid Cloud:** A mix of both public and private clouds, allowing data and applications to be shared between them.

### Cloud Service Models (SaaS, PaaS, IaaS)
* **IaaS (Infrastructure as a Service):** You rent the basic building blocks like virtual servers, storage, and networking hardware. You are responsible for installing the operating system, security, and data. (Example: AWS EC2, Azure VMs).
* **PaaS (Platform as a Service):** The provider handles the hardware and the operating system. They give you a platform to deploy your code without worrying about server management. (Example: Heroku, AWS Elastic Beanstalk).
* **SaaS (Software as a Service):** A complete, fully managed software application that you access over the internet. You only manage your user settings. (Example: Microsoft 365, Gmail).

### Shared Responsibility Matrix
When you move to the cloud, security is a partnership. The Shared Responsibility Matrix dictates who is responsible for what based on the service model you use:

* **Provider Responsibility:** Usually responsible for the physical security of the data centers, hardware, virtualization layer, and global infrastructure ("Security **of** the cloud").
* **Customer Responsibility:** You are always responsible for your own data, user accounts, permissions, and passwords ("Security **in** the cloud").
* **The Rule:** The more "as a Service" you go (moving from IaaS -> PaaS -> SaaS), the *more* responsibility shifts to the provider, and the *less* you have to manage yourself.

## Introduction to IP and Transport Protocols

Data moving across a network acts like a series of moving vans. The network infrastructure provides the roads, the Internet Protocol (IP) acts as the delivery truck, and the boxes inside hold the data packets.

### Data Encapsulation
* Data is wrapped inside layers like Russian nesting dolls (Data goes inside TCP/UDP, which goes inside IP, which goes inside an Ethernet frame).

### TCP vs. UDP (Layer 4 Protocols)
* **TCP (Transmission Control Protocol):** Connection-oriented. It requires a formal handshake to set up and close connections. It guarantees reliable delivery by recovering from data errors and managing data flow control.
* **UDP (User Datagram Protocol):** Connectionless. It drops data onto the network without checking if the receiver is ready. It provides fast, "unreliable" delivery with no error recovery or flow control.


### Ports and Sockets
* **IP Address:** Like a house address. It gets the delivery truck to the correct computer system.
* **Port Number:** Like a specific room name inside the house. It tells the system exactly which application or service should receive the data box.
* **Sockets:** The complete communication path, consisting of an IP address, a protocol (TCP or UDP), and a port number (e.g., `10.0.0.1 : TCP : 80`).

### Port Ranges (0 to 65,535)
* **Non-Ephemeral Ports:** Permanent port numbers assigned to standard server applications (Ports 0 through 1,023). 
  * *Examples:* Web servers (`TCP 80`), Email servers (`TCP 143`).
* **Ephemeral Ports:** Temporary port numbers automatically assigned on-the-fly by the client's computer to track a specific conversation (Ports 1,024 through 65,535).

## Common Ports

Ports are like virtual doors that let specific types of network traffic enter or leave a device. 

### Web and Remote Access Ports
* **SSH (Secure Shell) -> TCP 22:** Encrypted remote console access. Used to securely manage routers and servers from a distance.
* **Telnet -> TCP 23:** Insecure, unencrypted remote console access. In cybersecurity, we avoid this because everything is sent in plain text.
* **HTTP (Hypertext Transfer Protocol) -> TCP 80:** Insecure web browsing.
* **HTTPS (HTTP Secure) -> TCP 443:** Secure, encrypted web browsing.
* **RDP (Remote Desktop Protocol) -> TCP 3389:** Graphical remote access. Let's you view and control a virtual or remote desktop screen.

### File and Media Transfer Ports
* **FTP (File Transfer Protocol) -> TCP 20/21:** Insecure file transfer. Uses port 21 for control commands and port 20 for the actual data.
* **SFTP (SSH File Transfer Protocol) -> TCP 22:** Uses SSH to transfer files securely over a single port.
* **TFTP (Trivial File Transfer Protocol) -> UDP 69:** A very basic, simple file transfer protocol with no authentication. Uses UDP because it's fast.
* **SMB (Server Message Block) -> TCP 445:** Used by Windows networks for sharing files and printers locally.

### Infrastructure and Management Ports
* **DNS (Domain Name System) -> UDP/TCP 53:** Converts website names (like google.com) into IP addresses. Uses UDP for quick queries, and TCP for heavy transfers.
* **DHCP (Dynamic Host Configuration Protocol) -> UDP 67/68:** Automatically assigns IP addresses, subnet masks, and gateways to devices when they connect to the network.
* **SNMP (Simple Network Management Protocol) -> UDP 161/162:** Used by network engineers to gather metrics and monitor the health of routers, switches, and servers.

### Email Ports
* **SMTP -> TCP 25:** Used to *send* mail from a client to a server. (Insecure/Plain text).
* **Secure SMTP (SMTPS) -> TCP 465:** Uses TLS to *send* email securely with encryption.
* **POP3 -> TCP 110:** Downloads emails to a single device and deletes them from the server. (Insecure/Plain text).
* **Secure POP3 -> TCP 995:** Uses TLS to download emails securely.
* **IMAP -> TCP 143:** Syncs emails across multiple devices while keeping them on the server. (Insecure/Plain text).
* **Secure IMAP -> TCP 993:** Uses TLS to sync emails across devices securely.
