# Garanti BBVA – Enterprise Network Infrastructure Design

## Project Overview
This project presents a secure, scalable, and enterprise-grade network infrastructure design for a modern banking branch.  
The architecture is modeled according to real-world banking standards, focusing on high availability, departmental isolation, and efficient traffic management using the Cisco Hierarchical Design Model.

The entire topology has been designed and tested in Cisco Packet Tracer, simulating real operational behavior in a financial institution environment.

---

## Design Philosophy
The infrastructure follows a Core–Access Layer Architecture, ensuring:

- Efficient handling of local traffic at the access layer  
- High-speed inter-departmental communication at the core layer  
- Logical separation of departments to prevent lateral movement  
- Centralized routing and policy enforcement  

---

## Infrastructure Overview (Global Topology)

![Network Infrastructure Map](images/topology.png)

Figure 1:  
Complete hierarchical star topology illustrating the core switch, access switches, server room, operational departments, and isolated guest network.

---

## Technical Specifications and Implementation

### A. Network Segmentation (VLAN Architecture)

To minimize security risks and enforce strict access boundaries, the network is segmented into multiple VLANs, each mapped to a dedicated subnet and gateway.

| Zone | VLAN ID | Subnet | Gateway | Description |
|---|---|---|---|---|
| Server Room | 10 | 10.0.10.0/24 | 10.0.10.1 | Core banking servers and internal services |
| Operations | 20 | 10.0.20.0/24 | 10.0.20.1 | Teller desks and front-office operations |
| Loans | 30 | 10.0.30.0/24 | 10.0.30.1 | Individual and corporate loan services |
| IT Department | 40 | 10.0.40.0/24 | 10.0.40.1 | Network administration and system support |
| Management | 50 | 10.0.50.0/24 | 10.0.50.1 | Executive and managerial systems |
| Guest / Café | 60 | 192.168.1.0/24 | 192.168.1.1 | Fully isolated wireless guest access |

---

### B. Core Switching and Routing

- Inter-VLAN Routing  
  Implemented via a Cisco 3650 Multilayer Switch using Switch Virtual Interfaces (SVIs).

- IEEE 802.1Q Trunking  
  All uplinks between Cisco 2960 access switches and the core switch operate in trunk mode to carry multi-VLAN traffic.

- Peripheral Connectivity  
  Enterprise printers are connected to access switches with correct VLAN assignments, ensuring seamless departmental printing.

---

## Verification and Testing

### ICMP Connectivity (Ping Tests)

![Ping Verification](images/ping-test.png)

Figure 2:  
Successful ICMP tests between workstations and the server network confirm:

- Correct VLAN assignment  
- Proper gateway configuration  
- Functional inter-VLAN routing  
- Stable trunk connections  

---

### Service Accessibility Validation

- Internal Web Services  
  Departmental workstations can successfully access internal HTTP services hosted in the server VLAN.

- Printer Services  
  Network printers respond correctly within their assigned VLANs, validating access-layer configuration accuracy.

---

## Future Roadmap

This project serves as a foundation for further enterprise-level enhancements:

1. Virtualized Firewall Deployment  
   Migration of routing and firewall logic to pfSense deployed on VirtualBox or VMware.

2. Advanced Security Policies  
   Implementation of granular Access Control Lists (ACLs) to restrict sensitive server access.

3. Monitoring and Logging  
   Integration of centralized logging, traffic monitoring, and audit readiness mechanisms.

---

## Developer
PartineS  
https://github.com/PartineS

---

This project demonstrates enterprise networking principles such as VLAN segmentation, inter-VLAN routing, hierarchical design, and secure departmental isolation within a banking infrastructure.
