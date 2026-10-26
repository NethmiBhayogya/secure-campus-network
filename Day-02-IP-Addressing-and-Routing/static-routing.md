# Static Routing Configuration

## Overview
Static routing connects the main campus and branch campus through two routers.

## Router-to-Router Link

| Router | Interface | IP Address |
|---|---|---|
| R1-MAIN | GigabitEthernet0/1 | 10.10.254.1/30 |
| R2-BRANCH | GigabitEthernet0/1 | 10.10.254.2/30 |

## Routes on R1-MAIN

The main-campus router forwards traffic for the branch networks to R2-BRANCH.

| Destination Network | Next-Hop Address |
|---|---|
| 10.10.70.0/24 | 10.10.254.2 |
| 10.10.80.0/24 | 10.10.254.2 |

## Routes on R2-BRANCH

The branch router forwards traffic for the main-campus networks to R1-MAIN.

| Destination Network | Next-Hop Address |
|---|---|
| 10.10.10.0/24 | 10.10.254.1 |
| 10.10.20.0/24 | 10.10.254.1 |
| 10.10.30.0/24 | 10.10.254.1 |
| 10.10.40.0/24 | 10.10.254.1 |
| 10.10.50.0/24 | 10.10.254.1 |
| 10.10.60.0/24 | 10.10.254.1 |

## Verification

The following connectivity tests passed:

- PC1-ADMIN to PC2-FINANCE.
- PC1-ADMIN to PC6-BRANCH.
- PC6-BRANCH to SERVER2-WEB.

Each test received four replies with 0% packet loss.

## Verification Commands

Run these commands on the routers:

```text
show ip route
show ip interface brief
```

The routing table should show the connected networks and configured static routes.

**Note:** This project currently uses static routing. Dynamic routing can be explored as a future enhancement.
