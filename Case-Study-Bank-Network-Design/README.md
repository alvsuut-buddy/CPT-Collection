\# Case Study: Bank Network Design \& Configuration



\*\*Project Type:\*\* Network Engineering Practicum

\*\*Tool:\*\* Cisco Packet Tracer



\## Overview

This project demonstrates a top-down network design approach for a hierarchical network infrastructure (U Bank). The primary goal is to analyze technical requirements and trade-offs in designing a scalable and manageable network. The design incorporates VLANs, Inter-VLAN routing, OSPF dynamic routing, and essential network services (DHCP, DNS, Web, Email) for a multi-story building and branch offices.



\## Network Topology

The network connects a \*\*Headquarters (4 Floors)\*\* with a \*\*Branch Office\*\* and a \*\*Cloud Router\*\*.



\### Campus Structure \& VLANs

| Location | Department | VLAN ID | Network Address |

| :--- | :--- | :--- | :--- |

| \*\*HQ - Floor 1\*\* | Management | 10 | 192.168.10.0/26 |

| | Research | 20 | 192.168.10.64/26 |

| | HR | 30 | 192.168.10.128/26 |

| \*\*HQ - Floor 2\*\* | Marketing | 40 | 192.168.10.192/26 |

| | Accounting | 50 | 192.168.11.0/26 |

| | Finance | 60 | 192.168.11.64/26 |

| \*\*HQ - Floor 3\*\* | Logistics | 70 | 192.168.11.128/26 |

| | Customer Care | 80 | 192.168.11.192/26 |

| | Guest Area | 90 | 192.168.12.0/26 |

| \*\*HQ - Floor 4\*\* | Administration | 100 | 192.168.12.64/26 |

| | ICT | 110 | 192.168.12.128/26 |

| | Server Room | 120 | 192.168.12.192/26 |

| \*\*Branch Office\*\* | FKG | 90 | 192.168.9.0/24 |

| | FK | 100 | 192.168.10.0/24 |



\## Key Configurations

1\.  \*\*Hierarchical Design:\*\*

&nbsp;   \* \*\*Core Layer:\*\* High-speed routers (MainRT) connecting different distribution blocks.

&nbsp;   \* \*\*Distribution Layer:\*\* Multilayer Switches (L3SW) handling Inter-VLAN routing for each floor.

&nbsp;   \* \*\*Access Layer:\*\* Switches connecting end devices.

2\.  \*\*VLAN \& Trunking:\*\*

&nbsp;   \* Configured VLANs 10-120 across multiple switches.

&nbsp;   \* Trunk links established between Access Switches and Multilayer Switches.

3\.  \*\*Inter-VLAN Routing:\*\*

&nbsp;   \* \[cite\_start]\*\*Multilayer Switching (SVI):\*\* Configured on L3 Switches (LT1\_L3SW to LT4\_L3SW) to route traffic between VLANs on the same floor \[cite: 9919-10081].

&nbsp;   \* \*\*Router-on-a-Stick:\*\* Used for Branch Office routing.

4\.  \*\*Routing Protocol (OSPF):\*\*

&nbsp;   \* \[cite\_start]OSPF Process ID 10 configured on all Routers and L3 Switches \[cite: 9852-9913].

&nbsp;   \* Area 0 (Backbone) used for all inter-router connections (10.10.10.x networks).

5\.  \*\*Network Services:\*\*

&nbsp;   \* \[cite\_start]\*\*DHCP:\*\* Configured on MainRT and BranchRT to assign IPs to specific VLAN pools using `ip helper-address` on L3 switches to relay requests\[cite: 9921].

&nbsp;   \* \*\*DNS:\*\* Resolves `ubank.net`.

&nbsp;   \* \*\*Web Server:\*\* Internal website hosted at `192.168.12.194`.

&nbsp;   \* \[cite\_start]\*\*Mail Server:\*\* Email service for users (e.g., `alvin@andromeda.com`) \[cite: 8130-8158].

6\.  \*\*Security:\*\*

&nbsp;   \* \[cite\_start]\*\*SSH:\*\* Enabled on routers and switches for secure remote management (RSA 1024 bit) \[cite: 9293-9413].

&nbsp;   \* \*\*Port Security:\*\* Configured on access ports (sticky MAC, violation shutdown).

&nbsp;   \* \[cite\_start]\*\*WLAN Security:\*\* WPA2-PSK authentication for Guest Area Access Points \[cite: 10083-10113].



\## Trade-Off Analysis

In this design, we prioritized \*\*Scalability\*\* and \*\*Performance\*\* by using Multilayer Switches at the distribution layer. This reduces the load on the main router compared to a Router-on-a-Stick model, although it increases hardware cost. OSPF was chosen over RIP for faster convergence and better scalability for a large enterprise network.



\## How to Run

1\.  Download the .pkt file.

2\.  Open with Cisco Packet Tracer (Version 8.2+).

3\.  Wait for OSPF neighbor adjacency to form (convergence).

4\.  \*\*Test Connectivity:\*\*

&nbsp;   \* Ping between PC Management (VLAN 10) and Laptop Guest (VLAN 90).

&nbsp;   \* Access the web server via browser: `http://192.168.12.194`.

&nbsp;   \* Send an email between different users.



---

\*\*Alvin Oktavian\*\* - 2025

