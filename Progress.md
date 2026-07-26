# 📈 Project Progress & Learning Log

## 📌 Project Overview
* **Project Name:** Enterprise Network Project - Small Business Infrastructure
* **Number of VLANs:** 4 VLANs (HR, IT, Finance, Server/Management)
* **Total Devices:** 15 Devices (2 Routers, 2 Switches, 1 Server, 9 PCs)

---

## 🧠 Key Learnings
During the implementation of this enterprise network project, I strengthened and applied several core CCNA concepts and practices:

1. **Network Segmentation & VTY Security:** Learned how to isolate departmental traffic using VLANs, configure standard trunk links, and enforce secure SSHv2 remote management over VTY lines while completely disabling insecure Telnet.
2. **Inter-VLAN Routing & Dynamic IP Services:** Configured Router-on-a-Stick (ROAS) using sub-interfaces with `802.1Q` encapsulation and automated IP distribution via localized DHCP pools on Cisco routers.
3. **Inter-Router Connectivity:** Applied Static Routing between multiple routers to achieve complete end-to-end network reachability.
4. **Security Hardening Standards:** Implemented essential device security practices, including securing console access, setting up local user authentication, and disabling/shutting down unused switch ports to prevent unauthorized access.

---

## 🛠️ Major Challenge & Resolution

### 🚨 The Problem:
During the SSH verification phase, the client PC was unable to establish an SSH connection to the switch SVI (`Connection timed out; remote host not responding`).

### 🔍 Cause & Troubleshooting:
Upon investigating interface statuses using `show ip interface brief`, the management SVI (`VLAN 99`) was in an `UP/DOWN` state. The SVI line protocol remained down because the switch port connected to the device was not assigned to `VLAN 99`, leaving no active physical access or trunk ports carrying that VLAN traffic.

### 💡 Resolution:
1. Assigned the connected switchport to `VLAN 99` using `switchport access vlan 99`.
2. Verified that the trunk link allowed `VLAN 99` traffic across to the gateway router.
3. Verified the interface status again (`UP/UP`), performed a successful `ping`, and successfully established the SSH session (`ssh -l <username> <SVI_IP>`).
