# Secure University Campus Network

A simulated university campus network built using Cisco Packet Tracer to gain hands-on experience with enterprise networking concepts. The project represents a main campus and a branch campus, with a focus on network segmentation, connectivity, and security.

## Network Topology

The diagram below illustrates the planned network design for the main and branch campuses, including the proposed VLAN structure.

![Secure University Campus Network Topology](Day-01-Topology-Design/campus-topology.png.png)

*Note: IP addressing, inter-VLAN routing, DHCP, campus routing, and security configurations will be implemented and tested in upcoming stages.*

## Project Objectives

Design and implement a university campus network using Cisco Packet Tracer.

Separate departments using VLANs.

Configure trunk links and router-on-a-stick inter-VLAN routing.

Implement IPv4 addressing and subnetting.

Connect the main and branch campuses using static routing.

Configure network services such as DHCP and a web server.

Improve network security using SSH, switch port security, and Access Control Lists (ACLs).

Test connectivity and document the implementation.

## Technology Stack

Cisco Packet Tracer

IPv4 Addressing and Subnetting

VLANs and Trunking

Router-on-a-Stick Inter-VLAN Routing

Static Routing

DHCP (planned)

Web Server Configuration (planned)

SSH (planned)

Switch Port Security (planned)

Wireless LAN (WLAN)

Access Control Lists (ACLs) (planned)

## Network Design

The network contains two locations:

Main Campus: ADMIN, FINANCE, STUDENTS, IT, SERVERS, and GUEST_WIFI VLANs.

Branch Campus: STUDENTS and GUEST_WIFI VLANs, using separate IP subnets from the main campus.

The routers are connected through a point-to-point Ethernet link using the 10.10.254.0/30 network. Static routes allow the two campuses to communicate.

## VLAN and IP Addressing Plan

### Main Campus

| VLAN ID | VLAN Name | Network Address | Default Gateway |
|:---:|---|---|---|
| 10 | ADMIN | `10.10.10.0/24` | `10.10.10.1` |
| 20 | FINANCE | `10.10.20.0/24` | `10.10.20.1` |
| 30 | STUDENTS | `10.10.30.0/24` | `10.10.30.1` |
| 40 | IT | `10.10.40.0/24` | `10.10.40.1` |
| 50 | SERVERS | `10.10.50.0/24` | `10.10.50.1` |
| 60 | GUEST_WIFI | `10.10.60.0/24` | `10.10.60.1` |

### Branch Campus

| VLAN ID | VLAN Name | Network Address | Default Gateway |
|:---:|---|---|---|
| 30 | STUDENTS | `10.10.70.0/24` | `10.10.70.1` |
| 60 | GUEST_WIFI | `10.10.80.0/24` | `10.10.80.1` |

### Router-to-Router Link

| Router | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| R1-MAIN | GigabitEthernet0/1 | `10.10.254.1` | `255.255.255.252` |
| R2-BRANCH | GigabitEthernet0/1 | `10.10.254.2` | `255.255.255.252` |

## End-Device IP Addressing

| Device | IP Address | Default Gateway |
|---|---|---|
| PC1-ADMIN | `10.10.10.10` | `10.10.10.1` |
| PC2-FINANCE | `10.10.20.10` | `10.10.20.1` |
| PC3-STUDENT | `10.10.30.10` | `10.10.30.1` |
| PC4-STUDENT | `10.10.30.11` | `10.10.30.1` |
| PC5-IT | `10.10.40.10` | `10.10.40.1` |
| PC6-BRANCH | `10.10.70.10` | `10.10.70.1` |
| SERVER1-DHCP | `10.10.50.10` | `10.10.50.1` |
| SERVER2-WEB | `10.10.50.20` | `10.10.50.1` |
| AP1-MAIN | `10.10.60.2` | `10.10.60.1` |
| LAPTOP1-GUEST | `10.10.60.10` | `10.10.60.1` |
| AP2-BRANCH | `10.10.80.2` | `10.10.80.1` |
| LAPTOP2-STAFF | `10.10.80.10` | `10.10.80.1` |


## Day 1 — Topology Design and VLAN Configuration

### Completed Tasks

