# Stoneleaf Systems — IP Addressing Plan

## Purpose

This document defines the IPv4 addressing strategy for the Stoneleaf Systems enterprise IT environment.

The addressing plan is designed to support:

* Approximately 40 employees
* Windows servers
* Windows 11 workstations
* Linux systems
* Network infrastructure
* Administrative systems
* Wireless devices
* Guest devices
* Lab and testing systems
* Remote-access VPN clients
* Microsoft Azure resources
* Future organizational growth

Stoneleaf Systems will use private RFC 1918 addressing throughout the internal environment.

---

# 1. Addressing Strategy

The primary Stoneleaf Systems local network will use:

```text
10.20.0.0/16
```

This provides a large private address space that can be divided into multiple `/24` networks.

Each major network function will receive its own subnet.

A standard `/24` provides:

```text
256 total addresses
254 usable host addresses
```

This is significantly more capacity than the current environment requires but keeps the addressing structure simple and scalable.

---

# 2. Network Summary

| VLAN | Network         | Purpose               |
| ---: | --------------- | --------------------- |
|   10 | `10.20.10.0/24` | Network Management    |
|   20 | `10.20.20.0/24` | Servers               |
|   30 | `10.20.30.0/24` | Employee Workstations |
|   40 | `10.20.40.0/24` | IT Administration     |
|   50 | `10.20.50.0/24` | Corporate Wireless    |
|   60 | `10.20.60.0/24` | Guest Wireless        |
|   70 | `10.20.70.0/24` | Lab and Testing       |
|   80 | `10.20.80.0/24` | Remote VPN Clients    |

The VLAN structure may be introduced gradually as the lab develops.

---

# 3. Default Gateway Standard

The first usable address in each subnet will normally be assigned to the pfSense interface serving that network.

Example:

```text
10.20.20.1
```

Therefore, the standard gateway convention will be:

```text
10.20.<VLAN>.1
```

Examples:

| Network            | Gateway      |
| ------------------ | ------------ |
| Management         | `10.20.10.1` |
| Servers            | `10.20.20.1` |
| Workstations       | `10.20.30.1` |
| IT Administration  | `10.20.40.1` |
| Corporate Wireless | `10.20.50.1` |
| Guest Wireless     | `10.20.60.1` |
| Lab/Test           | `10.20.70.1` |
| VPN                | `10.20.80.1` |

---

# 4. VLAN 10 — Network Management

**Network:**

```text
10.20.10.0/24
```

**Subnet Mask:**

```text
255.255.255.0
```

**Default Gateway:**

```text
10.20.10.1
```

This network will be used for infrastructure management.

Potential devices include:

* Managed switches
* Wireless access points
* Hypervisor management
* Firewall management
* Network appliances
* Monitoring interfaces

---

## Management Address Allocation

| Range                       | Purpose                |
| --------------------------- | ---------------------- |
| `10.20.10.1`                | Default gateway        |
| `10.20.10.2-10.20.10.49`    | Network infrastructure |
| `10.20.10.50-10.20.10.99`   | Management systems     |
| `10.20.10.100-10.20.10.199` | Reserved future use    |
| `10.20.10.200-10.20.10.254` | Reserved               |

Management systems should generally use static addresses or DHCP reservations.

---

# 5. VLAN 20 — Servers

**Network:**

```text
10.20.20.0/24
```

**Subnet Mask:**

```text
255.255.255.0
```

**Default Gateway:**

```text
10.20.20.1
```

This network will contain Stoneleaf Systems server infrastructure.

Servers should normally use static IPv4 addresses.

---

## Planned Server Addresses

| Hostname   | Role                                     | Address       |
| ---------- | ---------------------------------------- | ------------- |
| `SL-DC01`  | Primary Domain Controller / DNS          | `10.20.20.10` |
| `SL-DC02`  | Future Secondary Domain Controller / DNS | `10.20.20.11` |
| `SL-FS01`  | File Server                              | `10.20.20.20` |
| `SL-LNX01` | Ubuntu Linux Server                      | `10.20.20.30` |
| `SL-MON01` | Future Monitoring Server                 | `10.20.20.40` |
| `SL-LOG01` | Future Logging Server                    | `10.20.20.41` |

Additional server addresses will be assigned as systems are deployed.

---

## Server Address Allocation

| Range                       | Purpose                            |
| --------------------------- | ---------------------------------- |
| `10.20.20.1`                | Gateway                            |
| `10.20.20.2-10.20.20.9`     | Network/infrastructure reservation |
| `10.20.20.10-10.20.20.49`   | Core servers                       |
| `10.20.20.50-10.20.20.99`   | Application servers                |
| `10.20.20.100-10.20.20.149` | Monitoring/security systems        |
| `10.20.20.150-10.20.20.199` | Future servers                     |
| `10.20.20.200-10.20.20.254` | Reserved                           |

---

# 6. VLAN 30 — Employee Workstations

**Network:**

```text
10.20.30.0/24
```

**Subnet Mask:**

```text
255.255.255.0
```

**Default Gateway:**

```text
10.20.30.1
```

This network will contain standard employee Windows workstations.

