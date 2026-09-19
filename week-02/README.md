
## 📌 Module Overview
This module expands on core enterprise networking architecture, focusing on **Layer 3 Routing (Static & Dynamic)**, **Variable Length Subnet Masking (VLSM)**, and essential infrastructure operational services (**DHCP** & **DNS**). 

These competencies represent crucial building blocks for managing scalable network enterprise deployments, local data centers, and Cloud Virtual Private Clouds (VPCs).

---

## 📅 Daily Execution & Technical Concepts

### 🛣️ Day 1 & 2: IP Routing Fundamentals & Static Routing
* **Understanding Routing:** The process by which Layer 3 boundary devices (Routers) forward packets across disparate logical networks using internal **Routing Tables**.
* **Routing Table Decision Criteria:**
  1. **Longest Prefix Match:** The interface matching the highest number of continuous prefix bits `/24` over `/16` takes precedence.
  2. **Administrative Distance (AD):** The trustworthiness rating of a route source (e.g., Directly Connected = `0`, Static Route = `1`, OSPF = `110`).
  3. **Metric:** The cost associated with reaching a destination network.
* **Static vs. Dynamic Routing:**
  * **Static Routing:** Manually configured routes (`ip route <network> <mask> <next-hop>`). Ideal for small networks or default gateway routes (`0.0.0.0/0`). Highly secure and CPU-efficient.
  * **Dynamic Routing:** Automated route discovery using protocols like **OSPF (Open Shortest Path First)** or **BGP (Border Gateway Protocol)**. Handles topology changes dynamically.

#### 🧪 Cisco Packet Tracer Lab: Static Route Implementation
* Configured point-to-point static routes between dual edge routers connecting internal host subnets.
* Verified connectivity using `ping` and path trace diagnostics via `traceroute`.

---

### 🧮 Day 3: Advanced Subnetting & VLSM (Variable Length Subnet Masking)
* **Variable Length Subnet Masking (VLSM):** The efficiency technique of allocating custom subnet sizes (masks) tailored to specific host density requirements rather than fixed classful networks.
* **Subnetting Calculation Formula:**

$$\text{Usable Hosts} = 2^{H} - 2$$

*(Where $H$ is the number of remaining Host Bits).*

#### 📊 VLSM Allocation Practical Example (`192.168.1.0/24`)
Given a classless address pool of `192.168.1.0/24`:
* **Department A (50 Hosts Needed):** Requires `/26` mask ($2^6 - 2 = 62$ hosts).
  * *Subnet Range:* `192.168.1.0/26` (`192.168.1.1` - `192.168.1.62`).
* **Department B (20 Hosts Needed):** Requires `/27` mask ($2^5 - 2 = 30$ hosts).
  * *Subnet Range:* `192.168.1.64/27` (`192.168.1.65` - `192.168.1.94`).
* **Point-to-Point Router Link (2 Hosts Needed):** Requires `/30` mask ($2^2 - 2 = 2$ hosts).
  * *Subnet Range:* `192.168.1.96/30` (`192.168.1.97` - `192.168.1.98`).

---

### 🔄 Day 4 & 5: Dynamic Host Configuration Protocol (DHCP) & Relay
* **DHCP Operational Flow (DORA Process):**
  1. **Discover:** Client broadcasts request for an IP (`0.0.0.0:68` ➔ `255.255.255.255:67`).
  2. **Offer:** Server offers an available IP lease with network parameters.
  3. **Request:** Client accepts the offered IP.
  4. **Acknowledge (ACK):** Server confirms the binding lease.
 
     <img width="740" height="352" alt="Capture d’écran 2026-09-19 172112" src="https://github.com/user-attachments/assets/9b39705a-13c0-4706-b2f2-b5b45268a401" />
<img width="726" height="215" alt="Capture d’écran 2026-09-19 171943" src="https://github.com/user-attachments/assets/c0f10794-47fb-4db6-a3e0-456df2d87b78" />
<img width="731" height="146" alt="Capture d’écran 2026-09-19 171859" src="https://github.com/user-attachments/assets/83311235-45b9-4ca0-b43c-de4e821f49fa" />
