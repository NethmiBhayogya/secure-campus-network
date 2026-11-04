# Day 07 — Final Network Verification and Testing

## Overview

The final day focused on verifying the complete Secure University Campus Network. I reviewed the configurations of all routers and switches, checked network security settings, performed end-to-end connectivity tests, and confirmed that the implemented network policies were working as expected.

## 1. Configuration Verification

Verified the configurations of all six network devices:

**Routers**
- R1-MAIN
- R2-BRANCH

**Switches**
- SW1-CORE
- SW2-ADMIN
- SW3-FACULTY
- SW4-BRANCH

The following configurations were checked:

- VLAN configurations and port assignments
- Trunk links between network devices
- Router subinterfaces and IP addressing
- Static routing between the main and branch campuses
- DHCP relay configurations
- Extended Access Control Lists (ACLs)
- SSH version 2 remote management
- Port security on selected access ports

## 2. Network Connectivity Testing

End-to-end connectivity tests were performed to verify communication between the main and branch campuses.

| Test | Expected Result | Status |
|---|---|---|
| Main-campus student to branch-campus student | Successful communication | Passed |
| Branch-campus student to main-campus student | Successful communication | Passed |
| Branch student to main-campus web server | Successful communication | Passed |
| Main-campus ADMIN to branch student | Restricted by ACL policy | Passed |

## 3. Web Server Verification

The university web server (`10.10.50.20`) was tested from the branch-campus student computer.

| Test | Result |
|---|---|
| ICMP (Ping) | Successful |
| HTTP (TCP Port 80) | Successful |
| HTTPS (TCP Port 443) | Successful |

The Cisco Packet Tracer welcome page loaded successfully using both HTTP and HTTPS.

## 4. Security Policy Verification

The configured Extended ACLs were tested to confirm that the intended access restrictions were enforced.

- Guest Wi-Fi users were restricted from accessing internal campus networks.
- Guest users could still communicate with their default gateway and obtain IP addresses through DHCP.
- Main and branch student networks could access the university web server through HTTP and HTTPS.
- Student networks were restricted from accessing the ADMIN and FINANCE networks.
- Communication between main-campus and branch-campus student networks was successfully tested.

## 5. Device Configuration Backup

The running configurations of all six network devices were saved to startup configurations.

Command used:

```cisco
copy running-config startup-config
```

All six devices returned the `[OK]` confirmation.

## 6. Final Project Outcome

The Secure University Campus Network was successfully configured and verified in Cisco Packet Tracer.

The project demonstrates practical experience with:

- VLANs and trunking
- Inter-VLAN routing using Router-on-a-Stick
- Static routing
- DHCP and DHCP relay
- HTTP and HTTPS services
- SSH remote device management
- Switch port security
- Extended Access Control Lists (ACLs)
- Network connectivity and security testing

## Conclusion

Completing this project helped me strengthen my understanding of enterprise network design, configuration, troubleshooting, and basic network security.

It also gave me practical experience in connecting multiple campus networks and implementing access restrictions using Cisco networking technologies.

**Project Status: Configuration and final verification completed.**
