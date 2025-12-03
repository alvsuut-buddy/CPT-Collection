\# Analisis Tujuan Teknis dan Trade-Off pada Desain Jaringan Sederhana



\*\*Project Type:\*\* Network Engineering Practicum

\*\*Tool:\*\* Cisco Packet Tracer



\## Overview

This project demonstrates a top-down network design approach for a hierarchical network infrastructure (Andromeda Campus). The primary goal is to analyze technical requirements and trade-offs in designing a scalable and manageable network. The design incorporates VLANs, Inter-VLAN routing, dynamic routing (RIPv2), and essential network services (DHCP, DNS, Web, Email).



\## Network Topology

The network connects a \*\*Main Campus\*\* (3 floors) with a \*\*Branch Campus\*\* and a \*\*Cloud Router\*\*.



\### Campus Structure \& VLANs

| Location | Department | VLAN ID | Network Address |

| :--- | :--- | :--- | :--- |

| \*\*Main - Floor 1\*\* | Logistic | 60 | 192.168.6.0/24 |

| | Store | 70 | 192.168.7.0/24 |

| | Reception | 80 | 192.168.8.0/24 |

| \*\*Main - Floor 2\*\* | Sales | 30 | 192.168.3.0/24 |

| | HR | 40 | 192.168.4.0/24 |

| | Finance | 50 | 192.168.5.0/24 |

| \*\*Main - Floor 3\*\* | IT (Server) | 10 | 192.168.1.0/24 |

| | Admin | 20 | 192.168.2.0/24 |

| \*\*Branch Campus\*\* | FKG | 90 | 192.168.9.0/24 |

| | FK | 100 | 192.168.10.0/24 |



\## Key Configurations

1\.  \*\*Hierarchical Design:\*\*

&nbsp;   \* \*\*Core/Distribution Layer:\*\* Multilayer Switches (MainSW, BranchSW) handling Inter-VLAN routing.

&nbsp;   \* \*\*Access Layer:\*\* Switches connecting end devices.

&nbsp;   \* \*\*Edge/Router Layer:\*\* Routers (MainRT, BranchRT, CloudRT) connecting different sites via Serial links.

2\.  \*\*VLAN \& Trunking:\*\*

&nbsp;   \* Configured VLANs 10-100.

&nbsp;   \* Trunk links established between Access Switches and Distribution Switches/Routers.

3\.  \*\*Inter-VLAN Routing:\*\*

&nbsp;   \* \*\*Router-on-a-Stick:\*\* Implemented on MainRT and BranchRT using sub-interfaces (e.g., `g0/0.10`, `g0/0.20`) with dot1Q encapsulation.

4\.  \*\*Routing Protocol (RIPv2):\*\*

&nbsp;   \* RIP version 2 configured on all routers (MainRT, BranchRT, CloudRT) to advertise connected networks (192.168.x.0/24 and 10.10.10.0/30).

5\.  \*\*Network Services:\*\*

&nbsp;   \* \*\*DHCP:\*\* Routers configured as DHCP servers for all departments.

&nbsp;   \* \*\*DNS:\*\* DNS server configured to resolve `andromeda.com`.

&nbsp;   \* \*\*Web Server:\*\* Hosted website accessible via domain.

&nbsp;   \* \*\*Mail Server:\*\* Email service configured for users (e.g., `alvin@andromeda.com`).

6\.  \*\*Security:\*\*

&nbsp;   \* \*\*SSH:\*\* Enabled on routers for secure remote management.

&nbsp;   \* \*\*Port Security:\*\* Configured on IT Dept switch ports (sticky MAC, violation shutdown).

&nbsp;   \* \*\*WLAN Security:\*\* WPA2-PSK authentication for Access Points on each floor.



\## Trade-Off Analysis

In this design, we prioritized \*\*Scalability\*\* and \*\*Manageability\*\* (using dynamic routing and DHCP) over \*\*Cost\*\* (requiring more routers and multilayer switches). The use of RIPv2 is suitable for this small-to-medium network size but might need to be upgraded to OSPF for larger implementations.



\## How to Run

1\.  Download the `.pkt` file.

2\.  Open with \*\*Cisco Packet Tracer\*\* (Version 8.2+).

3\.  Wait for convergence.

4\.  \*\*Test Connectivity:\*\*

&nbsp;   \* Ping between PC Akademik (VLAN 10) and PC FKG (VLAN 90).

&nbsp;   \* Access the web server via browser: `http://andromeda.com`.

&nbsp;   \* Send an email from PC FK to PC FH.



---

\*\*Alvin Oktavian\*\* - 2025

