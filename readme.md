# Garanti BBVA Enterprise Network Infrastructure Design

## Project Overview
This repository contains a high-availability network infrastructure design for a modern bank branch. The project is built using Cisco Packet Tracer and demonstrates a hierarchical star topology focused on security, scalability, and departmental isolation.

## Network Topology
The architecture consists of a 3650 Multilayer Switch at the Core/Distribution layer and several 2960 switches at the Access layer, providing dedicated connectivity for each floor/department.

### Infrastructure Overview
![Network Infrastructure Map](images/topology_overview.png)
*Figure 1: Full hierarchical network map with departmental segmentation (VLANs).*

## Technical Specifications
- **Hierarchical Design:** Implemented Cisco’s two-tier design model to optimize traffic flow and management.
- **VLAN Segmentation:** Isolated broadcast domains for Tellers, Loans, IT, and Management to enhance internal security.
- **Inter-VLAN Routing:** Configured Switch Virtual Interfaces (SVI) on the Core Switch to enable controlled communication between departments.
- **Wireless Isolation:** Deployed a dedicated WPA2-secured Access Point for Guest and Cafeteria traffic on an independent subnet.

## IP Addressing Table
| Zone | VLAN | Subnet | Gateway |
| :--- | :---: | :--- | :--- |
| Server Room | 10 | 10.0.10.0/24 | 10.0.10.1 |
| Operations | 20 | 10.0.20.0/24 | 10.0.20.1 |
| Loans | 30 | 10.0.30.0/24 | 10.0.30.1 |
| IT Dept | 40 | 10.0.40.0/24 | 10.0.40.1 |
| Management | 50 | 10.0.50.0/24 | 10.0.50.1 |
| Guest/Café | 60 | 192.168.1.0/24 | 192.168.1.1 |

## Verification and Testing
Connectivity has been successfully verified across all VLANs using ICMP (Ping) tests.

### Connectivity Demonstration
![Ping Verification](images/ping_test_results.png)
*Figure 2: Successful ping delivery (envelopes) between departmental workstations and core servers.*

## Repository Structure
- `/src`: Contains the source Cisco Packet Tracer file (`.pkt`).
- `/images`: Includes high-resolution topology diagrams and test proof screenshots.

---
