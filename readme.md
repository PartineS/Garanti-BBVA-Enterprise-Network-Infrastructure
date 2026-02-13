# Garanti BBVA Enterprise Network Infrastructure Design

## Project Overview
This project represents a comprehensive architectural design and implementation of a secure, scalable, and high-performance network infrastructure for a modern bank branch. Modeled after enterprise-grade banking standards, the simulation focuses on high availability and strict departmental isolation using the Cisco Hierarchical Design Model.

## Design Philosophy
The infrastructure is built on a **Core-Access layer architecture** to ensure that local departmental traffic is handled efficiently at the access layer while inter-departmental communication is managed by a high-speed multilayer core.

### 1. Infrastructure Overview (Global Topology)
The following diagram illustrates the complete hierarchical star topology, including the server room, operational departments, and guest zones.

![Network Infrastructure Map](https://i.imgur.com/MO0Sxpz.jpg)
*Figure 1: Complete network map showcasing departmental segmentation and device positioning.*

## Technical Specifications & Implementation

### A. Network Segmentation (VLANs)
To mitigate security risks such as unauthorized lateral movement, the network is logically partitioned into distinct VLANs. Each zone is isolated within its own broadcast domain:

| Zone | VLAN ID | Subnet | Gateway | Description |
| :--- | :---: | :--- | :--- | :--- |
| **Server Room** | 10 | 10.0.10.0/24 | 10.0.10.1 | Core banking servers & local assets |
| **Operations** | 20 | 10.0.20.0/24 | 10.0.20.1 | Teller and front-office banking |
| **Loans** | 30 | 10.0.30.0/24 | 10.0.30.1 | Specialized individual banking services |
| **IT Dept** | 40 | 10.0.40.0/24 | 10.0.40.1 | Network administration and technical support |
| **Management** | 50 | 10.0.50.0/24 | 10.0.50.1 | Executive-level internal workstations |
| **Guest/Café** | 60 | 192.168.1.0/24 | 192.168.1.1 | Isolated wireless guest access |

### B. Core Switching & Routing
- **Inter-VLAN Routing:** A Cisco 3650 Multilayer Switch acts as the network backbone, utilizing Switch Virtual Interfaces (SVI) to facilitate communication between departments.
- **IEEE 802.1Q Trunking:** All uplinks between access switches (2960) and the core switch are configured as trunk ports to manage multi-VLAN traffic.
- **Peripheral Connectivity:** High-speed Fast Ethernet modules were deployed for enterprise printers to ensure seamless office automation across all floors.

## Verification and Testing

### ICMP Connectivity (Ping Tests)
Connectivity has been rigorously verified across all network segments. The successful ICMP (Ping) tests confirm that the routing logic, gateway configurations, and trunking protocols are functioning optimally.

![Ping Verification](https://i.imgur.com/RXxoJD2.png)
*Figure 2: Real-time verification showcasing successful packet delivery between workstations and the central server room.*

### Service Accessibility
- **Local Web Services:** Internal HTTP servers are accessible via departmental PC browsers, confirming Layer 7 (Application) functionality.
- **Printer Integration:** Peripheral devices successfully respond to requests from their respective subnets, confirming correct VLAN port assignments.

## Future Roadmap
This Packet Tracer design serves as a blueprint for the next phase of the project:
1.  **Virtualization:** Transitioning the network logic to a **pfSense** environment within **VirtualBox**.
2.  **Firewall Policies:** Implementing granular Access Control Lists (ACLs) to restrict sensitive server access.

---
**Developer:** [PartineS](https://github.com/PartineS)
