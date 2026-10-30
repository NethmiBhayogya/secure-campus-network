# Day 05 – SSH and Port Security Configuration

## Overview

On Day 05, I focused on improving the security of the Secure University Campus Network by configuring Secure Shell (SSH) for remote device management and implementing switch port security on user-facing access ports.

## 1. SSH Configuration

Configured SSH Version 2 on all six network devices to enable secure remote management.

**Devices configured:**
- R1-MAIN
- R2-BRANCH
- SW1-CORE
- SW2-ADMIN
- SW3-FACULTY
- SW4-BRANCH

**Configuration features:**
- Configured the domain name: `securecampus.local`
- Created a local user account named `netadmin`
- Generated RSA key pairs
- Enabled SSH Version 2
- Configured VTY lines with local authentication
- Allowed SSH connections only on VTY lines
- Configured privilege level 15 for the administrator account

## 2. Switch Management IP Addresses

Configured management IP addresses on the switches to allow remote administration.

| Switch | Management VLAN | Management IP |
|---|---|---|
| SW1-CORE | VLAN 10 | 10.10.10.3 |
| SW2-ADMIN | VLAN 10 | 10.10.10.2 |
| SW3-FACULTY | VLAN 10 | 10.10.10.4 |
| SW4-BRANCH | VLAN 30 | 10.10.70.2 |

Verified management connectivity using ICMP ping tests.

## 3. SSH Verification

Tested SSH remote login from the PCs to the network devices.

**Verification commands:**

```cisco
show ip ssh
show ssh
show users
show privilege
```

Successfully verified SSH access on all six devices.

The verification confirmed:
- SSH Version 2 was enabled.
- Remote SSH sessions were established.
- The `netadmin` account was authenticated.
- Privilege level 15 was available.

## 4. Switch Port Security Configuration

Implemented port security on six user-facing switch access ports to restrict unauthorized device connections.

**Configured ports:**

| Switch | Interface | Connected Device |
|---|---|---|
| SW2-ADMIN | Fa0/1 | PC1-ADMIN |
| SW2-ADMIN | Fa0/2 | PC2-FINANCE |
| SW3-FACULTY | Fa0/1 | PC3-STUDENT |
| SW3-FACULTY | Fa0/2 | PC4-STUDENT |
| SW3-FACULTY | Fa0/3 | PC5-IT |
| SW4-BRANCH | Fa0/1 | PC6-BRANCH |

**Security features implemented:**
- Enabled switch port security.
- Limited each secured port to one MAC address.
- Enabled sticky MAC address learning.
- Configured violation mode as shutdown.
- Verified learned MAC addresses and port security status.

**Verification commands:**

```cisco
show port-security
show port-security interface fa0/1
show port-security address
```

All six configured user-facing ports successfully learned their connected device MAC addresses.

Trunk links and access point connections were left unchanged.

## 5. Project Progress

**Completed on Day 05:**
- SSH Version 2 configuration on six network devices.
- Remote SSH login testing.
- Switch management IP configuration.
- Port security implementation on six access ports.
- Verification of SSH sessions and port security status.

## Screenshots

The screenshots in this folder demonstrate SSH configuration, successful remote login sessions, switch management connectivity, and port security verification.

## Next Steps

- Configure and test Access Control Lists (ACLs).
- Apply network access restrictions based on VLANs.
- Perform additional security and connectivity tests.
- Complete final project documentation and verification.
