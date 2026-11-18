# TVI Enterprise Network – Step 2: IP Addressing & VLSM

## 1. Addressing strategy

The project uses the private IPv4 block `192.168.0.0/16`. The following site and service blocks are reserved:

| Area | Reserved IPv4 block |
|---|---|
| HCMC HQ | `192.168.16.0/20` |
| Hanoi R&D | `192.168.32.0/21` |
| Da Nang Logistics | `192.168.40.0/22` |
| HCMC IoT | `192.168.64.0/20` |
| Hanoi IoT | `192.168.80.0/20` |
| Da Nang IoT | `192.168.96.0/20` |
| HCMC Guest | `192.168.128.0/22` |
| Hanoi Guest | `192.168.132.0/22` |
| Da Nang Guest | `192.168.136.0/23` |
| HCMC Management | `192.168.1.0/24` |
| Hanoi Management | `192.168.2.0/24` |
| Da Nang Management | `192.168.3.0/24` |
| HQ Server Network | `192.168.48.0/24` |

## 2. IPv4 VLSM allocation

### HCMC – Headquarters

| VLAN | Name | Network/CIDR | Subnet mask | Default gateway | Usable host range | Broadcast |
|---:|---|---|---|---|---|---|
| 10 | EXECUTIVE | `192.168.16.0/24` | `255.255.255.0` | `192.168.16.1` | `192.168.16.1–192.168.16.254` | `192.168.16.255` |
| 11 | HQ-FINANCE | `192.168.17.0/23` | `255.255.254.0` | `192.168.17.1` | `192.168.17.1–192.168.18.254` | `192.168.18.255` |
| 12 | HQ-STAFF | `192.168.20.0/22` | `255.255.252.0` | `192.168.20.1` | `192.168.20.1–192.168.23.254` | `192.168.23.255` |
| 13 | HQ-DATACENTER | `192.168.48.0/24` | `255.255.255.0` | `192.168.48.1` | `192.168.48.1–192.168.48.254` | `192.168.48.255` |
| 40 | HCMC-IOT | `192.168.64.0/20` | `255.255.240.0` | `192.168.64.1` | `192.168.64.1–192.168.79.254` | `192.168.79.255` |
| 50 | HCMC-GUEST | `192.168.128.0/22` | `255.255.252.0` | `192.168.128.1` | `192.168.128.1–192.168.131.254` | `192.168.131.255` |
| 99 | MANAGEMENT | `192.168.1.0/24` | `255.255.255.0` | `192.168.1.1` | `192.168.1.1–192.168.1.254` | `192.168.1.255` |

### Hanoi – R&D

| VLAN | Name | Network/CIDR | Subnet mask | Default gateway | Usable host range | Broadcast |
|---:|---|---|---|---|---|---|
| 20 | ENGINEERING | `192.168.32.0/21` | `255.255.248.0` | `192.168.32.1` | `192.168.32.1–192.168.39.254` | `192.168.39.255` |
| 41 | HANOI-IOT | `192.168.80.0/20` | `255.255.240.0` | `192.168.80.1` | `192.168.80.1–192.168.95.254` | `192.168.95.255` |
| 50 | HANOI-GUEST | `192.168.132.0/22` | `255.255.252.0` | `192.168.132.1` | `192.168.132.1–192.168.135.254` | `192.168.135.255` |
| 99 | MANAGEMENT | `192.168.2.0/24` | `255.255.255.0` | `192.168.2.1` | `192.168.2.1–192.168.2.254` | `192.168.2.255` |

### Da Nang – Logistics

| VLAN | Name | Network/CIDR | Subnet mask | Default gateway | Usable host range | Broadcast |
|---:|---|---|---|---|---|---|
| 30 | LOGISTICS | `192.168.40.0/22` | `255.255.252.0` | `192.168.40.1` | `192.168.40.1–192.168.43.254` | `192.168.43.255` |
| 42 | DANANG-IOT | `192.168.96.0/20` | `255.255.240.0` | `192.168.96.1` | `192.168.96.1–192.168.111.254` | `192.168.111.255` |
| 50 | DANANG-GUEST | `192.168.136.0/23` | `255.255.254.0` | `192.168.136.1` | `192.168.136.1–192.168.137.254` | `192.168.137.255` |
| 99 | MANAGEMENT | `192.168.3.0/24` | `255.255.255.0` | `192.168.3.1` | `192.168.3.1–192.168.3.254` | `192.168.3.255` |

The three IoT subnets provide 4,094 usable IPv4 addresses each, for a total of 12,282 usable addresses. This exceeds the project target of 10,000 IoT endpoints.

## 3. IPv6 addressing plan

The documentation prefix `2001:DB8::/32` is used for lab and documentation purposes. Each site receives a `/48`; each VLAN receives a `/64`.

### Site prefixes

