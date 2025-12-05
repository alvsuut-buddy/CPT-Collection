# Hotel Network Infrastructure Design

**Project Type:** Network Engineering Practicum
**Tool:** Cisco Packet Tracer

## Overview

This project simulates a hierarchical network infrastructure designed for a multi-story hotel building. The topology focuses on traffic segmentation, scalability, and security using Cisco Packet Tracer.

The design implements VLANs for departmental separation, Inter-VLAN Routing for communication between segments, OSPF for routing between floors, and WLAN for mobile accessibility.

---

## Key Configurations

### 1. VLAN & Trunking
* **VLANs 10-80** created across respective switches.
* **Trunk Ports (802.1Q)** configured on uplinks between Switches and Routers to carry tagged traffic.

### 2. Inter-VLAN Routing (Router-on-a-Stick)
* Sub-interfaces configured on routers (e.g., g0/0.60, g0/0.70) acting as default gateways.
* Encapsulation **dot1Q** matches the VLAN IDs.

### 3. Dynamic Routing (OSPF)
* **Protocol:** OSPF Process ID 10.
* **Area:** Backbone Area 0.
* Ensures full connectivity between the 1st, 2nd, and 3rd floors via Serial links.

### 4. DHCP Services
* Routers act as DHCP Servers.
* Dynamic IP allocation for all end devices (PCs, Printers, Smartphones) per VLAN pool.

### 5. Wireless Access (WLAN)
* Deployed 3 Access Points (AP) covering different floors.
* **Security:** WPA2-PSK.
* **SSIDs:** LT1_AP, LT2_AP, LT3_AP.

### 6. Security Implementation
* **SSH:** Enabled on routers for encrypted remote management.
* **Port Security:** Applied on sensitive switch ports (e.g., IT Dept) using Sticky MAC addresses and Shutdown violation mode to prevent unauthorized access.

---

## How to Run

1.  **Prerequisite:** Ensure you have Cisco Packet Tracer version 8.2 or newer installed.
2.  **Download:** Clone this repository or download the .pkt file.
3.  **Open:** Load the hotel-network-design.pkt file in Packet Tracer.
4.  **Convergence:** Wait for amber lights to turn green (STP convergence) or press the Fast Forward Time button.
5.  **Test:**
    * Open a PC Command Prompt.
    * Ping from one VLAN to another (e.g., Logistic 192.168.6.x to Finance 192.168.5.x).
    * Check ipconfig to verify DHCP assignment.

---

**Alvin Oktavian** - 2025


