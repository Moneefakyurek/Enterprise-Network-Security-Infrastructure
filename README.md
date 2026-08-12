# Enterprise Hybrid Network & Security Infrastructure Simulation

## 📌 Project Overview
Designed and deployed a highly available, multi-branch Enterprise Network topology using **Cisco Packet Tracer**. The project simulates a complete corporate environment including a Headquarters (HQ), two regional Branch offices, centralized core services, dynamic routing, and perimeter firewall security.

---

## 📐 Architecture & Components

### **Headquarters (HQ)**
* **Core Switch:** Cisco Catalyst 3560 (Layer 3 Switch) handling Inter-VLAN Routing.
* **HQ Edge Router:** Cisco 2911 Router.
* **Perimeter Security:** Cisco ASA 5505 Firewall connected to Cloud (ISP Simulation) via PAT/NAT Overload.
* **Central Server (Server50):** Hosting DHCP Relay services & DNS for the entire enterprise.

### **Branch Offices (Branch 1 & Branch 2)**
* Connected to HQ via dedicated WAN links (`10.0.0.0/30` and `10.0.0.4/30`).
* Local Access Switches serving remote department hosts.

---

## 🛠️ Key Technical Implementations

### 1. VLANs & Subnetting
* **VLAN 10 (IT):** `192.168.10.0/24`
* **VLAN 20 (HR):** `192.168.20.0/24`
* **VLAN 30 (FINANCE):** `192.168.30.0/24`
* **VLAN 50 (SERVERS):** `192.168.50.0/24`
* **Branch 1:** `192.168.70.0/24` | **Branch 2:** `192.168.60.0/24`

### 2. Routing & Core Services
* **Inter-VLAN Routing:** Enabled on Core L3 Switch via SVI interfaces.
* **Dynamic Routing:** **OSPF Area 0** deployed across HQ and Branch routers for full dynamic route propagation.
* **DHCP Relay:** Configured `ip helper-address 192.168.50.10` across SVIs to route DHCP requests centrally.

### 3. Hardening & Network Security
* **Access Control Lists (ACLs):** Enforced isolation between HR and Finance networks while maintaining full IT administrative access.
* **Management Security:** Secured remote access via **SSH v2** and encrypted passwords (`enable secret`, `service password-encryption`).
* **Port Security:** Configured `switchport port-security` with sticky MAC learning and violation restriction on user ports.
* **Firewall & NAT:** Cisco ASA deployed at the edge with Dynamic PAT allowing secure outbound Internet reachability.

---

## ✅ Verification & Testing
- [x] Successful dynamic IP leasing across all VLANs and remote branches via Central DHCP.
- [x] Full OSPF neighbor adjacency and end-to-end ICMP connectivity across branches.
- [x] ACL enforcement verified: HR ping requests to Finance blocked successfully.
- [x] Secure SSH management verified on Routers and Core Switch.
- [x] Outbound NAT translation functional via ASA Firewall.

---

## 📂 Project Artifacts
* `Enterprise-Network-v1.pkt` (Packet Tracer Source File)
* Network Topology Diagram & Configuration Snapshots 
<img width="1917" height="1137" alt="image" src="https://github.com/user-attachments/assets/eda3d2ad-6434-45f0-9e0a-5decdf41370b" />
