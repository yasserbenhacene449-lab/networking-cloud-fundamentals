# 🌐 Week 2: Linux Networking & Routing Command Reference (`iproute2`)

## 📌 Module Overview
This module documents essential Linux networking commands and practical execution workflows for inspecting physical interfaces, assigning IP addresses, managing static routing tables, and verifying kernel packet configurations.

---

## 🛠️ Summary of Essential Networking Commands & Execution

### 1. Network Interfaces & Link Management (`ip link`)
Displays all available network interfaces and verifies their physical link operational states (`UP`/`DOWN`).
* **Command:** `ip link`

![ip link output](images/ip-link.png)

> **Key Observation:** The primary active interface is identified as `eth0` in `UP` state[cite: 12].

---

### 2. IP Address Verification (`ip addr`)
Shows IPv4 and IPv6 addresses along with subnet parameters bound to each specific network device[cite: 13].
* **Command:** `ip addr`

![ip addr output](images/ip-addr.png)

> **Key Observation:** Interface `eth0` is assigned the IPv4 address `10.244.23.161/32`[cite: 13].

---

### 3. Routing Table Management (`ip route`)
Examines the current kernel routing table and default gateway configurations to direct outbound traffic[cite: 11].
* **Command:** `ip route`

![ip route output](images/ip-route.png)

> **Key Observation:** Non-local network traffic is routed through default gateway `169.254.1.1` via device `eth0`[cite: 11].

---

### 4. Core Network Command Checklist
* **`ip link`**: Inspects interface link statuses.
* **`ip addr`**: Views assigned IP configurations.
* **`ip addr add <IP>/<CIDR> dev <interface>`**: Assigns static IP addresses directly to a device.
* **`ip route`**: Views active routing pathways and gateways.
* **`ip route add <destination> via <gateway>`**: Adds static routing rules for remote subnets.
* **`cat /proc/sys/net/ipv4/ip_forward`**: Checks kernel packe
