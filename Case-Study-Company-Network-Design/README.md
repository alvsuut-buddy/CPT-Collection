# Case Study: Company Network Design & Configuration

**Project Type:** Network Engineering Practicum
**Tool:** Cisco Packet Tracer

## Overview
This project simulates the network infrastructure for Nagoya Company's new 4-story building. The design focuses on high availability and redundancy using a hierarchical model with dual ISPs. It incorporates advanced routing (OSPF), VLAN segmentation, Inter-VLAN routing via Multilayer Switches, NAT Overload for internet access, and strict security measures.

## Network Topology
The network spans 4 floors and connects to the internet via two ISPs for redundancy.

## Key Configurations

1.  **Redundant Hierarchical Design:**
    * **Core/Distribution:** Two Multilayer Switches (MLSW1, MLSW2) and two Routers (RouterNagoya1, RouterNagoya2) interconnected to provide failover.
    * **ISP Redundancy:** Connected to two separate ISPs (RouterISP1, RouterISP2) via public IP blocks (195.136.17.x).

2.  **VLAN & Inter-VLAN Routing:**
    * Configured VLANs 10-60 on Access Switches.
    * **SVI (Switch Virtual Interface):** Configured on Multilayer Switches to route traffic between VLANs.

3.  **Dynamic Routing (OSPF):**
    * OSPF Process ID 10 configured on all routers and multilayer switches.
    * All internal networks advertised in Area 0 (Backbone).

4.  **Network Services:**
    * **DHCP:** Centralized DHCP Server in Server Room (VLAN 60) providing IPs for all departments via `ip helper-address` configuration on SVI.
    * **DNS & Web:** Internal web server (`nagoya.net`) and DNS resolution.
    * **Email:** SMTP/POP3 service configured for users.

5.  **Internet Access (NAT/PAT):**
    * **NAT Overload (PAT):** Configured on Edge Routers to translate internal private IPs (172.16.x.x) to public IPs using Access Control Lists (ACL).

6.  **Security:**
    * **SSH:** Secure remote access configured on all routers and L3 switches.
    * **Port Security:** Implemented on Finance & Accounting switches (max 1 MAC, sticky, shutdown violation).
    * **WLAN Security:** WPA2-PSK for wireless access in HR & Logistic departments.

## How to Run
1.  Download the `.pkt` file.
2.  Open with **Cisco Packet Tracer** (Version 8.2+).
3.  Wait for OSPF convergence.
4.  **Test Connectivity:**
    * Verify Internet access by pinging ISP routers from internal PCs.
    * Access the corporate website `http://nagoya.net`.
    * Verify redundancy by shutting down one link and testing connectivity.

---
**Alvin Oktavian** - 2025
