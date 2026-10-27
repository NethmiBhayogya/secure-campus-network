# Day 3 — DHCP Configuration and Testing

## 1. Overview

On Day 3, I configured Dynamic Host Configuration Protocol (DHCP) for the Secure University Campus Network project using Cisco Packet Tracer.

The goal was to allow client devices at the main campus and branch campus to obtain their IPv4 addresses automatically from a centralized DHCP server.

## 2. Objectives

- Configure DHCP pools for the required client networks.
- Configure DHCP relay on both campus routers.
- Assign IP addresses automatically to client devices.
- Verify DHCP functionality across both campuses.
- Test connectivity between VLANs, campuses, and wireless clients.

## 3. Network Topology

The network consists of a main campus and a branch campus connected through two routers.

- **R1-MAIN:** Main-campus router.
- **R2-BRANCH:** Branch-campus router.
- **SERVER1-DHCP:** Central DHCP server.
- **PCs and laptops:** DHCP clients in different networks.

The DHCP server uses the static IP address `10.10.50.10` and default gateway `10.10.50.1`.

## 4. DHCP Addressing Plan

The following DHCP pools were configured on SERVER1-DHCP.

| DHCP Pool | Network | Default Gateway | Starting IP |
|---|---|---|---|
| ADMIN_POOL | `10.10.10.0/24` | `10.10.10.1` | `10.10.10.100` |
| FINANCE_POOL | `10.10.20.0/24` | `10.10.20.1` | `10.10.20.100` |
| STUDENTS_MAIN_POOL | `10.10.30.0/24` | `10.10.30.1` | `10.10.30.100` |
| IT_POOL | `10.10.40.0/24` | `10.10.40.1` | `10.10.40.100` |
| GUEST_MAIN_POOL | `10.10.60.0/24` | `10.10.60.1` | `10.10.60.100` |
| STUDENTS_BRANCH_POOL | `10.10.70.0/24` | `10.10.70.1` | `10.10.70.100` |
| GUEST_BRANCH_POOL | `10.10.80.0/24` | `10.10.80.1` | `10.10.80.100` |

**Subnet mask:** `255.255.255.0`

The server network (VLAN 50) uses static IP addressing for the servers.

## 5. DHCP Server Configuration

DHCP was enabled on SERVER1-DHCP through the Cisco Packet Tracer interface.

**Configuration steps:**

1. Open SERVER1-DHCP.
2. Select **Services → DHCP**.
3. Turn the DHCP service ON.
4. Create the seven DHCP pools listed in the addressing plan.
5. Configure each pool's default gateway, subnet mask, starting IP address, and maximum number of users.

## 6. DHCP Relay Configuration

Since the DHCP server is located on a different network from most clients, DHCP relay was configured on the routers using the `ip helper-address` command.

### R1-MAIN Configuration

```cisco
enable
configure terminal

interface gigabitEthernet0/0.10
ip helper-address 10.10.50.10
exit

interface gigabitEthernet0/0.20
ip helper-address 10.10.50.10
exit

interface gigabitEthernet0/0.30
ip helper-address 10.10.50.10
exit

interface gigabitEthernet0/0.40
ip helper-address 10.10.50.10
exit

interface gigabitEthernet0/0.60
ip helper-address 10.10.50.10
exit

end
write memory
```

### R2-BRANCH Configuration

```cisco
enable
configure terminal

interface gigabitEthernet0/0.30
ip helper-address 10.10.50.10
exit

interface gigabitEthernet0/0.60
ip helper-address 10.10.50.10
exit

end
write memory
```

VLAN 50 on R1-MAIN does not require a DHCP relay because the DHCP server is directly connected to that network.

## 7. Client DHCP Configuration

Client devices were configured to obtain their IPv4 settings automatically.

**Steps:**

1. Open a client device in Packet Tracer.
2. Select **Desktop → IP Configuration**.
3. Click **DHCP**.
4. Verify the assigned IP address, subnet mask, and default gateway.

The server and access points retained their static IP addresses.

### Verified DHCP Assignments

| Client | Assigned IP | Default Gateway |
|---|---|---|
| PC1-ADMIN | `10.10.10.100` | `10.10.10.1` |
| PC6-BRANCH | `10.10.70.100` | `10.10.70.1` |

The remaining client devices also successfully obtained their IP addresses through DHCP.

## 8. Connectivity Testing

Connectivity was tested using the `ping` command from the Packet Tracer command prompt.

### Test 1: Inter-VLAN Connectivity

**Source:** PC1-ADMIN

**Destination:** PC2-FINANCE

```text
ping 10.10.20.100
```

**Result:** 4 packets sent, 4 received, 0% packet loss.

This confirmed connectivity between the Admin and Finance networks.

### Test 2: Inter-Campus Connectivity

**Source:** PC1-ADMIN

**Destination:** PC6-BRANCH

```text
ping 10.10.70.100
```

**Result:** 4 packets sent, 4 received, 0% packet loss.

This confirmed connectivity between the main campus and branch campus.

### Test 3: Wireless Connectivity

**Source:** LAPTOP1-GUEST

**Destination:** LAPTOP2-STAFF

```text
ping 10.10.80.100
```

**Result:** 4 packets sent, 4 received, 0% packet loss.

This confirmed connectivity between the two wireless clients across the campus networks.

## 9. Results

The following tasks were completed:

- DHCP was enabled on the centralized DHCP server.
- Seven DHCP pools were configured.
- DHCP relay was configured on both routers.
- Client devices successfully obtained IPv4 configurations automatically.
- Inter-VLAN connectivity was verified.
- Inter-campus connectivity was verified.
- Wireless cross-campus connectivity was verified.

All three final connectivity tests completed with **0% packet loss**.

## 10. Screenshots

The following screenshots document the configuration and testing process.

Save the screenshots in the `screenshots/` directory of the repository.

- `DHCP-Pools.png` — DHCP pool configuration.
- `DHCP-Client-IP.png` — DHCP-assigned client IP configuration.
- `Inter-VLAN-Ping.png` — Successful inter-VLAN ping.
- `Inter-Campus-Ping.png` — Successful inter-campus ping.
- `Wireless-Ping.png` — Successful wireless connectivity test.

## 11. What I Learned

Through this stage, I gained practical experience with:

- Understanding DHCP and automatic IPv4 address assignment.
- Creating DHCP pools for multiple subnets.
- Configuring DHCP relay using `ip helper-address`.
- Understanding the role of default gateways in communication between networks.
- Testing network connectivity using `ping`.
- Troubleshooting initial ping timeouts and verifying connectivity again.

## 12. Day 3 Status

**Status: Core configuration and testing completed.**

DHCP configuration and connectivity testing were successful in Cisco Packet Tracer. The screenshots and documentation will be maintained in the GitHub repository as part of the project portfolio.
