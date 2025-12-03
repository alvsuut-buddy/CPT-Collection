\# Case Study: Company Network Design \& Configuration



\*\*Project Type:\*\* Network Engineering Practicum

\*\*Tool:\*\* Cisco Packet Tracer



\## Overview

This project simulates the network infrastructure for Nagoya Company's new 4-story building. The design focuses on high availability and redundancy using a hierarchical model with dual ISPs. It incorporates advanced routing (OSPF), VLAN segmentation, Inter-VLAN routing via Multilayer Switches, NAT Overload for internet access, and strict security measures.



\## Network Topology

The network spans 4 floors and connects to the internet via two ISPs for redundancy.



\### Floor Distribution \& VLANs

| Floor | Department | VLAN ID | Network Address |

| :--- | :--- | :--- | :--- |

| \*\*Floor 1\*\* | Sales \& Marketing | 10 | 172.16.1.0/25 |

| | HR \& Logistic | 20 | 172.16.1.128/25 |

| \*\*Floor 2\*\* | Finance \& Accounting | 30 | 172.16.2.0/25 |

| | Admin \& Humas | 40 | 172.16.2.128/25 |

| \*\*Floor 3\*\* | IT | 50 | 172.16.3.0/25 |

| | Server Room | 60 | 172.16.3.128/25 |

| \*\*Floor 4\*\* | (Future Expansion) | - | - |



\## Key Configurations

1\.  \*\*Redundant Hierarchical Design:\*\*

&nbsp;   \* \*\*Core/Distribution:\*\* Two Multilayer Switches (MLSW1, MLSW2) and two Routers (RouterNagoya1, RouterNagoya2) interconnected to provide failover.

&nbsp;   \* \*\*ISP Redundancy:\*\* Connected to two separate ISPs (RouterISP1, RouterISP2) via public IP blocks (195.136.17.x).

2\.  \*\*VLAN \& Inter-VLAN Routing:\*\*

&nbsp;   \* Configured VLANs 10-60 on Access Switches.

&nbsp;   \* \*\*SVI (Switch Virtual Interface):\*\* Configured on Multilayer Switches to route traffic between VLANs.

3\.  \*\*Dynamic Routing (OSPF):\*\*

&nbsp;   \* OSPF Process ID 10 configured on all routers and multilayer switches.

&nbsp;   \* All internal networks advertised in Area 0 (Backbone).

4\.  \*\*Network Services:\*\*

&nbsp;   \* \*\*DHCP:\*\* Centralized DHCP Server in Server Room (VLAN 60) providing IPs for all departments via `ip helper-address` configuration on SVI.

&nbsp;   \* \*\*DNS \& Web:\*\* Internal web server (`nagoya.net`) and DNS resolution.

&nbsp;   \* \*\*Email:\*\* SMTP/POP3 service configured for users.

5\.  \*\*Internet Access (NAT/PAT):\*\*

&nbsp;   \* \*\*NAT Overload (PAT):\*\* Configured on Edge Routers to translate internal private IPs (172.16.x.x) to public IPs using Access Control Lists (ACL).

6\.  \*\*Security:\*\*

&nbsp;   \* \*\*SSH:\*\* Secure remote access configured on all routers and L3 switches.

&nbsp;   \* \*\*Port Security:\*\* Implemented on Finance \& Accounting switches (max 1 MAC, sticky, shutdown violation).

&nbsp;   \* \*\*WLAN Security:\*\* WPA2-PSK for wireless access in HR \& Logistic departments.



\## Trade-Off Analysis

This design prioritizes \*\*Redundancy\*\* and \*\*Availability\*\* by duplicating core devices and ISP links, which increases cost and complexity but ensures business continuity. OSPF is used for fast convergence in this complex topology.



\## How to Run

1\.  Download the .pkt file.

2\.  Open with Cisco Packet Tracer (Version 8.2+).

3\.  Wait for OSPF convergence.

4\.  \*\*Test Connectivity:\*\*

&nbsp;   \* Verify Internet access by pinging ISP routers from internal PCs.

&nbsp;   \* Access the corporate website `http://nagoya.net`.

&nbsp;   \* Verify redundancy by shutting down one link and testing connectivity.



---

\*\*Alvin Oktavian\*\* - 2025