- Designed the initial main-campus and branch-campus topology.
- Added and named routers, switches, PCs, servers, access points, and laptops.
- Connected the network devices.
- Created the main-campus VLAN plan.
- Created VLANs on the switches.
- Configured relevant access ports and trunk links.
- Prepared the network for IP addressing and routing.

### VLAN Configuration

- VLAN 10 — ADMIN
- VLAN 20 — FINANCE
- VLAN 30 — STUDENTS
- VLAN 40 — IT
- VLAN 50 — SERVERS
- VLAN 60 — GUEST_WIFI

## Day 2 — IP Addressing and Routing

### Completed Tasks

- Configured IPv4 addresses and default gateways for end devices.
- Configured the point-to-point link between R1-MAIN and R2-BRANCH.
- Configured router subinterfaces for inter-VLAN routing.
- Configured static routes between the main and branch campuses.
- Verified default gateway connectivity for the tested devices.
- Tested inter-VLAN communication.
- Tested communication between the main and branch campuses.
- Verified branch-campus connectivity to the main-campus server IP address.
- Tested wireless connectivity across the campuses.

### Connectivity Test Results

The following ping tests completed successfully with four replies and `0%` packet loss.

| Test | Source | Destination | Result |
|---|---|---|:---:|
| Inter-VLAN routing | PC1-ADMIN | PC2-FINANCE | PASS |
| Main-to-branch connectivity | PC1-ADMIN | PC6-BRANCH | PASS |
| Branch-to-server connectivity | PC6-BRANCH | SERVER2-WEB | PASS |
| Wireless cross-campus connectivity | LAPTOP1-GUEST | LAPTOP2-STAFF | PASS |

## Connectivity Test Screenshots

Upload the screenshots to the Day-02-IP-Addressing-and-Routing/ folder to display them here.

Inter-VLAN Routing Test
This test verifies communication between devices in different VLANs
![Inter-VLAN Routing Test](Day-02-IP-Addressing-and-Routing/inter-vlan-routing-test.png)



Main-to-Branch Connectivity
This test verifies communication between the main campus and the branch campus.
![Main-to-Branch Connectivity](Day-02-IP-Addressing-and-Routing/main-to-branch-connectivity.png)


Branch-to-Server Connectivity
This test verifies that a device in the branch campus can communicate with the main-campus server.
![Branch-to-Server Connectivity](Day-02-IP-Addressing-and-Routing/branch-to-server-connectivity.png)

## Day 3 — DHCP Configuration
### Objectives
- Configure the DHCP service on `SERVER1-DHCP`.
- Create separate DHCP pools for the required networks.
- Configure DHCP relay on the routers using `ip helper-address`.
- Obtain IP addresses automatically on client devices.
- Verify DHCP assignments and connectivity.

### DHCP Server Configuration
The DHCP service was enabled on `SERVER1-DHCP` with the static IP address `10.10.50.10/24` and default gateway `10.10.50.1`. Seven DHCP pools were created to provide addresses to clients in the main and branch campuses:

| DHCP Pool Name | Network | Default Gateway | Starting IP |
| :--- | :--- | :--- | :--- |
| `ADMIN_POOL` | 10.10.10.0/24 | 10.10.10.1 | 10.10.10.100 |
| `FINANCE_POOL` | 10.10.20.0/24 | 10.10.20.1 | 10.10.20.100 |
| `STUDENTS_MAIN_POOL` | 10.10.30.0/24 | 10.10.30.1 | 10.10.30.100 |
| `IT_POOL` | 10.10.40.0/24 | 10.10.40.1 | 10.10.40.100 |
| `GUEST_MAIN_POOL` | 10.10.60.0/24 | 10.10.60.1 | 10.10.60.100 |
| `STUDENTS_BRANCH_POOL` | 10.10.70.0/24 | 10.10.70.1 | 10.10.70.100 |
| `GUEST_BRANCH_POOL` | 10.10.80.0/24 | 10.10.80.1 | 10.10.80.100 |

*Each pool uses subnet mask `255.255.255.0`.*

### DHCP Relay Configuration
The `ip helper-address 10.10.50.10` command was configured on router subinterfaces:
- **R1-MAIN:** VLANs 10, 20, 30, 40, and 60.
- **R2-BRANCH:** VLANs 30 and 60.

