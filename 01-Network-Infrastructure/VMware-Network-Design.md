# Stoneleaf Systems — VMware Network Design

## Purpose

This document defines the VMware Workstation virtual-network design used to build the Stoneleaf Systems enterprise IT environment.

VMware Workstation will provide the virtual switching and network-isolation layer beneath the Stoneleaf Systems servers, workstations, Linux systems, and pfSense firewall.

The initial design will use **separate VMware virtual networks for each logical Stoneleaf Systems subnet**.

This approach allows the lab to build and troubleshoot multiple routed networks without requiring physical managed switches.

---

# 1. Design Goals

The VMware network design must support:

* Internet connectivity
* pfSense firewalling
* Multiple isolated internal networks
* Server infrastructure
* Employee workstations
* IT administration systems
* Lab and testing systems
* Future network expansion
* Routing between networks
* DHCP
* DNS
* Firewall-policy testing
* Network troubleshooting
* Microsoft Azure connectivity later in the project

---

# 2. Network Architecture

The initial VMware environment will place `SL-FW01` between the external VMware network and all Stoneleaf Systems internal networks.

```text
                    Internet
                       │
                       ▼
               Host Computer Network
                       │
                       ▼
                 VMware NAT
                    VMnet8
                       │
                       │ WAN
                       ▼
                ┌─────────────┐
                │   SL-FW01   │
                │   pfSense   │
                └──────┬──────┘
                       │
       ┌───────────────┼───────────────┐
       │               │               │
       ▼               ▼               ▼
 Server Network   Workstation      Lab/Test
  VMnet20           VMnet30         VMnet70
10.20.20.0/24     10.20.30.0/24   10.20.70.0/24
```

`SL-FW01` will become the router and security boundary between these networks.

---

# 3. VMware Network Types

VMware Workstation provides several types of virtual networks.

The Stoneleaf Systems lab will use them deliberately according to function.

---

## Bridged Networking

A bridged virtual machine connects directly to the host computer's physical network.

The VM behaves like another device on the physical LAN.

Example:

```text
Physical Network
      │
      ├── Host Computer
      │
      └── Virtual Machine
```

Bridged networking is useful when a virtual machine needs direct access to the physical LAN.

Stoneleaf Systems will **not initially use bridged networking for the internal enterprise network**.

Keeping the lab separated from the home network provides greater control and reduces the chance of accidental interference with real devices.

---

# 4. VMware NAT

VMware NAT allows virtual machines to access external networks through the host computer.

The default VMware NAT network is normally:

```text
VMnet8
```

Stoneleaf Systems will use `VMnet8` as the external/WAN-facing network for `SL-FW01`.

Logical flow:

```text
Internet
   │
Host Computer
   │
VMware NAT
VMnet8
   │
SL-FW01 WAN
```

pfSense will then provide NAT again for the Stoneleaf internal networks.

This creates a lab-safe **double-NAT environment**, which is acceptable for the initial homelab.

---

# 5. Host-Only / Custom Networks

Internal Stoneleaf Systems networks will use isolated VMware virtual networks.

These networks function like independent virtual switches.

Examples:

```text
VMnet20 — Servers
VMnet30 — Workstations
VMnet70 — Lab/Test
```

Virtual machines connected to the same VMnet can communicate at Layer 2.

Communication between different VMnets must pass through `SL-FW01`.

This provides a realistic routing and firewalling environment.

---

# 6. Initial VMware Network Inventory

The initial configuration will contain four primary VMware networks.

| VMware Network | Stoneleaf Purpose      | IPv4 Network    |
| -------------- | ---------------------- | --------------- |
| `VMnet8`       | pfSense WAN / Internet | VMware-managed  |
| `VMnet20`      | Servers                | `10.20.20.0/24` |
| `VMnet30`      | Workstations           | `10.20.30.0/24` |
| `VMnet70`      | Lab/Test               | `10.20.70.0/24` |

Additional VMnets will be added later when required.

---

# 7. VMnet8 — WAN Network

`VMnet8` will provide the WAN connection for pfSense.

VMware will manage the addressing on this network.

`SL-FW01` will initially obtain its WAN address through DHCP from VMware.

