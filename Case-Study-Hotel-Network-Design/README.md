\# Case Study: Hotel Network Design \& Configuration



\*\*Project Type:\*\* Network Engineering Practicum

\*\*Tool:\*\* Cisco Packet Tracer



\## Overview

This project simulates a hierarchical network infrastructure for a multi-story hotel building. The design focuses on segmenting traffic using VLANs, enabling communication via Inter-VLAN Routing, and providing wireless access across different floors.



\## Network Topology

The network is divided into 3 floors, connected via routers using Serial DCE cables (OSPF Routing).



\### Floor Distribution \& VLANs

| Floor | Department | VLAN ID | Network Address | Devices |

| :--- | :--- | :--- | :--- | :--- |

| \*\*1st Floor\*\* | Logistic | 60 | 192.168.6.0/24 | PC, Printer |

| | Store | 70 | 192.168.7.0/24 | PC, Printer |

| | Reception | 80 | 192.168.8.0/24 | PC, Printer, AP |

| \*\*2nd Floor\*\* | Sales | 30 | 192.168.3.0/24 | PC, Printer, AP |

| | HR | 40 | 192.168.4.0/24 | PC, Printer |

| | Finance | 50 | 192.168.5.0/24 | PC, Printer |

| \*\*3rd Floor\*\* | IT (Server) | 10 | 192.168.1.0/24 | PC, Printer |

| | Admin | 20 | 192.168.2.0/24 | PC, Printer, AP |



\## Key Configurations

1\.  \*\*VLAN \& Trunking:\*\*

&nbsp;   \* Configured VLANs 10-80 on respective switches.

&nbsp;   \* Trunk ports configured on links between Switches and Routers.

2\.  \*\*Inter-VLAN Routing (Router on a Stick):\*\*

&nbsp;   \* Sub-interfaces created on routers (e.g., g0/0.60, g0/0.70) to act as gateways for each VLAN.

&nbsp;   \* Encapsulation dot1Q used.

3\.  \*\*Routing Protocol (OSPF):\*\*

&nbsp;   \* OSPF Process ID 10 configured on all routers.

&nbsp;   \* Backbone Area 0 used for routing between floors (10.10.10.0/30 networks).

4\.  \*\*DHCP Server:\*\*

&nbsp;   \* Routers configured as DHCP servers to assign dynamic IP addresses to all end devices (PCs, Printers, Smartphones).

5\.  \*\*Wireless Access (WLAN):\*\*

&nbsp;   \* 3 Access Points (AP) configured with WPA2-PSK security.

&nbsp;   \* SSIDs: LT1\_AP, LT2\_AP, LT3\_AP.

6\.  \*\*Security:\*\*

&nbsp;   \* \*\*SSH:\*\* Enabled for secure remote access to routers.

&nbsp;   \* \*\*Port Security:\*\* Enabled on specific switch ports (e.g., IT Dept) with sticky MAC address and shutdown violation mode.



\## Topology Preview

\*(Upload screenshot topologi jaringan hotel kamu di sini)\*



\## How to Run

1\.  Download the hotel-network-design.pkt file.

2\.  Open with Cisco Packet Tracer (Version 8.2 or newer recommended).

3\.  Wait for STP convergence (or press Fast Forward Time).

4\.  Test connectivity by pinging between different VLANs (e.g., Logistic to Finance).



---

\*\*Alvin Oktavian\*\* - 2025