### DHCP Verification Sample
| Client Device | Assigned DHCP Address | Default Gateway |
| :--- | :--- | :--- |
| PC1-ADMIN | 10.10.10.100 | 10.10.10.1 |
| PC6-BRANCH | 10.10.70.100 | 10.10.70.1 |

The other client devices were also switched to DHCP and successfully obtained their IP addresses. Servers and access points retain their static IP addresses.

# Connectivity Test Results After DHCP
| Test Source | Test Destination | Result |
| :--- | :--- | :--- |
| Inter-VLAN connectivity (PC1-ADMIN) | PC2-FINANCE | PASS |
| Main-to-branch connectivity (PC1-ADMIN) | PC6-BRANCH | PASS |
| Wireless cross-campus connectivity (LAPTOP1-GUEST) | LAPTOP2-STAFF | PASS |

All three final ping tests completed successfully with four replies and 0% packet loss.

## Day 3 Screenshots
Upload the screenshots to the Day-03-DHCP-Configuration folder using the filenames below:

1. **DHCP Pool Configuration:**
   
   ![DHCP Pool Configuration](Day-03-DHCP-Configuration/DHCP-Pools.png)

2. **DHCP Client IP Configuration:**
   
   ![DHCP Client IP Configuration](Day-03-DHCP-Configuration/DHCP-Client-IP.png)

3. **Inter-VLAN Connectivity:**
   
   ![Inter-VLAN Connectivity](Day-03-DHCP-Configuration/Inter-VLAN-Ping.png)

4. **Inter-Campus Connectivity:**
   
   ![Inter-Campus Connectivity](Day-03-DHCP-Configuration/Inter-Campus-Ping.png)

5. **Wireless Connectivity:**
    
   ![Wireless Connectivity](Day-03-DHCP-Configuration/Wireless-Ping.png)
   
## Day 4 — Web Server Configuration
### Objectives
- Configure `SERVER2-WEB` with a static IP address (`10.10.50.20`).
- Enable and customize the HTTP/HTTPS web service on `SERVER2-WEB`.
- Test web accessibility from clients across different VLANs in the main campus.
- Test cross-campus web access from the branch campus (`PC6-BRANCH`) to the main-campus web server.

### Web Server Details
- **Server Name:** `SERVER2-WEB`
- **IP Address:** `10.10.50.20`
- **Subnet Mask:** `255.255.255.0`
- **Default Gateway:** `10.10.50.1`
- **Service:** HTTP/HTTPS (Enabled)

### Day 4 Screenshots
1. **Main-Campus Web Server Test:**  
   This screenshot demonstrates that `PC1-ADMIN` can access the web server using HTTP.  
   ![Main Campus Web Test](Day-04-Web-Server-Configuration/main-campus-web-test.png)

2. **Branch-Campus Web Server Test:**  
   This screenshot demonstrates that `PC6-BRANCH` can access the main-campus web server.

   ---

## Day 05 — SSH and Port Security

### Objectives
- Configure secure remote device management using SSH Version 2.
- Configure management IP addresses on network devices.
- Enable local username authentication.
- Restrict remote management access to SSH.
- Implement switch port security on user-facing access ports.
- Verify SSH connectivity and port security configurations.

---

### 1. SSH Configuration
SSH Version 2 was configured on all six network devices to provide secure remote access for network administration.

**Devices configured:**
- `R1-MAIN`
- `R2-BRANCH`
- `SW1-CORE`
- `SW2-ADMIN`
- `SW3-FACULTY`
- `SW4-BRANCH`

#### SSH Security Features
- Configured domain name: `securecampus.local`.
- Created local administrative account with privilege level 15.
- Generated RSA key pair (1024-bit modulus).
- Enforced SSH Version 2 (`ip ssh version 2`).
- Configured VTY lines (`0 4`) with `login local` and `transport input ssh`.
- Restricted remote management exclusively to SSH.

