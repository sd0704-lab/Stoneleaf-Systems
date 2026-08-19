# 01 — Network Infrastructure

## Overview

The **Network Infrastructure** phase builds the networking foundation for the Stoneleaf Systems enterprise IT environment.

The Foundation phase defined the organization's requirements, architecture, addressing strategy, naming conventions, and operational standards. This phase turns those designs into a functioning network.

Stoneleaf Systems will begin with a virtualized network using **VMware Workstation** and **pfSense**, then gradually introduce segmentation, routing, DHCP, firewall policies, network services, monitoring, troubleshooting, and hybrid connectivity.

The goal is to build the network in stages rather than configuring the entire environment at once.

---

## Phase Objectives

This phase will provide hands-on experience with:

* VMware virtual networking
* pfSense installation and administration
* IPv4 addressing
* Subnetting
* Default gateways
* NAT
* Routing
* VLAN concepts
* Network segmentation
* Firewall rules
* DHCP
* DNS-related networking
* Network troubleshooting
* Network documentation
* Connectivity validation
* Network security
* VPN concepts
* Network monitoring
* Network change management

---

# Network Architecture

Stoneleaf Systems uses the private address space:

```text
10.20.0.0/16
```

This address space is divided into logical `/24` networks.

| VLAN | Network         | Purpose            |
| ---: | --------------- | ------------------ |
|   10 | `10.20.10.0/24` | Management         |
|   20 | `10.20.20.0/24` | Servers            |
|   30 | `10.20.30.0/24` | Workstations       |
|   40 | `10.20.40.0/24` | IT Administration  |
|   50 | `10.20.50.0/24` | Corporate Wireless |
|   60 | `10.20.60.0/24` | Guest Wireless     |
|   70 | `10.20.70.0/24` | Lab/Test           |
|   80 | `10.20.80.0/24` | Remote VPN         |

Not every network will be deployed immediately.

The environment will begin with the networks necessary to support the first infrastructure systems and expand as additional capabilities are introduced.

---

# Primary Network Device

The primary network edge device will be:

```text
SL-FW01
```

**Platform:** pfSense

`SL-FW01` will eventually provide:

* Internet connectivity
* Default gateways
* Network Address Translation
* Routing
* Firewall policies
* Network segmentation
* DHCP where appropriate
* VPN connectivity
* Traffic logging
* Network troubleshooting capabilities

---

# Initial Network Design

The first implementation will focus on a small number of networks.

Initial target:

```text
Internet / VMware NAT
        │
        ▼
     SL-FW01
      pfSense
        │
        ├── Server Network
        │   10.20.20.0/24
        │
        ├── Workstation Network
        │   10.20.30.0/24
        │
        └── Lab/Test Network
            10.20.70.0/24
```

This provides enough infrastructure to begin deploying:

* Domain controllers
* Servers
* Windows workstations
* Linux systems
* Test systems

Additional segmentation will follow later.

---

# Gateway Standard

pfSense will generally use the first usable address of each network as its gateway.

Examples:

```text
10.20.20.1 — Server Gateway
10.20.30.1 — Workstation Gateway
10.20.70.1 — Lab/Test Gateway
```

Future networks will follow the same convention.

---

# Planned Infrastructure

The networking phase will prepare connectivity for systems including:

| Hostname   | Role                        | Planned Address     |
| ---------- | --------------------------- | ------------------- |
| `SL-FW01`  | pfSense Firewall            | Multiple interfaces |
| `SL-DC01`  | Domain Controller / DNS     | `10.20.20.10`       |
| `SL-DC02`  | Secondary Domain Controller | `10.20.20.11`       |
| `SL-FS01`  | File Server                 | `10.20.20.20`       |
| `SL-LNX01` | Linux Server                | `10.20.20.30`       |
| `SL-MON01` | Monitoring Server           | `10.20.20.40`       |
| `SL-LOG01` | Logging Server              | `10.20.20.41`       |

Employee workstations will primarily use DHCP.

---

# Representative Workstations

Stoneleaf Systems represents approximately 40 employees but uses nine representative Windows 11 workstations.

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

These systems will allow the network to simulate different departments and use cases without requiring 40 workstation virtual machines.

---

# Network Implementation Strategy

The network will be built incrementally.

## Stage 1 — VMware Networking

Configure the virtual networks required for the lab.

Topics include:

* VMware NAT
* Host-only networking
* Virtual network adapters
* Virtual switches
* Isolated networks
* Internet connectivity

---

## Stage 2 — pfSense Deployment

Deploy:

```text
SL-FW01
```

Tasks include:

* Create pfSense virtual machine
* Assign WAN interface
* Assign LAN/internal interfaces
* Configure administrative access
* Configure interface addressing
* Verify internet connectivity
* Verify NAT

---

## Stage 3 — Server Network

Deploy:

```text
10.20.20.0/24
```

Gateway:

```text
10.20.20.1
```

Initial server:

```text
SL-DC01
10.20.20.10
```

This network becomes the foundation for later Windows Server infrastructure.

---

## Stage 4 — Workstation Network

Deploy:

```text
10.20.30.0/24
```

Gateway:

```text
10.20.30.1
```

Initial DHCP pool:

```text
10.20.30.100–10.20.30.199
```

Representative Windows workstations will use this network.

---

## Stage 5 — Lab/Test Network

Deploy:

```text
10.20.70.0/24
```

Gateway:

```text
10.20.70.1
```

This network will provide an isolated location for:

* Experimental systems
* Troubleshooting exercises
* Intentionally broken configurations
* Test servers
* Test clients
* Security exercises

---

## Stage 6 — Segmentation

Additional networks will be introduced.

Examples:

```text
VLAN 10 — Management
VLAN 40 — IT Administration
VLAN 50 — Corporate Wireless
VLAN 60 — Guest Wireless
VLAN 80 — VPN
```

Firewall policies will control communication between networks.

---

# Firewall Policy Strategy

Stoneleaf Systems will follow a **least-privilege network-access model**.

Traffic should be allowed because a business requirement exists rather than simply allowing unrestricted communication between all networks.

Examples:

```text
Allow-Workstations-to-DNS

Allow-Workstations-to-DHCP

Allow-Workstations-to-FileServer-SMB

Allow-ITAdmin-to-Servers-RDP

Allow-Servers-to-Internet-HTTPS

Deny-Guest-to-Internal
```

Firewall rules will be tested after implementation.

---

# Network Segmentation

Segmentation will separate systems with different security and operational requirements.

Examples include:

### Servers

Contains critical enterprise infrastructure.

```text
10.20.20.0/24
```

### Workstations

Contains normal employee endpoints.

```text
10.20.30.0/24
```

### IT Administration

Provides a more trusted management network.

```text
10.20.40.0/24
```

### Guest Wireless

Provides internet connectivity without internal network access.

```text
10.20.60.0/24
```

### Lab/Test

Contains systems used for experimentation and troubleshooting.

```text
10.20.70.0/24
```

---

# DHCP

DHCP will be used for normal endpoints.

The initial workstation scope will use:

```text
Network:
10.20.30.0/24

Gateway:
10.20.30.1

DHCP Pool:
10.20.30.100–10.20.30.199

DNS:
10.20.20.10
```

DHCP administration will include:

* Scope creation
* Lease management
* Exclusions
* Reservations
* DHCP options
* Client lease renewal
* Troubleshooting

---

# DNS Dependency

Active Directory DNS will eventually operate from:

```text
SL-DC01
10.20.20.10
```

Future secondary DNS:

```text
SL-DC02
10.20.20.11
```

Network infrastructure must allow clients to communicate with the internal DNS servers.

DNS configuration itself will be implemented in greater detail during:

`02-Windows-Server-Active-Directory`

---

# NAT

`SL-FW01` will provide Network Address Translation for internal systems.

Private networks such as:

```text
10.20.20.0/24
10.20.30.0/24
10.20.70.0/24
```

will access the internet through the pfSense WAN interface.

NAT will allow the private Stoneleaf Systems network to reach external services without exposing internal IPv4 addresses directly.

---

# Routing

The networking phase will demonstrate routing between multiple internal networks.

Routing tasks will include:

* Default gateways
* Routing tables
* Inter-network routing
* Static routes where required
* Route validation
* Route troubleshooting

Useful tools will include:

```text
tracert
traceroute
route print
Get-NetRoute
```

---

# Network Troubleshooting

Troubleshooting will be intentionally incorporated throughout this phase.

Example failures may include:

* Incorrect IPv4 address
* Incorrect subnet mask
* Incorrect gateway
* DHCP failure
* APIPA address
* DNS misconfiguration
* Firewall rule blocking traffic
* Missing route
* Incorrect interface assignment
* Duplicate IPv4 address
* Network isolation failure

The objective is not simply to create a functioning network.

The objective is to learn how to identify why a network is **not** functioning.

---

# Troubleshooting Methodology

Stoneleaf Systems will generally use the following process:

1. Identify the problem.
2. Gather information.
3. Determine the scope.
4. Establish a theory of probable cause.
5. Test the theory.
6. Correct the issue.
7. Verify full functionality.
8. Document the resolution.

Important troubleshooting scenarios will eventually become incident tickets in:

`05-IT-Operations`

---

# Network Tools

## Windows

```text
ipconfig
ping
tracert
nslookup
arp
netstat
route
pathping
```

## PowerShell

```powershell
Get-NetAdapter
Get-NetIPAddress
Get-NetRoute
Test-NetConnection
Resolve-DnsName
```

## Linux

