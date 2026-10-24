# Secure University Campus Network

Building a simulated university network (main campus + branch campus) using Cisco Packet Tracer to practice real-world networking concepts.

## Network Topology

The diagram below illustrates the planned network design for the main and branch campuses, including the proposed VLAN structure.

## What's in the lab?
* Departments & Labs: Separated using VLANs and inter-VLAN routing
* Services:Automated IP assignment via DHCP and remote management via SSH
* Security: Port Security on switches and Access Control Lists (ACLs)
* Connectivity: Connected main and branch campuses with dynamic routing, plus wireless LAN setup

## Tech Stack
* Cisco Packet Tracer
* IPv4 Addressing & Subnetting
* VLANs, Trunking, & Inter-VLAN Routing
* DHCP & Dynamic Routing
* SSH & Port Security
* WLAN & ACLs

## Roadmap / Progress
Working through this step-by-step and uploading configurations as I go:
-  Requirements & topology design / VLAN plan
-  Device placement and cabling
-  VLANs & trunk links configuration
-  Inter-VLAN routing & DHCP setup
-  Campus routing, SSH, & Port Security
-  Wireless access & ACLs
-  Final testing, troubleshooting, and documentation

## Repository Structure
secure-campus-network/
├── README.md
├── Day-01-Topology-Design/
│   ├── requirements.md
│   └── vlan-plan.md
└── packet-tracer/
    └── Secure_Campus_Network.pkt

(More configuration notes, files, and screenshots coming soon as I finish each stage.)

## Goals
I'm building this to get hands-on practice with enterprise networking and to have a solid project to show off when applying for internships.

## Day 1 Progress

- Designed the initial main-campus and branch-campus network topology.
- Added and named the routers, switches, PCs, servers, and wireless devices in Cisco Packet Tracer.
- Connected the network devices and enabled the required router interfaces.
- Created the six planned VLANs on the core switch:
  - VLAN 10 — ADMIN
  - VLAN 20 — FINANCE
  - VLAN 30 — STUDENTS
  - VLAN 40 — IT
  - VLAN 50 — SERVERS
  - VLAN 60 — GUEST_WIFI

**Next steps:** Configure VLANs on the remaining switches, assign access ports, and configure trunk links.