#### Management IP Address Table
| Device | Management VLAN | Management IP Address |
| :--- | :--- | :--- |
| `R1-MAIN` | VLAN 10 | `10.10.10.1` |
| `R2-BRANCH` | VLAN 70 | `10.10.70.1` |
| `SW1-CORE` | VLAN 10 | `10.10.10.3` |
| `SW2-ADMIN` | VLAN 10 | `10.10.10.2` |
| `SW3-FACULTY` | VLAN 10 | `10.10.10.4` |
| `SW4-BRANCH` | VLAN 30 | `10.10.70.2` |

#### SSH Verification Commands
- `show ip ssh`
- `show ssh`
- `show users`
- `show privilege`

*Verification confirmed successful remote login, SSH Version 2 enforcement, and privilege level 15 allocation across all six devices.*

---

### 2. Switch Port Security
Port security was implemented on six PC-facing access ports to prevent unauthorized device access across access switches.

#### Port Security Assignment Matrix
| Switch | Interface | Connected Device | VLAN |
| :--- | :--- | :--- | :--- |
| `SW2-ADMIN` | `Fa0/1` | `PC1-ADMIN` | 10 |
| `SW2-ADMIN` | `Fa0/2` | `PC2-FINANCE` | 20 |
| `SW3-FACULTY` | `Fa0/1` | `PC3-STUDENT` | 30 |
| `SW3-FACULTY` | `Fa0/2` | `PC4-STUDENT` | 30 |
| `SW3-FACULTY` | `Fa0/3` | `PC5-IT` | 40 |
| `SW4-BRANCH` | `Fa0/1` | `PC6-BRANCH` | 30 |

#### Port Security Configuration Policy
- Activated port security (`switchport port-security`).
- Maximum MAC address limit: **1** (`switchport port-security maximum 1`).
- Dynamic MAC learning: **Sticky** (`switchport port-security mac-address sticky`).
- Violation mode: **Shutdown** (`switchport port-security violation shutdown`).

*Trunk links and wireless access point interfaces were maintained without port security.*

#### Verification Commands & Results
- `show port-security`
- `show port-security interface <interface_id>`
- `show port-security address`

**Results Summary:**
- All 6 configured access ports operational state: `Secure-up`.
- Dynamic sticky learning successfully registered connected device MAC addresses into running configuration.
- Total security violations across all monitored ports: **0**.

# Campus Network Security Implementation & Access Control Lists (ACLs)

## Day 06 — Access Control Lists (ACLs)

### Objectives
- Implement **Extended Access Control Lists (ACLs)** on the main and branch campus routers.
- Restrict guest Wi-Fi users from accessing internal campus networks.
- Prevent student networks from accessing **ADMIN** and **FINANCE** networks.
- Allow students to access the university web server.
- Maintain **DHCP functionality** and required network communication.
- Verify permitted and denied traffic through connectivity tests.

---

### 1. ACL Implementation
Four Extended ACLs were configured and applied **inbound** on the appropriate router subinterfaces.

| Router | ACL Name | Interface | Direction |
| :--- | :--- | :--- | :--- |
| **R1-MAIN** | `GUEST_MAIN_IN` | `g0/0.60` | Inbound |
| **R1-MAIN** | `STUDENT_MAIN_IN` | `g0/0.30` | Inbound |
| **R2-BRANCH** | `GUEST_BRANCH_IN` | `g0/0.60` | Inbound |
| **R2-BRANCH** | `STUDENT_BRANCH_IN` | `g0/0.30` | Inbound |

---

### 2. Guest Network Restrictions
The following ACLs were configured:
- `GUEST_MAIN_IN`
- `GUEST_BRANCH_IN`

**Security Rules:**
- **Permit** DHCP requests.
- **Permit** communication with the guest network's default gateway.
- **Deny** access to internal private campus networks (`10.0.0.0/8`).
- **Permit** other destinations according to the ACL rules.

> **Result:** Prevents guest users from accessing internal university resources, including ADMIN, FINANCE, student, IT, and server networks.

---

### 3. Student Network Restrictions
The following ACLs were configured:
- `STUDENT_MAIN_IN`
- `STUDENT_BRANCH_IN`

