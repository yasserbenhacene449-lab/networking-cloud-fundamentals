# learning-Networking-CCNA-
Daily hands-on lab documentation for Linux System Administration, Cloud Security, and Cisco CCNA networking fundamentals, tailored for corporate IT environments.
---

## 🌐 Week 1: Networking & CCNA Core (Jeremy's IT Lab)

### 🎥 Day 1: Network Devices (CCNA 200-301)
*   **Concepts Learned:** Understanding the foundational roles of network nodes and how enterprise infrastructures are built to share resources securely.
*   **Core Components Mastered:**
    *   **Clients & Servers:** Understood the client-server relationship where clients request services (like web browsers or smartphones) and servers fulfill them (like dedicated hardware or applications providing data).
    *   **Switches:** Mastered the role of Enterprise-grade Switches (e.g., Cisco Catalyst) which provide high-density port connectivity (typically 24+ ports) to aggregate and forward traffic locally within the same **LAN (Local Area Network)**.
    *   **Routers:** Learned that routers (e.g., Cisco ISR) have fewer interfaces than switches and are strictly designed to provide connectivity *between* different networks, enabling data forwarding across the Internet.
    *   **Firewalls:** Explored dedicated network security devices that control traffic entering and exiting the network based on security rules. Differentiated between hardware-based **Network Firewalls** and software-based **Host-based Firewalls**.
    *   **Next-Generation Firewalls (NGFW):** Understood how modern appliances (like Cisco Firepower or modern ASAs) upgrade traditional filtering by adding advanced features like **IPS (Intrusion Prevention Systems)**.

### 📝 Day 1 Quiz Results: Skills Assessment
*   **Status:** Successfully Passed ✅
*   **Key Validated Skills:**
    *   Correctly identified the **Switch** as the appropriate device for high-density local endpoint connectivity (e.g., connecting 30 departmental PCs).
    *   Validated the functional difference between an end-host acting as a server vs. a client in peer-to-peer (P2P) transactions (e.g., AirDrop).
 
    *   
    *   Demonstrated understanding of a **Router's** primary core competency in interconnecting separate networks over a Firewall or Switch.
    *   Distinguished **Next-Generation Firewalls (NGFW)** from traditional and host-based firewalls by identifying their advanced threat filtering capabilities.

<img width="1920" height="1080" alt="Screenshot 2026-06-21 211224" src="https://github.com/user-attachments/assets/32fb9f0f-89a4-447e-bf74-20c84f52ed19" />

---
---

### 🌐 Day 2: Network Interfaces, Cabling Standards & Practical Topology
*   **Concepts Learned:** Deep dive into Physical Layer components, Ethernet cabling standards (UTP vs. Fiber), and understanding interface pinouts crucial for production environments.
*   **Core Knowledge Mastered:**
    *   **Copper (UTP) vs. Fiber Optic:** Understood that UTP cables are legally limited to a maximum length of **100 meters** and are susceptible to Electromagnetic Interference (EMI).
    *   **Fiber Varieties (SMF vs. MMF):** Mastered the core differences between Single-mode Fiber (narrow core, laser-driven, long distances up to kilometers) and Multi-mode Fiber (wider core, LED-driven, cost-effective for shorter building-to-building distances).
    *   **Pinouts & Auto MDI-X:** Learned that End-hosts, Routers, and Firewalls transmit on pins 1,2 and receive on 3,6, while Switches do the exact opposite. Modern networks leverage **Auto MDI-X** to automatically negotiate these connections.
*   **Practical Lab Application (Cisco Packet Tracer):** 
    *   Successfully simulated a multi-device enterprise network architecture consisting of PCs, Switches, Routers, and Firewalls.
    *   Resolved physical hardware constraints in the lab by understanding device interface exhaustion and properly mapping physical cable connections between Firewalls and Core Routers.