Stoneleaf Systems represents 40 employees but will initially use nine representative Windows 11 workstation VMs.

---

## DHCP Scope

The primary workstation DHCP scope will be:

```text
10.20.30.100 - 10.20.30.199
```

This provides 100 dynamically assignable addresses.

---

## Representative Workstations

Workstations will normally receive addresses through DHCP rather than permanent static assignments.

Planned systems include:

```text
SL-WS-EXEC01
SL-WS-IT01
SL-WS-OPS01
SL-WS-SALES01
SL-WS-CS01
SL-WS-FIN01
SL-WS-HR01
SL-WS-REMOTE01
SL-WS-TEST01
```

DHCP reservations may later be created when consistent addresses are useful for testing or administration.

---

## Workstation Address Allocation

| Range                       | Purpose                   |
| --------------------------- | ------------------------- |
| `10.20.30.1`                | Gateway                   |
| `10.20.30.2-10.20.30.49`    | Reserved infrastructure   |
| `10.20.30.50-10.20.30.99`   | Reserved/static endpoints |
| `10.20.30.100-10.20.30.199` | DHCP clients              |
| `10.20.30.200-10.20.30.254` | Future use                |

---

# 7. VLAN 40 — IT Administration

**Network:**

```text
10.20.40.0/24
```

**Default Gateway:**

```text
10.20.40.1
```

The IT Administration network is intended for systems used to manage infrastructure.

Potential systems include:

* Privileged Access Workstations
* Administrative jump hosts
* Network-management systems
* IT troubleshooting systems

This network should receive greater access to infrastructure than normal employee networks.

Access should still follow least-privilege principles.

---

# 8. VLAN 50 — Corporate Wireless

**Network:**

```text
10.20.50.0/24
```

**Default Gateway:**

```text
10.20.50.1
```

**DHCP Scope:**

```text
10.20.50.100 - 10.20.50.220
```

This network will support authorized company wireless devices.

Potential devices include:

* Company laptops
* Mobile devices
* Authorized wireless endpoints

Corporate wireless devices should authenticate using approved credentials and should not share the same network as guest devices.

---

# 9. VLAN 60 — Guest Wireless

**Network:**

```text
10.20.60.0/24
```

**Default Gateway:**

```text
10.20.60.1
```

**DHCP Scope:**

```text
10.20.60.100 - 10.20.60.240
```

The Guest Wireless network will provide internet access for visitors and unmanaged devices.

Guest clients should normally be prevented from accessing:

* Domain controllers
* File servers
* Employee workstations
* Management interfaces
* Internal business systems
* Administrative networks

Guest traffic should primarily be permitted outbound to the internet.

---

# 10. VLAN 70 — Lab and Testing

**Network:**

```text
10.20.70.0/24
```

**Default Gateway:**

```text
10.20.70.1
```

This network will support temporary systems and controlled testing.

Examples include:

* Test servers
* Test workstations
* Troubleshooting exercises
* Vulnerability testing
* Experimental services
* Intentionally misconfigured systems

Lab systems should be separated from normal business systems whenever practical.

---

# 11. VLAN 80 — Remote VPN Clients

**Network:**

```text
10.20.80.0/24
```

This address space is reserved for authenticated remote-access VPN users.

Example VPN pool:

```text
10.20.80.100 - 10.20.80.150
```

VPN users should receive access only to resources required for their role.

Remote access should not automatically provide unrestricted access to the entire Stoneleaf Systems environment.

---

# 12. DHCP Standards

DHCP will primarily be used for:

* Employee workstations
* Wireless devices
* Guest devices
* Temporary test systems

Static addressing will primarily be used for:

* Domain controllers
* Servers
* Firewalls
* Network devices
* Monitoring systems
* Infrastructure services

---

# 13. Static Address Standard

Static infrastructure should normally use lower-numbered addresses within each subnet.

General convention:

```text
.1          Gateway
.2-.49      Infrastructure / Servers
.50-.99     Reserved / Static Devices
.100-.199   DHCP
.200-.254   Expansion / Reserved
```

This pattern may be adjusted when a specific network requires a larger DHCP pool.

---

# 14. DNS Server Configuration

Domain-joined systems should use the Stoneleaf Systems domain controllers as their primary DNS servers.

Initial configuration:

```text
Primary DNS:   10.20.20.10
Secondary DNS: 10.20.20.11
```

Until `SL-DC02` is deployed, clients will use:

```text
10.20.20.10
```

as the primary internal DNS server.

Domain-joined systems should not normally use public DNS servers directly.

Internal DNS servers may forward external queries to approved upstream DNS services.

---

# 15. DHCP Options

Standard DHCP configurations should provide:

### Default Gateway

Example:

```text
10.20.30.1
```

### DNS Server

```text
10.20.20.10
```

Future secondary DNS:

```text
10.20.20.11
```

Additional DHCP options may be configured as the environment develops.

---

# 16. Microsoft Azure Addressing

Microsoft Azure must use a separate address space that does not overlap with the local Stoneleaf Systems network.

The planned Azure Virtual Network will use:

```text
10.50.0.0/16
```

This allows future site-to-site VPN connectivity between the local environment and Azure.

---