**Security Rules:**
- **Permit** DHCP requests.
- **Permit** HTTP traffic (TCP port 80) to the university web server.
- **Permit** HTTPS traffic (TCP port 443) to the university web server.
- **Permit** ICMP traffic to the web server for connectivity testing.
- **Deny** access to the ADMIN network (`10.10.10.0/24`).
- **Deny** access to the FINANCE network (`10.10.20.0/24`).
- **Permit** other traffic from the student subnets.

* **University Web Server IP:** `10.10.50.20`

---

### 4. Connectivity Verification
The following tests were performed after applying the ACL configurations:

| Test Source | Destination | Expected / Actual Result |
| :--- | :--- | :--- |
| **Main guest gateway access** (`LAPTOP1-GUEST`) | `10.10.60.1` | **PASS** |
| **Main guest to ADMIN** (`LAPTOP1-GUEST`) | `10.10.10.1` | **BLOCKED** |
| **Main guest to FINANCE** (`LAPTOP1-GUEST`) | `10.10.20.1` | **BLOCKED** |
| **Main guest to Web Server** (`LAPTOP1-GUEST`) | `10.10.50.20` | **BLOCKED** |
| **Branch guest gateway access** (`LAPTOP2-GUEST`) | `10.10.80.1` | **PASS** |
| **Branch guest to ADMIN** (`LAPTOP2-GUEST`) | `10.10.10.1` | **BLOCKED** |
| **Branch guest to FINANCE** (`LAPTOP2-GUEST`) | `10.10.20.1` | **BLOCKED** |
| **Branch guest to Web Server** (`LAPTOP2-GUEST`) | `10.10.50.20` | **BLOCKED** |
| **Main student gateway access** (`PC3-STUDENT`) | `10.10.30.1` | **PASS** |
| **Main student to Web Server** (`PC3-STUDENT`) | `10.10.50.20` | **PASS** |
| **Main student to ADMIN** (`PC3-STUDENT`) | `10.10.10.1` | **BLOCKED** |
| **Main student to FINANCE** (`PC3-STUDENT`) | `10.10.20.1` | **BLOCKED** |
| **Branch student gateway access** (`PC6-BRANCH`) | `10.10.70.1` | **PASS** |
| **Branch student to Web Server** (`PC6-BRANCH`) | `10.10.50.20` | **PASS** |
| **Branch student to ADMIN** (`PC6-BRANCH`) | `10.10.10.1` | **BLOCKED** |
| **Branch student to FINANCE** (`PC6-BRANCH`) | `10.10.20.1` | **BLOCKED** |

---

### 5. Web Server Access Verification
HTTP access to the university web server was tested from both main and branch student devices.

- **Web Server URL:** `http://10.10.50.20`
- **Verification:** Both student devices successfully loaded the Cisco Packet Tracer default web page.

---

### 6. DHCP Verification After ACL Implementation
DHCP configurations were checked to confirm that clients retained their correct IP addressing after ACL implementation.

| Device | Assigned IPv4 Address | Default Gateway | Subnet Mask |
| :--- | :--- | :--- | :--- |
| **Main Guest Laptop** | `10.10.60.100` | `10.10.60.1` | `255.255.255.0` |
| **Branch Guest Laptop** | `10.10.80.102` | `10.10.80.1` | `255.255.255.0` |
| **Main Student PC** | `10.10.30.101` | `10.10.30.1` | `255.255.255.0` |
| **Branch Student PC** | `10.10.70.100` | `10.10.70.1` | `255.255.255.0` |

#### ACL Verification Commands Executed:
```bash
show access-lists
show ip interface gigabitEthernet 0/0.30
show ip interface gigabitEthernet 0/0.60
show running-config
```

## Day 07 — Final Network Verification

### Objectives

- Perform final verification of all router and switch configurations.
- Verify VLANs, trunk links, IP addressing, and routing.
- Confirm SSH and switch port security configurations.
- Test end-to-end connectivity between the main and branch campuses.
- Verify ACL security policies and web server accessibility.
- Save the configurations of all network devices.

### 1. Network Device Configuration Verification

Final configuration checks were performed on all six network devices.

**Routers:**
- R1-MAIN
- R2-BRANCH

**Switches:**
- SW1-CORE
- SW2-ADMIN
- SW3-FACULTY
- SW4-BRANCH