```bash
ip addr
ip route
ping
traceroute
dig
ss
arp
```

## pfSense

pfSense tools will include:

* Ping
* Packet capture
* Firewall logs
* States
* Routing table
* Interface status
* DNS lookup
* Traffic graphs

---

# Evidence Requirements

Important networking projects should produce portfolio evidence.

Evidence may include:

* Architecture diagrams
* VMware network configuration
* pfSense interface configuration
* Firewall rules
* DHCP scopes
* Routing tables
* Command output
* Packet captures
* Connectivity tests
* Screenshots
* Change records
* Incident tickets
* Troubleshooting documentation

Evidence should demonstrate both successful configuration and technical understanding.

---

# Validation Standard

A network configuration is not considered complete simply because it has been entered.

It should be validated.

Examples include:

```text
Can the workstation reach its gateway?

Can the workstation reach SL-DC01?

Can it resolve internal DNS?

Can it reach the internet?

Can a guest network reach internal servers?

Can IT Administration reach approved management services?

Does the firewall block traffic that should be denied?
```

Validation results should be documented.

---

# Change Management

Significant networking changes should follow:

`00-Foundation/Change-Management.md`

Examples include:

```text
CHG-0001 — Deploy SL-FW01

CHG-0002 — Create Server Network

CHG-0003 — Create Workstation Network

CHG-0004 — Implement Network Segmentation

CHG-0005 — Configure Guest Network
```

Changes should include:

* Business justification
* Risk
* Implementation plan
* Testing
* Rollback
* Validation

---

# Documentation Standards

All network documentation will follow:

`00-Foundation/Documentation-Standards.md`

Infrastructure names will follow:

`00-Foundation/Naming-Standards.md`

IPv4 assignments will follow:

`00-Foundation/IP-Addressing-Plan.md`

---

# Security Principles

Networking decisions will follow several core security principles.

## Least Privilege

Only required communication should be permitted.

## Segmentation

Systems with different purposes and risk levels should be separated.

## Administrative Separation

Management access should be more restricted than normal employee access.

## Logging

Important firewall and network events should be logged.

## Secure Management

Network devices should be administered using secure methods.

## Change Control

Important network configuration changes should be documented.

---

# Network+ Alignment

This phase provides the primary hands-on implementation environment for the Network+ skills defined in:

`00-Foundation/NetworkPlus-Skills-Matrix.md`

Major skills demonstrated will include:

* IPv4
* Subnetting
* Network topologies
* Network devices
* Routing
* Switching concepts
* VLANs
* DHCP
* DNS
* NAT
* Firewalls
* VPN
* Virtual networking
* Network security
* Network operations
* Network troubleshooting

---

# Planned Repository Structure

The `01-Network-Infrastructure` section will expand as the network is built.

```text
01-Network-Infrastructure/
│
├── README.md
│
├── VMware-Network-Design.md
├── pfSense-Deployment.md
├── Network-Topology.md
├── Server-Network.md
├── Workstation-Network.md
├── Lab-Test-Network.md
├── VLAN-Implementation.md
├── Routing-Configuration.md
├── DHCP-Configuration.md
├── Firewall-Rules.md
├── NAT-Configuration.md
├── Network-Validation.md
├── Network-Troubleshooting.md
│
├── Diagrams/
│
├── Screenshots/
│
└── Configs/
```

Documents will be created as the corresponding infrastructure is actually designed and implemented.

---

# Implementation Order

The planned order for this phase is:

```text
1. VMware Network Design
        ↓
2. Deploy SL-FW01
        ↓
3. Verify WAN / Internet
        ↓
4. Build Server Network
        ↓
5. Build Workstation Network
        ↓
6. Build Lab/Test Network
        ↓
7. Validate Routing
        ↓
8. Configure Firewall Policies
        ↓
9. Configure DHCP
        ↓
10. Deploy Additional Segmentation
        ↓
11. Introduce Failures
        ↓
12. Troubleshoot and Document
```

---

# Phase Completion Criteria

The Network Infrastructure phase will be considered substantially complete when Stoneleaf Systems can demonstrate:

* Functional pfSense firewall
* Internet connectivity
* Multiple internal networks
* Correct IPv4 addressing
* Functional routing
* NAT
* DHCP
* Network segmentation
* Appropriate firewall rules
* Server connectivity
* Workstation connectivity
* Lab isolation
* Network troubleshooting
* Documented network architecture
* Validation evidence

Additional advanced networking work may continue during later phases.

---

## Phase Status

**Organization:** Stoneleaf Systems

**Current Phase:** `01-Network-Infrastructure`

**Phase Status:** In Progress

**Primary Firewall:** `SL-FW01`

**Firewall Platform:** pfSense

**Local Address Space:** `10.20.0.0/16`

**First Networks:** Servers, Workstations, Lab/Test

**Next Document:** `VMware-Network-Design.md`

