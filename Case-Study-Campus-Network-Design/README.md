# Analysis of Technical Objectives and Trade-Offs in Simple Network Design

**Project Type:** Network Engineering Practicum
**Tool:** Cisco Packet Tracer

## Overview
This project demonstrates a top-down network design approach for a hierarchical network infrastructure (Andromeda Campus). The primary goal is to analyze technical requirements and trade-offs in designing a scalable and manageable network. The design incorporates VLANs, Inter-VLAN routing, dynamic routing (RIPv2), and essential network services (DHCP, DNS, Web, Email).

## Network Topology
The network connects a **Main Campus** (3 floors) with a **Branch Campus** and a **Cloud Router**.

## Key Configurations

1.  **Hierarchical Design:**
    * **Core/Distribution Layer:** Multilayer Switches (MainSW, BranchSW) handling Inter-VLAN routing.
    * **Access Layer:** Switches connecting end devices.
    * **Edge/Router Layer:** Routers (MainRT, BranchRT, CloudRT) connecting different sites via Serial links.

2.  **VLAN & Trunking:**
    * Configured VLANs 10-100.
    * Trunk links established between Access Switches and Distribution Switches/Routers.

3.  **Inter-VLAN Routing:**
    * **Router-on-a-Stick:** Implemented on MainRT and BranchRT using sub-interfaces (e.g., `g0/0.10`, `g0/0.20`) with dot1Q encapsulation.

4.  **Routing Protocol (RIPv2):**
    * RIP version 2 configured on all routers (MainRT, BranchRT, CloudRT) to advertise connected networks (192.168.x.0/24 and 10.10.10.0/30).

5.  **Network Services:**
    * **DHCP:** Routers configured as DHCP servers for all departments.
    * **DNS:** DNS server configured to resolve `andromeda.com`.
    * **Web Server:** Hosted website accessible via domain.
    * **Mail Server:** Email service configured for users (e.g., `alvin@andromeda.com`).

6.  **Security:**
    * **SSH:** Enabled on routers for secure remote management.
    * **Port Security:** Configured on IT Dept switch ports (sticky MAC, violation shutdown).
    * **WLAN Security:** WPA2-PSK authentication for Access Points on each floor.

## Trade-Off Analysis
In this design, we prioritized **Scalability** and **Manageability** (using dynamic routing and DHCP) over **Cost** (requiring more routers and multilayer switches). The use of RIPv2 is suitable for this small-to-medium network size but might need to be upgraded to OSPF for larger implementations.

## How to Run
1.  Download the `.pkt` file.
2.  Open with **Cisco Packet Tracer** (Version 8.2+).
3.  Wait for convergence.
4.  **Test Connectivity:**
    * Ping between PC Akademik (VLAN 10) and PC FKG (VLAN 90).
    * Access the web server via browser: `http://andromeda.com`.
    * Send an email from PC FK to PC FH.

---
**Alvin Oktavian** - 2025