## Planned Azure Subnets

| Azure Subnet       | Network         | Purpose                       |
| ------------------ | --------------- | ----------------------------- |
| Server Subnet      | `10.50.10.0/24` | Azure virtual machines        |
| Management Subnet  | `10.50.20.0/24` | Administrative resources      |
| Application Subnet | `10.50.30.0/24` | Future applications           |
| Security Subnet    | `10.50.40.0/24` | Security/monitoring resources |

Additional Azure networks may be added as required.

---

# 17. Local-to-Azure Architecture

The local and Azure networks will remain non-overlapping.

```text
Stoneleaf Local Network
10.20.0.0/16
        │
        │
        │ Site-to-Site VPN
        │
        ▼
Microsoft Azure
10.50.0.0/16
```

Non-overlapping address spaces are necessary for reliable routing between the two environments.

---

# 18. IP Address Assignment Rules

All infrastructure addresses must be documented.

Before assigning a new static address:

1. Identify the correct network.
2. Verify that the address is unused.
3. Confirm that it falls within the appropriate range.
4. Record the hostname.
5. Record the device role.
6. Record the IP address.
7. Record the subnet.
8. Record the gateway.
9. Record relevant DNS information.
10. Update documentation.

---

# 19. Reserved Addresses

The following addresses must not be assigned to hosts within a `/24` subnet:

```text
.0
```

Network address

and

```text
.255
```

Broadcast address

The `.1` address is reserved for the default gateway unless otherwise documented.

---

# 20. IP Address Documentation

Static systems should be tracked using a table similar to:

| Hostname   | IP Address          | Network      | Role         | Assignment |
| ---------- | ------------------- | ------------ | ------------ | ---------- |
| `SL-FW01`  | Multiple interfaces | Network Edge | Firewall     | Static     |
| `SL-DC01`  | `10.20.20.10`       | Servers      | AD DS / DNS  | Static     |
| `SL-DC02`  | `10.20.20.11`       | Servers      | AD DS / DNS  | Static     |
| `SL-FS01`  | `10.20.20.20`       | Servers      | File Server  | Static     |
| `SL-LNX01` | `10.20.20.30`       | Servers      | Linux Server | Static     |
| `SL-MON01` | `10.20.20.40`       | Servers      | Monitoring   | Static     |
| `SL-LOG01` | `10.20.20.41`       | Servers      | Logging      | Static     |

This table will be updated as infrastructure is deployed.

---

# 21. Addressing Design Principles

## No Overlapping Networks

Local, remote-access, test, and Azure networks should not use overlapping address spaces.

## Predictable Addressing

Network IDs should make it easy to identify a system's purpose.

For example:

```text
10.20.20.x = Servers
10.20.30.x = Workstations
10.20.40.x = IT Administration
```

## Static Infrastructure

Critical infrastructure should use predictable static addresses.

## Dynamic Endpoints

Normal employee endpoints should generally receive addresses through DHCP.

## Documentation

Every static IP assignment must be documented.

## Scalability

Unused address space should remain available for future growth.

---

# 22. Initial Implementation

Stoneleaf Systems does not need to deploy every VLAN immediately.

The environment can initially begin with the most important networks:

```text
VLAN 20 — Servers
VLAN 30 — Workstations
VLAN 70 — Lab/Test
```

Additional segmentation can be implemented as networking skills and infrastructure capabilities develop.

This provides an opportunity to document the migration from a simpler network into a more segmented enterprise design.

---

# 23. Future Network Expansion

Future network segments could include:

```text
10.20.90.0/24   Printers / IoT

10.20.100.0/24  Voice / Communications

10.20.110.0/24  Backup Infrastructure

10.20.120.0/24  Security Infrastructure
```

These networks should only be created when a defined requirement exists.

---

# IP Addressing Summary

| Network         | CIDR            | Gateway       | Primary Use            |
| --------------- | --------------- | ------------- | ---------------------- |
| Management      | `10.20.10.0/24` | `10.20.10.1`  | Network management     |
| Servers         | `10.20.20.0/24` | `10.20.20.1`  | Server infrastructure  |
| Workstations    | `10.20.30.0/24` | `10.20.30.1`  | Employee endpoints     |
| IT Admin        | `10.20.40.0/24` | `10.20.40.1`  | Administrative systems |
| Corporate Wi-Fi | `10.20.50.0/24` | `10.20.50.1`  | Company wireless       |
| Guest Wi-Fi     | `10.20.60.0/24` | `10.20.60.1`  | Guest internet         |
| Lab/Test        | `10.20.70.0/24` | `10.20.70.1`  | Testing                |
| VPN             | `10.20.80.0/24` | `10.20.80.1`  | Remote clients         |
| Azure           | `10.50.0.0/16`  | Azure-managed | Cloud infrastructure   |

---

## Document Status

**Organization:** Stoneleaf Systems

**Local Address Space:** `10.20.0.0/16`

**Azure Address Space:** `10.50.0.0/16`

**Primary Subnet Size:** `/24`

**Current Phase:** `00-Foundation`

**Current Document:** `IP-Addressing-Plan.md`

**Next Document:** `Naming-Standards.md`