> [!NOTE]
> Physical interfaces on enterprise devices (Routers and Firewalls) are shut down by default for security, requiring active administration (`no shutdown` command) to bring the links up.
> <img width="1930" height="1167" alt="Screenshot 2026-06-22 172345" src="https://github.com/user-attachments/assets/e7a248ad-5ce7-47ae-b18d-b3c48c26f95e" />
<img width="1920" height="1080" alt="Screenshot 2026-06-22 172310" src="https://github.com/user-attachments/assets/65bdef0f-9e17-40be-a978-4292241f74e4" />
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/c51b6a23-8083-4ffb-a69d-d7490b1d1616" />
# Core Networking Essentials: The TCP/IP Model

This document serves as a technical reference for foundational networking concepts required for **System Administration** and **Cloud Engineering**. It focuses on understanding how data moves through a network without diving into vendor-specific hardware configurations.

---
<img width="1920" height="1080" alt="Screenshot 2026-07-01 145219" src="https://github.com/user-attachments/assets/f4bc67d9-ae86-42c2-a7b7-f2a4ce1e1593" />


## 🔑 Key Concepts

### 1. Protocols & Standards
* **Protocol:** A set of rules or "languages" that computers use to communicate with each other over a network.
* **Standard:** An agreed-upon, vendor-neutral specification (such as those defined by the IETF or IEEE) ensuring that devices from different manufacturers (e.g., Linux servers, Windows PCs, Macs) can seamlessly exchange data.

### 2. The 5-Layer TCP/IP Model

| Layer | Name | Core Function | Protocol Data Unit (PDU) | Key Examples |
| :--- | :--- | :--- | :--- | :--- |
| **Layer 5** | **Application** | Enables user-facing software applications to format and interpret data. | Data | HTTP, HTTPS, DNS, SSH |
| **Layer 4** | **Transport** | Manages end-to-end communication between specific application processes using **Port Numbers**. | **Segment** (TCP) / **Datagram** (UDP) | TCP, UDP |
| **Layer 3** | **Network / Internet** | Handles end-to-end delivery of data between hosts across multiple networks using **IP Addresses**. | **Packet** | IPv4, IPv6, ICMP |
| **Layer 2** | **Data Link / Local Network** | Manages hop-to-hop delivery of data within the same local area network (LAN) using **MAC Addresses**. | **Frame** | Ethernet, Wi-Fi |
| **Layer 1** | **Physical** | Transmits raw bits as electrical, optical, or radio signals over physical media. | Bits | Cables, Fiber, NICs |

---

## 🔄 Data Encapsulation & Decapsulation

Understanding how data is wrapped and unwrapped is essential for troubleshooting firewalls, routing, and cloud security groups.

### Encapsulation (Sending Data)
As data travels down the network stack from the **Application Layer** to the **Physical Layer**, each layer adds a **Header** (and sometimes a Trailer) containing control information:
1. **Application Data** is passed to Layer 4.
2. Layer 4 adds port numbers, creating a **Segment**.
3. Layer 3 adds source and destination IP addresses, creating a **Packet**.
4. Layer 2 adds source and destination MAC addresses along with error-checking codes, creating a **Frame**.
5. Layer 1 converts the frame into raw signals to cross the physical medium.

### Decapsulation (Receiving Data)
The receiving host processes this in reverse. It strips away the headers layer-by-layer, verifying the control information (MACs, IPs, and Ports) until the raw application data safely reaches the intended program.

---

## 💡 System & Cloud Architecture Takeaways

