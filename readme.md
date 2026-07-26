# Enterprise Network Project - Small Business Infrastructure

## 📌 Project Overview
This project demonstrates the design, configuration, and security hardening of a small enterprise network topology using Cisco networking standards (CCNA best practices). The infrastructure supports multi-departmental isolation, dynamic IP addressing, inter-VLAN routing, secure remote management, and inter-router connectivity.

---

## 📐 Network Topology & Hardware Specs

| Device Type | Quantity | Model / Role |
| :--- | :---: | :--- |
| **Routers** | 2 | Cisco Integrated Services Router (Inter-VLAN & Static Routing) |
| **Switches** | 2 | Cisco Catalyst Switch (VLANs, Access/Trunk Ports) |
| **Server** | 1 | Enterprise Application / Central Server |
| **End Devices** | 10 | Workstations distributed across departments |

---

## 🌐 VLANs & IP Addressing Scheme

| Department | VLAN ID | Device Count | Subnet Range | Subnet Mask | Default Gateway |
| :--- | :---: | :---: | :--- | :--- | :--- |
| **HR** | 10 | 3 | `192.168.10.0/24` | `255.255.255.0` | `192.168.10.1` |
| **IT** | 20 | 3 | `192.168.20.0/24` | `255.255.255.0` | `192.168.20.1` |
| **Finance** | 30 | 4 | `192.168.30.0/24` | `255.255.255.0` | `192.168.30.1` |
| **Server / Mgmt** | 40 | 1 | `192.168.40.0/24` | `255.255.255.0` | `192.168.40.1` |

---

## 🛠️ Technical Configuration Highlights

### 1. Layer 2 Segmentation & Trunking
* Configured dedicated **VLANs (10, 20, 30, 40)** across switches to isolate departmental traffic.
* Standardized 802.1Q **Trunk links** enabled between switches and routers to carry multi-VLAN traffic.

### 2. Inter-VLAN Routing & Services
* Implemented **Router-on-a-Stick (ROAS)** on sub-interfaces (`.10`, `.20`, `.30`, `.40`) for seamless inter-departmental communication.
* Dynamic IP allocation via localized **DHCP Pools** on the router, providing IP, Subnet Mask, Default Gateway, and DNS settings automatically to end devices.
* Established **Static Routing** between `R1` and `R2` to guarantee end-to-end reachability across the multi-router topology.

### 3. Security Hardening (Best Practices)
* **Port Security & Hardening:** Disabled and shut down all unused interfaces (`shutdown`) to mitigate unauthorized physical access.
* **Device Identification:** Applied standard device naming conventions (`R1`, `R2`, `SW1`, `SW2`).
* **Access Protection:** Secured Console and VTY lines with strong encrypted passwords (`secret`).
* **Secure Remote Access:** Enforced **SSHv2** on VTY lines and completely disabled unencrypted Telnet (`transport input ssh`).

---

## 🧪 Testing & Verification

1. **Inter-VLAN Connectivity:** Verified full IP reachability using `ping` across all distinct VLANs.
2. **Server Access:** Confirmed all workstations can successfully access the centralized Server (`VLAN 40`).
3. **DHCP Verification:** Validated automatic IP lease assignments on host PCs using `ipconfig /all`.
4. **SSH Verification:** Confirmed active encrypted management sessions using `show ip ssh` on active nodes.

---
*Developed as part of the Enterprise Network Engineering Practical Labs.*