| Site | IPv6 site prefix |
|---|---|
| HCMC | `2001:DB8:10::/48` |
| Hanoi | `2001:DB8:20::/48` |
| Da Nang | `2001:DB8:30::/48` |

### HCMC

| VLAN | Name | IPv6 subnet | Planned gateway |
|---:|---|---|---|
| 10 | EXECUTIVE | `2001:DB8:10:10::/64` | `2001:DB8:10:10::1` |
| 11 | HQ-FINANCE | `2001:DB8:10:11::/64` | `2001:DB8:10:11::1` |
| 12 | HQ-STAFF | `2001:DB8:10:12::/64` | `2001:DB8:10:12::1` |
| 13 | HQ-DATACENTER | `2001:DB8:10:13::/64` | `2001:DB8:10:13::1` |
| 40 | HCMC-IOT | `2001:DB8:10:40::/64` | `2001:DB8:10:40::1` |
| 50 | HCMC-GUEST | `2001:DB8:10:50::/64` | `2001:DB8:10:50::1` |
| 99 | MANAGEMENT | `2001:DB8:10:99::/64` | `2001:DB8:10:99::1` |

### Hanoi

| VLAN | Name | IPv6 subnet | Planned gateway |
|---:|---|---|---|
| 20 | ENGINEERING | `2001:DB8:20:20::/64` | `2001:DB8:20:20::1` |
| 41 | HANOI-IOT | `2001:DB8:20:41::/64` | `2001:DB8:20:41::1` |
| 50 | HANOI-GUEST | `2001:DB8:20:50::/64` | `2001:DB8:20:50::1` |
| 99 | MANAGEMENT | `2001:DB8:20:99::/64` | `2001:DB8:20:99::1` |

### Da Nang

| VLAN | Name | IPv6 subnet | Planned gateway |
|---:|---|---|---|
| 30 | LOGISTICS | `2001:DB8:30:30::/64` | `2001:DB8:30:30::1` |
| 42 | DANANG-IOT | `2001:DB8:30:42::/64` | `2001:DB8:30:42::1` |
| 50 | DANANG-GUEST | `2001:DB8:30:50::/64` | `2001:DB8:30:50::1` |
| 99 | MANAGEMENT | `2001:DB8:30:99::/64` | `2001:DB8:30:99::1` |

## 4. WAN point-to-point addressing

The block `192.168.240.0/24` is reserved for WAN point-to-point links. Each listed link uses a `/30`.

| Link | IPv4 network | Endpoint A | Endpoint B |
|---|---|---|---|
| HCMC–Hanoi | `192.168.240.0/30` | `192.168.240.1` | `192.168.240.2` |
| HCMC–Da Nang | `192.168.240.4/30` | `192.168.240.5` | `192.168.240.6` |
| HCMC–ISP | `192.168.240.8/30` | `192.168.240.9` | `192.168.240.10` |

IPv6 WAN link prefixes:

| Link | IPv6 prefix | Endpoint A | Endpoint B |
|---|---|---|---|
| HCMC–Hanoi | `2001:DB8:FFFF:1::/127` | `2001:DB8:FFFF:1::` | `2001:DB8:FFFF:1::1` |
| HCMC–Da Nang | `2001:DB8:FFFF:2::/127` | `2001:DB8:FFFF:2::` | `2001:DB8:FFFF:2::1` |
| HCMC–ISP | `2001:DB8:FFFF:3::/127` | `2001:DB8:FFFF:3::` | `2001:DB8:FFFF:3::1` |

These WAN assignments are a logical addressing proposal. Confirm the actual router-to-router links and interface names against the final lab topology before applying configurations.

## 5. Address allocation rules

1. The `.1` address in each subnet is reserved as the planned default gateway.
2. If HSRP/VRRP is deployed, `.1` is the virtual gateway address; physical Layer 3 switch/router addresses must use other available addresses in that subnet.
3. Reserve infrastructure addresses for routers, Layer 3 switches, servers, printers, access points, and network management.
4. Exclude gateway and infrastructure reservations from DHCP pools.
5. Use static addressing or DHCP reservations for infrastructure and management devices.
6. Use `/64` prefixes for end-user IPv6 VLANs. SLAAC or DHCPv6 can be selected according to device support and lab requirements.
7. Never assign a network address or IPv4 broadcast address to a host.
8. Do not reuse a subnet across different VLANs or sites.

## 6. Implementation notes

- The IPv4 plan is hierarchical and uses the previously agreed `192.168.0.0/16` private address space.
- The three IoT `/20` networks provide 12,282 usable IPv4 host addresses in total.
- The server network is reserved as `192.168.48.0/24` and is associated with HCMC VLAN 13.
- The gateway addresses are planned values. They must be implemented consistently on the Layer 3 gateway devices.
- The WAN table assumes the three listed point-to-point links exist. If the physical topology differs, retain the reserved WAN block but adjust individual link assignments.
- `2001:DB8::/32` is a documentation prefix, not a globally routable production allocation.
