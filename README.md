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

---

### Day 05 Verification Screenshots

#### SSH Remote Management Screenshots
1. **R1-MAIN SSH Verification:**  
   ![R1-MAIN SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-r1-main.png)
2. **R2-BRANCH SSH Verification:**  
   ![R2-BRANCH SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-r2-branch.png)
3. **SW1-CORE SSH Verification:**  
   ![SW1-CORE SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-sw1-core.png)
4. **SW2-ADMIN SSH Verification:**  
   ![SW2-ADMIN SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-sw2-admin.png)
5. **SW3-FACULTY SSH Verification:**  
   ![SW3-FACULTY SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-sw3-faculty.png)
6. **SW4-BRANCH SSH Verification:**  
   ![SW4-BRANCH SSH](Day-05-SSH-and-Port-Security/screenshots/ssh-sw4-branch.png)

#### Switch Port Security Screenshots
1. **SW2-ADMIN Port Security:**  
   ![SW2-ADMIN Port Security](Day-05-SSH-and-Port-Security/screenshots/port-security-sw2.png)
2. **SW3-FACULTY Port Security Summary:**  
   ![SW3-FACULTY Port Security Summary](Day-05-SSH-and-Port-Security/screenshots/port-security-sw3-summary.png)
3. **SW3-FACULTY Port Security Interface Details:**  
   ![SW3-FACULTY Port Security Details](Day-05-SSH-and-Port-Security/screenshots/port-security-sw3-details.png)
4. **SW4-BRANCH Port Security:**  
   ![SW4-BRANCH Port Security](Day-05-SSH-and-Port-Security/screenshots/port-security-sw4.png)

**Day 05 Status:** Completed

---

### Project Summary & Status

### What I Learned
Through this project, I gained practical experience in:
- Designing a campus network with multiple departments and locations.
- Creating VLANs and configuring trunk links.
- Implementing inter-VLAN routing using router-on-a-stick.
- Configuring IPv4 addressing and static routing.
- Setting up DHCP pools and DHCP relay.
- Configuring and testing an HTTP web server.
- Enabling secure remote management using SSH Version 2.
- Configuring switch port security and sticky MAC address learning.
- Verifying network configurations using Cisco IOS commands.
- Troubleshooting connectivity and documenting network implementations.

### Remaining Tasks
- [ ] Configure and test Access Control Lists (ACLs).
- [ ] Perform additional connectivity and security tests.
- [ ] Complete the final project documentation.
- [ ] Perform final network verification.
- [ ] Upload the completed Cisco Packet Tracer `.pkt` file.

### Project Goals
- Develop practical Cisco networking and troubleshooting skills.
- Understand how VLANs, routing, DHCP, and network security work together.
- Build a documented networking portfolio for internship applications.
- Gain hands-on experience with networking concepts covered in CCNA studies.

### Project Status
**Completed:**
- Topology design and VLAN configuration.
- IPv4 addressing and subnetting.
- Router-on-a-stick inter-VLAN routing.
- Static routing between the campuses.
- DHCP pools and DHCP relay.
- DHCP client verification.
- Connectivity testing.
- HTTP web server configuration and testing.
- SSH Version 2 configuration on all six network devices.
- Switch port security on six PC-facing access ports.
- SSH and port security verification.

**Next Stage:** Access Control List (ACL) configuration, additional security testing, and final project verification.

*This project is being developed step by step using Cisco Packet Tracer. Configuration files, documentation, screenshots, and test results are added as each stage is completed.*