* **Port Numbers (Layer 4):** Act like "apartment numbers" inside a server host. For cloud security groups and firewalls, knowing ports is critical (e.g., **Port 22** for SSH, **Port 80/443** for Web Services).
* **IP Addressing (Layer 3):** The global address of the host machine. This forms the absolute baseline for setting up Virtual Private Clouds (VPCs) and subnets in cloud environments.
* **Payload:** The actual data carried within a specific PDU layer, excluding that layer's own header or trailer.
* <img width="1920" height="1080" alt="Screenshot 2026-07-01 121035" src="https://github.com/user-attachments/assets/09e24388-045b-4b02-8bbc-688d26faf189" />
<img width="1920" height="1080" alt="Screenshot 2026-07-01 121154" src="https://github.com/user-attachments/assets/f1151009-5f55-4c89-a405-fe4719564d08" />
🌐 Computer Networking Basics & IPv4 AddressingWelcome to my documentation repository! This repository serves as a personal log of my journey learning Networking Fundamentals as part of my preparation for the CCNA 200-301 certification, while building a rock-solid foundation for Linux System Administration and Cloud Computing.Inside, you will find organized summaries, practical examples, and interactive applications of the concepts I have studied and mastered.📌 Table of ContentsIPv4 Address StructureSubnet Mask Concept & The Dividing LineReserved Addresses & Host RangeKey Networking Concepts & TroubleshootingConnecting Concepts to Cloud Computing1. IPv4 Address StructureAn IPv4 address is composed of 32 bits divided into four sections separated by dots. Each section is called an octet because it consists of 8 bits:$$32 \text{ Bits} = 4 \text{ Octets} \times 8 \text{ Bits}$$IP Address Example: 192.168.1.50Computers understand this address in Binary format (as $0$s and $1$s), whereas humans write it in Decimal format to make it easier to read, configure, and memorize.2. Subnet Mask Concept & The Dividing LineBy itself, a computer cannot distinguish which part of an IP address represents the "local network" and which part represents the "individual device". This is where the Subnet Mask comes in, acting as the Dividing Line:CIDR NotationSubnet Mask EquivalentNetwork ID PortionHost ID Portion/8255.0.0.01st octet onlyRemaining 3 octets/16255.255.0.0First 2 octetsRemaining 2 octets/24255.255.255.0First 3 octetsLast octet only🔍 Illustrative Examples:With the address 192.168.1.50/24:Network ID: 192.168.1.0Host ID: 50With the address 172.16.5.10/16:Network ID: 172.16.0.0Host ID: 5.10With the address 10.20.30.40/8:Network ID: 10.0.0.0Host ID: 20.30.403. Reserved Addresses & Host RangeWithin any given network, there are always two addresses reserved for system operations that cannot be assigned to any individual host (computer, server, etc.):Network ID: The very first address in the network (where all host bits are $0$s), representing the identity of the network itself.Broadcast Address: The very last address in the network (where all host bits are $1$s/255), used to send data packets to all devices on the network simultaneously.📝 Practical Case Study:Question: Can you assign the IP address 192.168.5.0 to a computer in a network defined by the range 192.168.5.0/24?Answer: No, absolutely not.Reason: Because the /24 mask designates the first three octets (192.168.5) as the network portion. Therefore, the address ending in .0 represents the Network ID itself, which is strictly reserved.📊 Calculating the Usable Host Range:For the network 192.168.5.0/24:Network ID (Reserved): 192.168.5.0First Usable Host IP: 192.168.5.1Last Usable Host IP: 192.168.5.254Broadcast Address (Reserved): 192.168.5.255Usable Range:$$\text{From } 192.168.5.1 \text{ to } 192.168.5.254$$4. Key Networking Concepts & TroubleshootingIP Address Conflict:This issue occurs when two active devices on the same local network are manually configured with the exact same IP address. It leads to packet loss and connection drops for both devices, as switches and routers struggle to direct traffic to the correct destination.Default Gateway:This is the IP address of the router interface connected to the local network. Without configuring a default gateway on your device, it will be isolated locally. It can still communicate with neighboring devices on the same subnet but will fail to reach external networks (like the Internet).5. Connecting Concepts to Cloud ComputingWhen working on cloud platforms such as AWS, Azure, and Google Cloud:Virtual networks are designed using VPC (Virtual Private Cloud) and further segmented into Subnets based on CIDR blocks (e.g., allocating a /16 block for the entire VPC, then carving out /24 subnets for individual server tiers).AWS Subnet Reservation Rule: In every subnet, AWS reserves 5 IP addresses automatically (the Network IP, the VPC Router/Gateway, the DNS server, a reserved IP for future use, and the Network Broadcast IP). This means a /24 subnet on AWS actually yields only 251 usable IPs instead of the standard 254.🛠️ Hands-on Tools Used:Cisco Packet Tracer: For designing, simulating, and configuring virtual network architectures.Linux Command Line: Using commands like ip a, ifconfig, and ping to test network connectivity and manage network interfaces.📝 This documentation is actively maintained and updated as I progress further into CCNA, Linux administration, and cloud architecture.