Example logical configuration:

```text
SL-FW01
Interface: WAN
VMware Network: VMnet8
IPv4 Assignment: DHCP
```

The exact WAN address does not need to match the Stoneleaf Systems internal addressing plan.

---

# 8. VMnet20 — Server Network

VMware network:

```text
VMnet20
```

Stoneleaf network:

```text
10.20.20.0/24
```

Subnet mask:

```text
255.255.255.0
```

pfSense gateway:

```text
10.20.20.1
```

This network will contain critical server infrastructure.

Planned systems include:

| Hostname   | Address       | Role                        |
| ---------- | ------------- | --------------------------- |
| `SL-DC01`  | `10.20.20.10` | Domain Controller / DNS     |
| `SL-DC02`  | `10.20.20.11` | Secondary Domain Controller |
| `SL-FS01`  | `10.20.20.20` | File Server                 |
| `SL-LNX01` | `10.20.20.30` | Linux Server                |
| `SL-MON01` | `10.20.20.40` | Monitoring                  |
| `SL-LOG01` | `10.20.20.41` | Logging                     |

Servers will normally use static addressing.

---

# 9. VMnet30 — Workstation Network

VMware network:

```text
VMnet30
```

Stoneleaf network:

```text
10.20.30.0/24
```

Subnet mask:

```text
255.255.255.0
```

Gateway:

```text
10.20.30.1
```

Planned DHCP pool:

```text
10.20.30.100 - 10.20.30.199
```

This network will support the representative Stoneleaf Systems Windows 11 workstations.

Examples:

```text
SL-WS-EXEC01
SL-WS-IT01
SL-WS-OPS01
SL-WS-SALES01
SL-WS-CS01
SL-WS-FIN01
SL-WS-HR01
```

Workstations will generally use DHCP.

---

# 10. VMnet70 — Lab/Test Network

VMware network:

```text
VMnet70
```

Stoneleaf network:

```text
10.20.70.0/24
```

Gateway:

```text
10.20.70.1
```

This network will be used for:

* Test systems
* Temporary virtual machines
* Network experiments
* Troubleshooting exercises
* Intentionally misconfigured systems
* Security testing
* Network+ exercises

The Lab/Test network provides a safer location to intentionally break systems without affecting the primary simulated business environment.

---

# 11. Why Separate VMnets Are Used Initially

Stoneleaf Systems ultimately includes VLAN concepts, but the first network implementation will use separate VMware virtual networks.

This provides several advantages.

### Simplicity

Each network behaves like a separate virtual Ethernet switch.

### Visibility

It is easy to understand which virtual machine belongs to which subnet.

### Isolation

Traffic cannot move between VMnets without routing.

### Troubleshooting

Network failures are easier to isolate while learning.

### pfSense Practice

pfSense must route and firewall traffic between the networks.

### Expandability

More complex VLAN configurations can be introduced later.

---

# 12. VMnet vs. VLAN

A VMware VMnet and an Ethernet VLAN are not exactly the same thing.

A VMware VMnet represents a separate virtual Layer 2 network.

A VLAN normally separates Layer 2 broadcast domains across managed switching infrastructure using VLAN IDs and potentially 802.1Q tagging.

The initial Stoneleaf environment therefore logically represents the planned network segments without requiring VLAN tagging immediately.

Example:

```text
VMnet20
   │
   └── Represents Server Network
       10.20.20.0/24
```

Later in the project, actual VLAN concepts can be introduced separately.

This allows Stoneleaf Systems to learn both:

1. Routed network segmentation
2. VLAN-based segmentation

---

# 13. VMware DHCP

VMware's built-in DHCP service should **not provide addresses to Stoneleaf internal business networks** once Stoneleaf DHCP is being used.

Therefore, VMware DHCP should be disabled for:

```text
VMnet20
VMnet30
VMnet70
```

This prevents VMware from competing with pfSense or Windows DHCP.

`VMnet8` may continue using VMware DHCP because it represents the external/WAN environment.

---

# 14. VMware Host Virtual Adapters

VMware may create host-side virtual adapters for custom networks.

Examples may appear in Windows as:

```text
VMware Network Adapter VMnet20
VMware Network Adapter VMnet30
VMware Network Adapter VMnet70
```

Where appropriate, the host adapter may remain enabled to allow the physical host to communicate with lab systems.

However, Stoneleaf Systems should not rely on the host adapter as the default gateway.

The default gateway for Stoneleaf internal networks must be `SL-FW01`.

---

# 15. pfSense Virtual Network Interfaces

The initial `SL-FW01` VM will require four virtual network adapters.

| pfSense Interface | VMware Network | Purpose               |
| ----------------- | -------------- | --------------------- |
| WAN               | `VMnet8`       | Internet              |
| SERVERS           | `VMnet20`      | Server network        |
| WORKSTATIONS      | `VMnet30`      | Employee workstations |
| LAB               | `VMnet70`      | Lab/Test              |

---

# 16. pfSense Addressing

The internal pfSense interfaces will use:

```text
SERVERS
10.20.20.1/24
```

```text
WORKSTATIONS
10.20.30.1/24
```

```text
LAB
10.20.70.1/24
```

These addresses become the default gateways for systems on each network.

---

# 17. pfSense Interface Layout

The logical pfSense configuration will appear similar to:

```text
SL-FW01
│
├── WAN
│   └── VMnet8
│       └── VMware DHCP
│
├── SERVERS
│   └── VMnet20
│       └── 10.20.20.1/24
│
├── WORKSTATIONS
│   └── VMnet30
│       └── 10.20.30.1/24
│
└── LAB
    └── VMnet70
        └── 10.20.70.1/24
```

---

# 18. Server Virtual Machine Configuration

A server VM connected to the server network should use:

```text
Network Adapter:
VMnet20
```

Example:

```text
SL-DC01

VMware Network:
VMnet20

IPv4:
10.20.20.10

Subnet Mask:
255.255.255.0

Gateway:
10.20.20.1
```

Once DNS is deployed:

```text
DNS:
10.20.20.10
```

---

# 19. Workstation Virtual Machine Configuration

Employee workstations will use:

```text
VMnet30
```

Example:

```text
SL-WS-FIN01

VMware Network:
VMnet30

IPv4:
DHCP

Expected Address:
10.20.30.100–10.20.30.199

Gateway:
10.20.30.1

DNS:
10.20.20.10
```

---

# 20. Lab Virtual Machine Configuration

Test systems will use:

```text
VMnet70
```

Example:

```text
SL-W11-TEST01

VMware Network:
VMnet70

Network:
10.20.70.0/24

Gateway:
10.20.70.1
```

Static or dynamic addressing may be used depending on the exercise.

---

# 21. Initial Traffic Flow

A workstation accessing the internet will follow:

```text
SL-WS-FIN01
     │
     │ 10.20.30.x
     ▼
VMnet30
     │
     ▼
SL-FW01
10.20.30.1
     │
     │ NAT
     ▼
VMnet8
     │
     ▼
VMware NAT
     │
     ▼
Host Network
     │
     ▼
Internet
```

---

# 22. Inter-Network Traffic

A workstation accessing `SL-DC01` will follow:

```text
SL-WS-FIN01
10.20.30.x
      │
      ▼
VMnet30
      │
      ▼
SL-FW01
      │
      │ Routing / Firewall
      ▼
VMnet20
      │
      ▼
SL-DC01
10.20.20.10
```

This means pfSense can control communication between clients and servers.

---

# 23. Security Benefit

Using separate internal VMware networks provides an important security advantage.

A workstation cannot communicate directly with a server through the same Layer 2 network.

Instead:

```text
Workstation
     │
     ▼
pfSense
     │
     ▼
Server
```

pfSense can therefore allow or deny the traffic according to policy.

---

# 24. Future VMware Networks

As Stoneleaf Systems expands, additional VMnets may be created.

Recommended mapping:

