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
# 🌐 Computer Networking Basics & IPv4 Addressing

Welcome to my documentation repository! This repository serves as a personal log of my journey learning **Networking Fundamentals** as part of my preparation for the **CCNA 200-301** certification, while building a rock-solid foundation for **Linux System Administration** and **Cloud Computing**.

Inside, you will find organized summaries, practical examples, and interactive applications of the concepts I have studied and mastered.

---

## 📌 Table of Contents
1. [IPv4 Address Structure](#1-ipv4-address-structure)
2. [Subnet Mask Concept & The Dividing Line](#2-subnet-mask-concept--the-dividing-line)
3. [Reserved Addresses & Host Range](#3-reserved-addresses--host-range)
4. [Key Networking Concepts & Troubleshooting](#4-key-networking-concepts--troubleshooting)
5. [Connecting Concepts to Cloud Computing](#5-connecting-concepts-to-cloud-computing)
6. [Basic Cisco IOS Interface Configuration](#6-basic-cisco-ios-interface-configuration)

---

## 1. IPv4 Address Structure
An **IPv4** address is composed of **32 bits** divided into four sections separated by dots. Each section is called an **octet** because it consists of 8 bits:

$$
32 \text{ Bits} = 4 \text{ Octets} \times 8 \text{ Bits}
$$

* **IP Address Example:** `192.168.1.50`
* Computers understand this address in **Binary** format (as $0$s and $1$s), whereas humans write it in **Decimal** format to make it easier to read, configure, and memorize.

---

## 2. Subnet Mask Concept & The Dividing Line
By itself, a computer cannot distinguish which part of an IP address represents the "local network" and which part represents the "individual device". This is where the **Subnet Mask** comes in, acting as the **Dividing Line**:

| CIDR Notation | Subnet Mask Equivalent | Network ID Portion | Host ID Portion |
| :--- | :--- | :--- | :--- |
| **`/8`** | `255.0.0.0` | 1st octet only | Remaining 3 octets |
| **`/16`** | `255.255.0.0` | First 2 octets | Remaining 2 octets |
| **`/24`** | `255.255.255.0` | First 3 octets | Last octet only |

### 🔍 Illustrative Examples:
1. **With the address `192.168.1.50/24`:**
   * **Network ID:** `192.168.1.0`
   * **Host ID:** `50`
2. **With the address `172.16.5.10/16`:**
   * **Network ID:** `172.16.0.0`
   * **Host ID:** `5.10`
3. **With the address `10.20.30.40/8`:**
   * **Network ID:** `10.0.0.0`
   * **Host ID:** `20.30.40`

---

## 3. Reserved Addresses & Host Range
Within any given network, there are always two addresses reserved for system operations that **cannot** be assigned to any individual host (computer, server, etc.):

1. **Network ID:** The very first address in the network (where all host bits are $0$s), representing the identity of the network itself.
2. **Broadcast Address:** The very last address in the network (where all host bits are $1$s/255), used to send data packets to all devices on the network simultaneously.

### 📝 Practical Case Study:
**Question:** Can you assign the IP address `192.168.5.0` to a computer in a network defined by the range `192.168.5.0/24`?
* **Answer:** **No, absolutely not.**
* **Reason:** Because the `/24` mask designates the first three octets (`192.168.5`) as the network portion. Therefore, the address ending in `.0` represents the **Network ID** itself, which is strictly reserved.

### 📊 Calculating the Usable Host Range:
For the network `192.168.5.0/24`:
* **Network ID (Reserved):** `192.168.5.0`
* **First Usable Host IP:** `192.168.5.1`
* **Last Usable Host IP:** `192.168.5.254`
* **Broadcast Address (Reserved):** `192.168.5.255`
* **Usable Range:**
  $$
  \text{From } 192.168.5.1 \text{ to } 192.168.5.254
  $$

---

## 4. Key Networking Concepts & Troubleshooting

* **IP Address Conflict:**
  This issue occurs when two active devices on the same local network are manually configured with the exact same IP address. It leads to packet loss and connection drops for both devices, as switches and routers struggle to direct traffic to the correct destination.

* **Default Gateway:**
  This is the IP
# 🌐 Level 2: IP Addressing & Subnetting - Study Notes & Labs

Welcome to my documentation for **Level 2: IP Addressing & Subnetting**. This repository serves as a technical reference and log of my progress as I master networking fundamentals tailored for **System Administration** and **Cloud Engineering**.

---

## 📑 Table of Contents
1. [Lesson 2.1: IPv4 Structure & Binary Conversion](#-lesson-21-ipv4-structure--binary-conversion)
2. [Lesson 2.2: Subnet Mask & CIDR Notation](#-lesson-22-subnet-mask--cidr-notation)
3. [Lesson 2.3 & 2.4: Network ID, Broadcast IP & Usable Hosts](#-lesson-23--24-network-id-broadcast-ip--usable-hosts)
4. [Lesson 2.5: Introduction to IPv6](#-lesson-25-introduction-to-ipv6)

---

## 🎯 Lesson 2.1: IPv4 Structure & Binary Conversion
* **Concept:** IPv4 addresses consist of **32 bits**, divided into 4 octets (8 bits each).
* **SysAdmin Relevance:** Understanding how systems read IPs in binary to debug network logs and troubleshoot connectivity.
* **Practice Lab:** * Convert Decimal `10` to Binary using the bit-weight scale (`128 64 32 16 8 4 2 1`).
  * **Result:** `00001010` (Bits 8 and 2 are active).

---

## 🎯 Lesson 2.2: Subnet Mask & CIDR Notation
* **Concept:** CIDR (Classless Inter-Domain Routing) defines how many bits are locked for the Network ID.
* **Cloud Relevance:** Vital for defining VPC CIDR blocks (e.g., `/16` for large infrastructures or `/24` for standard subnets).
* **Key Takeaway:**
  * `/24` = First 3 octets are fixed (`255.255.255.0`).
  * `/16` = First 2 octets are fixed (`255.255.0.0`).
  * `/32` = Points to a single specific host (Crucial for tight Firewall/Security Group rules).

---

## 🎯 Lesson 2.3 & 2.4: Network ID, Broadcast IP & Usable Hosts
* **Concept:** Every subnet has reserved administrative boundaries that cannot be assigned to individual servers.
* **Cloud Specific Rule (AWS/GCP):** Unlike traditional networking which reserves 2 addresses, Cloud providers reserve **5 IP addresses** per subnet for internal routing, DNS, and management.
* **Lab Scenario Accomplished:**
  * Given Subnet: `10.0.5.64/26` (Range: .64 to .127)
  * **Network ID:** `10.0.5.64`
  * **Broadcast IP:** `10.0.5.127`
  * **First Usable Cloud IP:** `10.0.5.65` (Traditional) or `10.0.5.68` (AWS specific after reserving 5 IPs).

---

## 🎯 Lesson 2.5: Introduction to IPv6
* **Concept:** A **128-bit** address space written in Hexadecimal to solve IPv4 exhaustion.
* **Cloud Relevance:** Modern cloud architectures use IPv6 for direct Internet-facing servers without the need for complex and expensive NAT Gateways.
* **Key Feature:** IPv6 eliminates Broadcast entirely, optimizing network traffic via Multicast.

---

### 🚀 Next Step
Moving forward to **Level 3**, focusing on upper layers: **TCP/UDP Protocols, Ports management (SSH, HTTP), and essential services like DNS & DHCP.**
<img width="1920" height="1080" alt="Screenshot 2026-07-06 180315" src="https://github.com/user-attachments/assets/d8f0333b-203c-4946-956c-0afc4b651690" />
<img width="1920" height="1080" alt="Screenshot 2026-07-06 180226" src="https://github.com/user-attachments/assets/c95f907b-3c05-4cc9-970d-cc2caeabed98" />
