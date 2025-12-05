# High Availability Network Implementation (Nagoya Company)

**Project Type:** Network Engineering Practicum (Week 11)
**Focus:** First Hop Redundancy Protocol (HSRP), EtherChannel, STP

## Overview
This project enhances the previous Nagoya Company network by implementing **High Availability** and **Load Balancing**. The goal is to ensure network continuity even if a distribution switch or router fails. This is achieved by configuring HSRP for gateway redundancy and EtherChannel for link aggregation.

## Key Features & Configurations

### 1. EtherChannel (LACP)
* **Link Aggregation:** Configured **Port-Channel 1** between the two Multilayer Switches (MLSW1 and MLSW2) using LACP (Link Aggregation Control Protocol) to increase bandwidth and provide link redundancy.
* **Mode:** Active-Active configuration.

### 2. HSRP (Hot Standby Router Protocol)
Configured on Multilayer Switches to provide a Virtual Gateway for end devices.

* **Load Balancing Strategy:**
    * **MLSW1:** Active Gateway for **Odd VLANs** (10, 30, 50). Standby for Even VLANs.
    * **MLSW2:** Active Gateway for **Even VLANs** (20, 40, 60). Standby for Odd VLANs.
* **Configuration Details:**
    * Virtual IP assigned to each VLAN interface.
    * `priority` set to **150** for Active roles and default (100) for Standby.
    * `preempt` enabled to allow the primary device to take over again after recovery.

### 3. Spanning Tree Protocol (STP) Optimization
* Adjusted **Root Bridge** priorities to match the HSRP active paths.
* **MLSW1** is the Root Primary for Odd VLANs (10, 30, 50).
* **MLSW2** is the Root Primary for Even VLANs (20, 40, 60).

## Topology Update
* **Redundant Links:** Added connections between Distribution Layer switches.
* **Virtual Gateways:** End devices now point to the HSRP Virtual IP, not the physical interface IP.

## Testing & Verification
* **Trace Route:** Verified that traffic from VLAN 10 goes through MLSW1, while traffic from VLAN 20 goes through MLSW2.
* **Failover Test:** Simulating a link failure shows traffic automatically rerouting to the Standby router without connection loss.

---
**Alvin Oktavian** - 2025