| VMware Network | Stoneleaf Network | Purpose                       |
| -------------- | ----------------- | ----------------------------- |
| `VMnet10`      | `10.20.10.0/24`   | Management                    |
| `VMnet20`      | `10.20.20.0/24`   | Servers                       |
| `VMnet30`      | `10.20.30.0/24`   | Workstations                  |
| `VMnet40`      | `10.20.40.0/24`   | IT Administration             |
| `VMnet50`      | `10.20.50.0/24`   | Corporate Wireless Simulation |
| `VMnet60`      | `10.20.60.0/24`   | Guest Wireless Simulation     |
| `VMnet70`      | `10.20.70.0/24`   | Lab/Test                      |
| `VMnet80`      | `10.20.80.0/24`   | VPN / Remote Access           |

Not all networks need to exist immediately.

---

# 25. Resource Conservation

The existence of multiple VMware networks does not require every virtual machine to run simultaneously.

Stoneleaf Systems represents a 40-person organization, but the homelab will only power on the systems required for the current task.

For example, an Active Directory exercise may require:

```text
SL-FW01
SL-DC01
SL-WS-IT01
SL-WS-FIN01
```

Other workstations can remain powered off.

This significantly reduces CPU and memory requirements.

---

# 26. Network Adapter Naming

Within pfSense, interfaces should receive descriptive names.

Instead of leaving only generic interface names such as:

```text
OPT1
OPT2
OPT3
```

Stoneleaf Systems should rename them logically:

```text
SERVERS
WORKSTATIONS
LAB
IT-ADMIN
MANAGEMENT
```

This improves administration and troubleshooting.

---

# 27. VMware Network Naming Documentation

VMware Workstation identifies networks using VMnet numbers.

Stoneleaf Systems documentation should always record both the VMware network and business purpose.

Example:

```text
VMnet20
Stoneleaf Name: Server Network
IPv4: 10.20.20.0/24
Gateway: 10.20.20.1
```

This prevents confusion when viewing VMware configuration.

---

# 28. Network Change Control

Creating or modifying a VMware network should be treated as an infrastructure change once the environment becomes operational.

Example:

```text
CHG-0002 — Create Stoneleaf Server Network
```

The change record should document:

* VMnet number
* Network address
* DHCP status
* pfSense interface
* Gateway
* Testing
* Rollback

---

# 29. VMware Network Validation

After creating each VMnet, validation should confirm:

### Layer 2

Systems attached to the same VMnet can communicate when allowed.

### Layer 3

Systems have addresses from the correct network.

### Gateway

Systems can reach the correct pfSense interface.

### Routing

Traffic reaches permitted remote networks.

### NAT

Internal systems can reach the internet when permitted.

### Isolation

Systems cannot bypass pfSense to reach other Stoneleaf networks.

---

# 30. Validation Commands

Windows systems may use:

```powershell
Get-NetAdapter
Get-NetIPAddress
Get-NetRoute
```

and:

```text
ipconfig /all
ping
tracert
```

Linux systems may use:

```bash
ip addr
ip route
ping
traceroute
```

pfSense may use:

* Interface Status
* Ping
* Routing Table
* Firewall Logs
* Packet Capture
* States

---

# 31. Initial Validation Tests

Once `SL-FW01` is deployed, test:

### Server Network Gateway

```text
ping 10.20.20.1
```

### Workstation Network Gateway

```text
ping 10.20.30.1
```

### Lab Network Gateway

```text
ping 10.20.70.1
```

Then test:

* Internet connectivity
* Inter-network connectivity
* Firewall restrictions
* DNS when available

---

# 32. Troubleshooting Scenarios

The VMware design will support realistic network troubleshooting.

Potential exercises include:

---

## Incorrect VMnet

Example:

`SL-WS-FIN01` is accidentally connected to `VMnet70`.

Expected symptom:

The workstation receives an address from the wrong network or cannot access normal corporate resources.

---

## Disconnected Virtual NIC

Expected symptoms:

* No network connectivity
* Interface reports disconnected
* DHCP fails

---

## VMware DHCP Accidentally Enabled

Expected symptom:

A workstation receives an unexpected IP configuration instead of the Stoneleaf DHCP configuration.

---

## Incorrect Static IP

Example:

```text
SL-DC01
10.20.30.10
```

instead of:

```text
10.20.20.10
```

Expected result:

Server cannot communicate correctly on the server network.

---

## Incorrect Gateway

Example:

