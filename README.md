# Secure University Campus Network

A simulated university campus network built using Cisco Packet Tracer to gain hands-on experience with enterprise networking concepts. The project represents a main campus and a branch campus, with a focus on network segmentation, connectivity, and security.

## Network Topology

The diagram below illustrates the planned network design for the main and branch campuses, including the proposed VLAN structure.

![Secure University Campus Network Topology](Day-01-Topology-Design/campus-topology.png.png)

*Note: IP addressing, inter-VLAN routing, DHCP, campus routing, and security configurations will be implemented and tested in upcoming stages.*

## Planned Lab Features

- **Network Segmentation:** Separate university departments using VLANs and inter-VLAN routing.
- **Network Services:** Automatic IP address assignment using DHCP and secure remote device management using SSH.
- **Network Security:** Switch Port Security and Access Control Lists (ACLs).
- **Campus Connectivity:** Connect the main and branch campuses using routing.
- **Wireless Networking:** Provide wireless access for staff and guest users.

## Technology Stack

- Cisco Packet Tracer
- IPv4 Addressing and Subnetting
- VLANs and Trunking
- Inter-VLAN Routing
- DHCP
- Dynamic Routing
- SSH
- Switch Port Security
- Wireless LAN (WLAN)
- Access Control Lists (ACLs)

## Planned VLAN and IP Addressing Scheme

The following IP ranges are the proposed addressing plan. They will be configured and tested during the implementation stages.

| VLAN ID | VLAN Name | Planned Network |
|---:|---|---|
| 10 | ADMIN | `10.10.10.0/24` |
| 20 | FINANCE | `10.10.20.0/24` |
| 30 | STUDENTS | `10.10.30.0/24` |
| 40 | IT | `10.10.40.0/24` |
| 50 | SERVERS | `10.10.50.0/24` |
| 60 | GUEST_WIFI | `10.10.60.0/24` |

## Day 1 Progress

- Designed the initial main-campus and branch-campus topology.
- Added and named the routers, switches, PCs, servers, and wireless devices in Cisco Packet Tracer.
- Connected the network devices and enabled the required router interfaces.
- Created six planned VLANs on the core switch:
  - VLAN 10 — ADMIN
  - VLAN 20 — FINANCE
  - VLAN 30 — STUDENTS
  - VLAN 40 — IT
  - VLAN 50 — SERVERS
  - VLAN 60 — GUEST_WIFI

**Next steps:** Configure VLANs on the remaining switches, assign access ports, and configure trunk links.

## Repository Structure

```text
secure-campus-network/
├── README.md
├── Day-01-Topology-Design/
│   ├── requirements.md
│   ├── vlan-plan.md
│   └── campus-topology.png
└── packet-tracer/
    └── Secure_Campus_Network.pkt
```

*Note: The structure above represents the intended project organization. Add files as they are created and uploaded.*

## Project Goals

- Develop practical Cisco networking and troubleshooting skills.
- Understand how VLANs, routing, DHCP, and network security work together.
- Build a documented networking portfolio for internship applications.
- Gain hands-on experience with concepts covered in CCNA studies.

## Project Status

**Currently working on:** Initial topology design and VLAN configuration.

This project is being developed step by step using Cisco Packet Tracer. Configurations, testing results, screenshots, and documentation will be added as each stage is completed.
