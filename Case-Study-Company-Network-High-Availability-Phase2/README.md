\# High Availability Network Implementation (Nagoya Company)



\*\*Project Type:\*\* Network Engineering Practicum (Week 11)

\*\*Focus:\*\* First Hop Redundancy Protocol (HSRP), EtherChannel, STP



\## Overview

This project enhances the previous Nagoya Company network by implementing \*\*High Availability\*\* and \*\*Load Balancing\*\*. The goal is to ensure network continuity even if a distribution switch or router fails. This is achieved by configuring HSRP for gateway redundancy and EtherChannel for link aggregation.



\## Key Features \& Configurations



\### 1. EtherChannel (LACP)

\* \[cite\_start]\*\*Link Aggregation:\*\* Configured \*\*Port-Channel 1\*\* between the two Multilayer Switches (MLSW1 and MLSW2) using LACP (Link Aggregation Control Protocol) to increase bandwidth and provide link redundancy \[cite: 53-63].

\* \*\*Mode:\*\* Active-Active configuration.



\### 2. HSRP (Hot Standby Router Protocol)

configured on Multilayer Switches to provide a Virtual Gateway for end devices.

\* \*\*Load Balancing Strategy:\*\*

&nbsp;   \* \*\*MLSW1:\*\* Active Gateway for \*\*Odd VLANs\*\* (10, 30, 50). Standby for Even VLANs.

&nbsp;   \* \*\*MLSW2:\*\* Active Gateway for \*\*Even VLANs\*\* (20, 40, 60). Standby for Odd VLANs.

\* \*\*Configuration Details:\*\*

&nbsp;   \* \[cite\_start]Virtual IP assigned to each VLAN interface \[cite: 38, 78-81].

&nbsp;   \* \[cite\_start]`priority` set to \*\*150\*\* for Active roles and default (100) for Standby \[cite: 84-86].

&nbsp;   \* \[cite\_start]`preempt` enabled to allow the primary device to take over again after recovery\[cite: 87].



\### 3. Spanning Tree Protocol (STP) Optimization

\* Adjusted \*\*Root Bridge\*\* priorities to match the HSRP active paths.

\* MLSW1 is the Root Primary for Odd VLANs.

\* \[cite\_start]MLSW2 is the Root Primary for Even VLANs \[cite: 66-69].



\## Topology Update

\* \*\*Redundant Links:\*\* Added connections between Distribution Layer switches.

\* \*\*Virtual Gateways:\*\* End devices now point to the HSRP Virtual IP, not the physical interface IP.



\## Testing \& Verification

\* \[cite\_start]\*\*Trace Route:\*\* Verified that traffic from VLAN 10 goes through MLSW1, while traffic from VLAN 20 goes through MLSW2 \[cite: 133-137].

\* \[cite\_start]\*\*Failover Test:\*\* Simulating a link failure shows traffic automatically rerouting to the Standby router without connection loss \[cite: 139-147].



---

\*\*Alvin Oktavian\*\* - 2025

