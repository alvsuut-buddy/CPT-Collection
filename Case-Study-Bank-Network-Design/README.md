# Case Study: Bank Network Design & Configuration

## Overview

This project demonstrates a top-down network design approach for a hierarchical network infrastructure (U Bank). The primary goal is to analyze technical requirements and trade-offs in designing a scalable and manageable network. The design incorporates VLANs, Inter-VLAN routing, OSPF dynamic routing, and essential network services (DHCP, DNS, Web, Email) for a multi-story building and branch offices.

## Network Topology

The network connects a **Headquarters (4 Floors)** with a **Branch Office** and a **Cloud Router**.

### Campus Structure & VLANs

| Location | Department | VLAN ID | Network Address |
| :--- | :--- | :--- | :--- |
| **HQ - Floor 1** | Management | 10 | 192.168.10.0/26 |
| | Research | 20 | 192.168.10.64/26 |
| | HR | 30 | 192.168.10.128/26 |
| **HQ - Floor 2** | Marketing | 40 | 192.168.10.192/26 |
| | Accounting | 50 | 192.168.11.0/26 |
| | Finance | 60 | 192.168.11.64/26 |
| **HQ - Floor 3** | Logistics | 70 | 192.168.11.128/26 |
| | Customer Care | 80 | 192.168.11.192/26 |
| | Guest Area | 90 | 192.168.12.0/26 |
| **HQ - Floor 4** | Administration | 100 | 192.168.12.64/26 |
| | ICT | 110 | 192.168.12.128/26 |
| | Server Room | 120 | 192.168.12.192/26 |
| **Branch Office** | FKG | 90 | 192.168.9.0/24 |
| | FK | 100 | 192.168.10.0/24 |

## Key Configurations

1. **Hierarchical Design:**
   * **Core Layer:** High-speed routers (MainRT) connecting different distribution blocks.
   * **Distribution Layer:** Multilayer Switches (L3SW) handling Inter-VLAN routing for each floor.
   * **Access Layer:** Switches connecting end devices.

2. **VLAN & Trunking:**
   * Configured VLANs 10-120 across multiple switches.
   * Trunk links established between Access Switches and Multilayer Switches.

3. **Inter-VLAN Routing:**
   * **Multilayer Switching (SVI):** Configured on L3 Switches (LT1_L3SW to LT4_L3SW) to route traffic between VLANs on the same floor.
   * **Router-on-a-Stick:** Used for Branch Office routing.

4. **Routing Protocol (OSPF):**
   * OSPF Process ID 10 configured on all Routers and L3 Switches.
   * Area 0 (Backbone) used for all inter-router connections (10.10.10.x networks).

5. **Network Services:**
   * **DHCP:** Configured on MainRT and BranchRT to assign IPs to specific VLAN pools using `ip helper-address` on L3 switches to relay requests.
   * **DNS:** Resolves `ubank.net`.
   * **Web Server:** Internal website hosted at `192.168.12.194`.
   * **Mail Server:** Email service for users (e.g., `alvin@andromeda.com`).

6. **Security:**
   * **SSH:** Enabled on routers and switches for secure remote management (RSA 1024 bit).
   * **Port Security:** Configured on access ports (sticky MAC, violation shutdown).
   * **WLAN Security:** WPA2-PSK authentication for Guest Area Access Points.

## Trade-Off Analysis

In this design, we prioritized **Scalability** and **Performance** by using Multilayer Switches at the distribution layer. This reduces the load on the main router compared to a Router-on-a-Stick model, although it increases hardware cost. OSPF was chosen over RIP for faster convergence and better scalability for a large enterprise network.

## How to Run

1. Download the `.pkt` file.
2. Open with Cisco Packet Tracer (Version 8.2+).
3. Wait for OSPF neighbor adjacency to form (convergence).
4. **Test Connectivity:**
   * Ping between PC Management (VLAN 10) and Laptop Guest (VLAN 90).
   * Access the web server via browser: `http://192.168.12.194`.
   * Send an email between different users.

---

**Alvin Oktavian** - 2025
