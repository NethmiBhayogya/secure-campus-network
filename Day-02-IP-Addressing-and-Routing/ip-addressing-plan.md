# IP Addressing Plan

## Project Overview
This project simulates a university network with a main campus and a branch campus using Cisco Packet Tracer.

The network uses VLANs to separate departments and static routing to enable communication between campuses.

## Main Campus VLANs

| VLAN ID | VLAN Name | Network | Default Gateway |
|---|---|---|---|
| 10 | ADMIN | 10.10.10.0/24 | 10.10.10.1 |
| 20 | FINANCE | 10.10.20.0/24 | 10.10.20.1 |
| 30 | STUDENTS | 10.10.30.0/24 | 10.10.30.1 |
| 40 | IT | 10.10.40.0/24 | 10.10.40.1 |
| 50 | SERVERS | 10.10.50.0/24 | 10.10.50.1 |
| 60 | GUEST_WIFI | 10.10.60.0/24 | 10.10.60.1 |

## Branch Campus VLANs

| VLAN ID | VLAN Name | Network | Default Gateway |
|---|---|---|---|
| 30 | STUDENTS | 10.10.70.0/24 | 10.10.70.1 |
| 60 | GUEST_WIFI | 10.10.80.0/24 | 10.10.80.1 |

## Router-to-Router Link

| Router | Interface | IP Address |
|---|---|---|
| R1-MAIN | GigabitEthernet0/1 | 10.10.254.1/30 |
| R2-BRANCH | GigabitEthernet0/1 | 10.10.254.2/30 |

## End-Device IP Addresses

| Device | IP Address | Default Gateway |
|---|---|---|
| PC1-ADMIN | 10.10.10.10 | 10.10.10.1 |
| PC2-FINANCE | 10.10.20.10 | 10.10.20.1 |
| PC3-STUDENT | 10.10.30.10 | 10.10.30.1 |
| PC4-STUDENT | 10.10.30.11 | 10.10.30.1 |
| PC5-IT | 10.10.40.10 | 10.10.40.1 |
| PC6-BRANCH | 10.10.70.10 | 10.10.70.1 |
| SERVER1-DHCP | 10.10.50.10 | 10.10.50.1 |
| SERVER2-WEB | 10.10.50.20 | 10.10.50.1 |
| LAPTOP1-GUEST | 10.10.60.10 | 10.10.60.1 |
| LAPTOP2-STAFF | 10.10.80.10 | 10.10.80.1 |

## Verification Results

The following tests were successful:

- Inter-VLAN communication between ADMIN and FINANCE.
- Main-campus PC to branch-campus PC.
- Branch-campus PC to main-campus web server IP.
- Wireless communication across campuses.

All recorded tests received four replies with 0% packet loss.

**Note:** DHCP and web services still require separate configuration and testing.