```text
10.20.20.254
```

instead of:

```text
10.20.20.1
```

Expected result:

Local subnet communication may work while remote-network communication fails.

---

## Wrong Subnet Mask

Example:

```text
255.255.0.0
```

instead of:

```text
255.255.255.0
```

This can create confusing routing behavior and is useful for troubleshooting practice.

---

# 33. VMware Snapshots

Snapshots should be created before major networking changes when appropriate.

Examples:

```text
2026-08-19_Pre-pfSense-Interfaces

2026-08-19_Post-pfSense-Initial-Config

2026-08-20_Pre-Firewall-Rules
```

Snapshots are temporary recovery tools and should not replace proper backups.

---

# 34. Network Evidence

Useful portfolio evidence from this portion of the project will include:

* VMware Virtual Network Editor screenshots
* VMnet configuration
* pfSense VM network adapters
* pfSense interface configuration
* Windows `ipconfig /all`
* Linux `ip addr`
* Successful gateway tests
* Successful internet tests
* Routing validation
* Firewall validation
* Troubleshooting examples

---

# 35. Screenshot Naming Examples

Screenshots should follow Stoneleaf documentation standards.

Examples:

```text
2026-08-19_VMware_VMnet20-Server-Network.png

2026-08-19_VMware_VMnet30-Workstation-Network.png

2026-08-19_SL-FW01_Network-Adapters.png

2026-08-19_SL-FW01_Interface-Assignments.png
```

---

# 36. Initial VMware Configuration Summary

| VMnet     | Purpose      | Network         | VMware DHCP | Gateway        |
| --------- | ------------ | --------------- | ----------- | -------------- |
| `VMnet8`  | WAN          | VMware-managed  | Enabled     | VMware-managed |
| `VMnet20` | Servers      | `10.20.20.0/24` | Disabled    | `10.20.20.1`   |
| `VMnet30` | Workstations | `10.20.30.0/24` | Disabled    | `10.20.30.1`   |
| `VMnet70` | Lab/Test     | `10.20.70.0/24` | Disabled    | `10.20.70.1`   |

---

# 37. pfSense Initial Interface Summary

| Interface    | VMware Network | IPv4 Configuration |
| ------------ | -------------- | ------------------ |
| WAN          | `VMnet8`       | DHCP               |
| SERVERS      | `VMnet20`      | `10.20.20.1/24`    |
| WORKSTATIONS | `VMnet30`      | `10.20.30.1/24`    |
| LAB          | `VMnet70`      | `10.20.70.1/24`    |

---

# 38. Design Decision

Stoneleaf Systems will **not create all eight planned internal networks at the beginning of the project**.

The initial build will use:

```text
VMnet20 — Servers
VMnet30 — Workstations
VMnet70 — Lab/Test
```

The remaining network segments will be introduced when the infrastructure requires them.

This provides several benefits:

* Easier troubleshooting
* Lower configuration complexity
* Clear understanding of each network
* Opportunity to document network expansion
* Opportunity to practice change management

---

# 39. Next Implementation

The next step is to deploy the virtual firewall:

```text
SL-FW01
```

The deployment will include:

1. Download the pfSense installer.
2. Create the pfSense VMware virtual machine.
3. Add four virtual network adapters.
4. Connect WAN to `VMnet8`.
5. Connect SERVERS to `VMnet20`.
6. Connect WORKSTATIONS to `VMnet30`.
7. Connect LAB to `VMnet70`.
8. Install pfSense.
9. Assign interfaces.
10. Configure internal gateway addresses.
11. Verify WAN connectivity.
12. Validate routing and internet access.
13. Document the configuration.

The implementation will be documented in:

`pfSense-Deployment.md`

---

## Document Status

**Organization:** Stoneleaf Systems

**Current Phase:** `01-Network-Infrastructure`

**Current Document:** `VMware-Network-Design.md`

**Virtualization Platform:** VMware Workstation

**WAN Network:** `VMnet8`

**Initial Internal Networks:** `VMnet20`, `VMnet30`, `VMnet70`

**Primary Firewall:** `SL-FW01`

**Next Document:** `pfSense-Deployment.md`
