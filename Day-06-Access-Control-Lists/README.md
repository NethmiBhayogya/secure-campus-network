# Day 06 – Access Control Lists (ACLs)

## Overview

On Day 6, I implemented Extended Access Control Lists (ACLs) to improve network security in the Secure University Campus Network.

The main objective was to control communication between different VLANs and restrict unauthorized access to sensitive university network resources while allowing required services to operate normally.

## Objectives

- Implement Extended ACLs on the main and branch campus routers.
- Restrict guest Wi-Fi users from accessing internal campus networks.
- Prevent student networks from accessing the ADMIN and FINANCE networks.
- Allow students to access the university web server using HTTP and HTTPS.
- Preserve DHCP functionality and normal gateway communication.
- Verify the ACL configurations through connectivity tests.

## ACL Implementation

I configured four Extended ACLs across the two campus routers.

| Router | ACL Name | Applied Interface | Direction |
|---|---|---|---|
| R1-MAIN | GUEST_MAIN_IN | G0/0.60 | Inbound |
| R1-MAIN | STUDENT_MAIN_IN | G0/0.30 | Inbound |
| R2-BRANCH | GUEST_BRANCH_IN | G0/0.60 | Inbound |
| R2-BRANCH | STUDENT_BRANCH_IN | G0/0.30 | Inbound |

### 1. Guest Network Restrictions

Configured `GUEST_MAIN_IN` and `GUEST_BRANCH_IN` to:

- Allow DHCP requests.
- Allow communication with the guest network's default gateway.
- Block access to internal private campus networks (`10.0.0.0/8`).
- Permit other destinations according to the ACL rules.

This prevents guest users from accessing internal university resources, including the ADMIN, FINANCE and server networks.

### 2. Student Network Restrictions

Configured `STUDENT_MAIN_IN` and `STUDENT_BRANCH_IN` to:

- Allow DHCP requests.
- Allow HTTP (TCP port 80) access to the university web server.
- Allow HTTPS (TCP port 443) access to the university web server.
- Allow ICMP communication with the web server for connectivity testing.
- Block access to the ADMIN network (`10.10.10.0/24`).
- Block access to the FINANCE network (`10.10.20.0/24`).
- Permit other traffic from the student subnet.

**University Web Server:** `10.10.50.20`

## Verification and Testing

After applying the ACLs, I performed connectivity tests from the main and branch campus devices.

| Test | Expected Result | Actual Result |
|---|---|---|
| Main guest to gateway | Allowed | Successful |
| Main guest to ADMIN | Blocked | Blocked |
| Main guest to FINANCE | Blocked | Blocked |
| Main guest to web server | Blocked | Blocked |
| Branch guest to gateway | Allowed | Successful |
| Branch guest to ADMIN | Blocked | Blocked |
| Branch guest to FINANCE | Blocked | Blocked |
| Branch guest to web server | Blocked | Blocked |
| Main student to gateway | Allowed | Successful |
| Main student to web server | Allowed | Successful |
| Main student to ADMIN | Blocked | Blocked |
| Main student to FINANCE | Blocked | Blocked |
| Branch student to gateway | Allowed | Successful |
| Branch student to web server | Allowed | Successful |
| Branch student to ADMIN | Blocked | Blocked |
| Branch student to FINANCE | Blocked | Blocked |

### Web Server Access

Tested HTTP access from both main and branch student devices using:

`http://10.10.50.20`

Both devices successfully loaded the Cisco Packet Tracer default web page.

### DHCP Verification

Verified that devices retained their correct DHCP configurations after ACL implementation.

| Device | IPv4 Address | Default Gateway |
|---|---|---|
| Main Guest Laptop | 10.10.60.100 | 10.10.60.1 |
| Branch Guest Laptop | 10.10.80.102 | 10.10.80.1 |
| Main Student PC | 10.10.30.101 | 10.10.30.1 |
| Branch Student PC | 10.10.70.100 | 10.10.70.1 |

Subnet mask for all devices: `255.255.255.0`

## ACL Verification Commands

The following commands were used to verify the ACL configurations and interface assignments:

```cisco
show access-lists
show ip interface gigabitEthernet 0/0.30
show ip interface gigabitEthernet 0/0.60
show running-config
```

All four ACLs were confirmed on their intended router subinterfaces. All four subinterfaces were UP/UP, and their DHCP helper addresses remained configured.

## What I Learned

Through this implementation, I gained practical experience in:

- Understanding how Extended ACLs control network traffic.
- Using standard source and destination IP matching.
- Filtering traffic based on TCP, UDP and ICMP protocols.
- Applying ACLs inbound on router subinterfaces.
- Protecting sensitive network segments from unauthorized access.
- Testing permitted and denied network traffic.
- Understanding how ACL rules are processed in sequence.

## Outcome

Successfully implemented and tested Extended ACLs on both main and branch campus routers.

The implementation introduced traffic restrictions for guest and student networks while maintaining the required DHCP functionality and student access to the university web server.

**Day 06 – Access Control Lists: Completed.**

---

*This documentation is part of my Secure University Campus Network project, developed using Cisco Packet Tracer.*