The following configurations were verified:

- VLAN configurations and access port assignments.
- Trunk links and VLAN forwarding.
- Router subinterfaces and IP addressing.
- Static routes between the main and branch campuses.
- DHCP relay configurations.
- Extended ACLs and their application to the correct interfaces.
- SSH Version 2 remote management.
- Switch port security on six PC-facing access ports.

### 2. End-to-End Connectivity Testing

Connectivity tests were performed between the main and branch campuses.

| Test | Source | Destination | Result |
|---|---|---|---|
| Main-to-branch student connectivity | PC3-STUDENT | PC6-BRANCH | PASS |
| Branch-to-main student connectivity | PC6-BRANCH | PC3-STUDENT | PASS |
| Branch student to web server | PC6-BRANCH | SERVER2-WEB | PASS |
| Main ADMIN to branch student | PC1-ADMIN | PC6-BRANCH | BLOCKED |

Both student-to-student connectivity tests completed successfully with four replies and 0% packet loss.

The ADMIN-to-branch-student communication was blocked according to the configured student network access policy.

### 3. Web Server Verification

The main-campus web server was tested from the branch-campus student computer.

**Server Details:**
- Server Name: SERVER2-WEB
- IP Address: 10.10.50.20
- Default Gateway: 10.10.50.1

| Test | Protocol | Result |
|---|---|---|
| Connectivity to web server | ICMP | PASS |
| Web page access | HTTP (TCP Port 80) | PASS |
| Secure web page access | HTTPS (TCP Port 443) | PASS |

The Cisco Packet Tracer welcome page loaded successfully using both HTTP and HTTPS.

### 4. Final Security Verification

The configured security policies were reviewed and tested.

- Guest Wi-Fi users were restricted from accessing internal campus networks.
- Guest devices could communicate with their default gateways and obtain IP addresses through DHCP.
- Student networks could access the university web server.
- Student networks were restricted from accessing ADMIN and FINANCE networks.
- Communication between the main-campus and branch-campus student networks was successfully verified.

### 5. Device Configuration Backup

The running configurations of all six network devices were saved to their startup configurations.

Command used:

```cisco
copy running-config startup-config
```

All six devices returned the `[OK]` confirmation.

### Day 07 Outcome

Final configuration verification and end-to-end testing were completed successfully. The main and branch campus networks, network services, and configured security policies were verified using Cisco Packet Tracer.

---

## Project Summary & Status

### What I Learned

Through this project, I gained practical experience in:

- Designing a campus network with multiple departments and locations.
- Creating VLANs and configuring trunk links.
- Implementing inter-VLAN routing using Router-on-a-Stick.
- Configuring IPv4 addressing and static routing.
- Setting up DHCP pools and DHCP relay.
- Configuring and testing an HTTP/HTTPS web server.
- Enabling secure remote management using SSH Version 2.
- Configuring switch port security and sticky MAC address learning.
- Implementing Extended ACLs to control network traffic.
- Restricting unauthorized access between network segments.
- Verifying network configurations using Cisco IOS commands.
- Troubleshooting connectivity issues and documenting network implementations.

### Project Goals

- Develop practical Cisco networking and troubleshooting skills.
- Understand how VLANs, routing, DHCP, and network security work together.
- Build a documented networking portfolio for internship applications.
- Gain hands-on experience with networking concepts covered in CCNA studies.

### Project Status

**All seven implementation stages have been completed.**

| Day | Implementation Stage | Status |
|---|---|---|
| Day 01 | Topology Design and VLAN Configuration | Completed |
| Day 02 | IP Addressing and Routing | Completed |
| Day 03 | DHCP Configuration | Completed |
| Day 04 | Web Server Configuration | Completed |
| Day 05 | SSH and Port Security | Completed |
| Day 06 | Access Control Lists (ACLs) | Completed |
| Day 07 | Final Network Verification | Completed |

**Final Outcome:** Network configuration, security implementation, connectivity testing, and documentation have been completed successfully.

The final Cisco Packet Tracer (`.pkt`) project file will be included in this repository.

---

*This project was developed step by step using Cisco Packet Tracer to gain practical experience in enterprise networking, network security, and troubleshooting.*


