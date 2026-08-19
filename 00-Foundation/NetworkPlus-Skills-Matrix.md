This finishes the **12th and final document in `00-Foundation`**. I’m mapping it to the current **CompTIA Network+ N10-009** skill areas: Networking Concepts, Network Implementation, Network Operations, Network Security, and Network Troubleshooting. CompTIA describes N10-009 as validating the ability to establish connectivity, maintain network documentation, work with network services and cloud/virtual networking, monitor networks, apply network hardening, and troubleshoot infrastructure. ([CompTIA Website][1])

# Stoneleaf Systems — Network+ Skills Matrix

## Purpose

This document maps the networking knowledge and hands-on activities performed throughout the Stoneleaf Systems enterprise IT homelab to the major skill areas of **CompTIA Network+ N10-009**.

The purpose of this matrix is not simply to prepare for a certification exam.

The goal is to demonstrate that Network+ concepts can be applied within a realistic enterprise environment through:

* Network design
* Configuration
* Administration
* Documentation
* Security
* Monitoring
* Troubleshooting
* Validation

Stoneleaf Systems will use Network+ concepts as the networking foundation upon which later systems administration, cloud, and security work will be built.

---

# 1. Network+ Skill Areas

Stoneleaf Systems will organize Network+ skill development around five major areas:

1. Networking Concepts
2. Network Implementation
3. Network Operations
4. Network Security
5. Network Troubleshooting

Each area will contain both knowledge objectives and practical Stoneleaf Systems tasks.

---

# 2. Skills Matrix Status

The following status values will be used:

| Status        | Meaning                                          |
| ------------- | ------------------------------------------------ |
| `Planned`     | Skill will be demonstrated later                 |
| `In Progress` | Currently being implemented or studied           |
| `Documented`  | Design has been documented                       |
| `Implemented` | Configuration has been completed                 |
| `Validated`   | Configuration has been tested successfully       |
| `Troubleshot` | Failure scenario has been diagnosed and resolved |

A skill may progress through several statuses during the project.

For example:

```text
Planned
   ↓
Documented
   ↓
Implemented
   ↓
Validated
   ↓
Troubleshot
```

---

# 3. Networking Concepts

This area establishes the fundamental concepts required to understand how the Stoneleaf Systems network operates.

---

## OSI Model

### Skills

* Understand the seven OSI layers.
* Associate protocols and devices with appropriate layers.
* Use the OSI model during troubleshooting.
* Distinguish physical, data-link, network, and transport problems.

### Stoneleaf Systems Application

Troubleshooting exercises will use the OSI model to isolate failures.

Example:

```text
User cannot reach SL-FS01.

Layer 1:
Is the network interface connected?

Layer 2:
Is the workstation connected to the correct VLAN?

Layer 3:
Does the workstation have a valid IP address?

Layer 4:
Is the required TCP/UDP port reachable?

Layer 7:
Is the file-sharing service functioning?
```

**Status:** Planned

---

## TCP/IP Model

### Skills

* Understand TCP/IP communication.
* Understand encapsulation.
* Understand IP-based communication.
* Understand TCP and UDP.
* Identify application protocols.

### Stoneleaf Systems Application

TCP/IP will be used throughout:

* Windows networking
* Linux networking
* Active Directory
* DNS
* DHCP
* SMB
* RDP
* SSH
* VPN
* Azure networking

**Status:** Planned

---

## IPv4 Addressing

### Skills

* Private IPv4 addressing
* Public vs. private addressing
* Subnet masks
* CIDR notation
* Default gateways
* Network addresses
* Broadcast addresses
* Host addresses
* APIPA
* Loopback addresses

### Stoneleaf Systems Application

The local Stoneleaf Systems environment uses:

```text
10.20.0.0/16
```

Major networks include:

```text
10.20.10.0/24 — Management
10.20.20.0/24 — Servers
10.20.30.0/24 — Workstations
10.20.40.0/24 — IT Administration
10.20.50.0/24 — Corporate Wireless
10.20.60.0/24 — Guest Wireless
10.20.70.0/24 — Lab/Test
10.20.80.0/24 — VPN
```

**Evidence:**

`IP-Addressing-Plan.md`

**Status:** Documented

---

## Subnetting

### Skills

* Determine network addresses.
* Determine usable host ranges.
* Determine broadcast addresses.
* Understand prefix lengths.
* Understand subnet masks.
* Understand VLSM.
* Understand CIDR.

### Stoneleaf Systems Application

Initial networks use `/24` subnets for simplicity.

Example:

```text
Network:     10.20.20.0/24
Mask:        255.255.255.0
Gateway:     10.20.20.1
Hosts:       10.20.20.1–10.20.20.254
Broadcast:   10.20.20.255
```

Later exercises may use smaller subnets to practice VLSM.

**Status:** In Progress

---

## IPv6

### Skills

* IPv6 addressing
* Link-local addresses
* Global unicast
* Multicast
* IPv6 prefix notation
* Dual-stack concepts

### Stoneleaf Systems Application

The environment will initially focus on IPv4.

IPv6 will later be introduced in the Lab/Test environment for configuration and troubleshooting exercises.

**Status:** Planned

---

# 4. Common Ports and Protocols

Stoneleaf Systems will use common network protocols in realistic scenarios.

| Protocol   | Typical Purpose               | Stoneleaf Application         |
| ---------- | ----------------------------- | ----------------------------- |
| DNS        | Name resolution               | Internal domain resolution    |
| DHCP       | Dynamic addressing            | Client configuration          |
| HTTP/HTTPS | Web traffic                   | Web and cloud applications    |
| SSH        | Secure remote shell           | Linux administration          |
| RDP        | Windows remote administration | Server/workstation management |
| SMB        | Windows file sharing          | Department file shares        |
| LDAP/LDAPS | Directory services            | Active Directory              |
| NTP        | Time synchronization          | Server/client time            |
| SNMP       | Monitoring                    | Network monitoring            |
| Syslog     | Central logging               | pfSense/Linux logging         |
| SMTP       | Email transport concepts      | Microsoft 365 scenarios       |

### Practical Tasks

* Identify services by port.
* Test service reachability.
* Configure firewall rules.
* Analyze failed connections.
* Determine whether a failure involves DNS, transport, authentication, or the application.

**Status:** Planned

---

# 5. Network Devices

Stoneleaf Systems will provide experience with the logical purpose of common networking devices.

---

## Router

Stoneleaf Systems routing will primarily be performed by:

```text
SL-FW01
```

Skills include:

* Default routes
* Inter-network routing
* Static routes
* Gateway configuration
* Route troubleshooting

**Status:** Planned

---

## Firewall

Primary firewall:

```text
SL-FW01
```

Platform:

```text
pfSense
```

Skills include:

* Stateful firewall rules
* NAT
* Network segmentation
* Rule ordering
* Traffic logging
* VPN
* Troubleshooting blocked traffic

**Status:** Planned

---

## Switch

Switching concepts will include:

* Ethernet
* MAC addresses
* VLANs
* Trunking
* Access ports
* Layer 2 forwarding
* Broadcast domains

Physical managed switching may be added later.

Virtual networking will initially simulate portions of the switching environment.

**Status:** Planned

---

## Wireless Access Points

Future exercises may include:

* Corporate wireless
* Guest wireless
* SSIDs
* Authentication
* Channel considerations
* Wireless security
* Network separation

**Status:** Planned

---

# 6. Network Topologies

Stoneleaf Systems will document and understand:

* Star topology
* Point-to-point connections
* Client/server architecture
* LAN
* WAN
* VPN connectivity
* Hybrid cloud architecture
* Virtual networking

### Stoneleaf Application

The primary architecture consists of:

```text
Internet
   │
SL-FW01
   │
Internal Networks
   │
├── Servers
├── Workstations
├── IT Administration
└── Other VLANs
   │
   └── Microsoft Azure
```

**Evidence:**

`Logical-Architecture.md`

**Status:** Documented

---

# 7. Network Implementation

This area focuses on actually building and configuring the Stoneleaf Systems network.

---

## VLAN Configuration

Planned VLANs:

| VLAN | Purpose            |
| ---: | ------------------ |
|   10 | Management         |
|   20 | Servers            |
|   30 | Workstations       |
|   40 | IT Administration  |
|   50 | Corporate Wireless |
|   60 | Guest Wireless     |
|   70 | Lab/Test           |
|   80 | VPN                |

### Skills

* Create VLANs.
* Assign interfaces.
* Understand tagged traffic.
* Understand access vs. trunk concepts.
* Configure gateways.
* Validate connectivity.
* Restrict traffic between VLANs.

**Status:** Planned

---

## Routing

### Tasks

* Configure default gateway.
* Configure inter-VLAN routing.
* Review routing tables.
* Test routes.
* Create static routes where required.
* Troubleshoot missing or incorrect routes.

### Tools

```text
route
tracert
traceroute
Get-NetRoute
```

**Status:** Planned

---

# 8. DHCP

Stoneleaf Systems will configure DHCP for client networks.

### Skills

* Create scopes.
* Configure exclusions.
* Configure leases.
* Configure reservations.
* Configure DHCP options.
* Provide default gateway.
* Provide DNS servers.
* Renew client leases.
* Troubleshoot DHCP failures.

### Example Workstation Scope

```text
Network:
10.20.30.0/24

DHCP Pool:
10.20.30.100–10.20.30.199

Gateway:
10.20.30.1

DNS:
10.20.20.10
```

### Troubleshooting Exercises

* Incorrect DNS option
* Exhausted scope
* DHCP server unavailable
* APIPA address
* Incorrect gateway
* Duplicate address

**Status:** Planned

---

# 9. DNS

Internal DNS will be a major part of the Stoneleaf Systems environment.

Primary server:

```text
SL-DC01
10.20.20.10
```

Future secondary server:

```text
SL-DC02
10.20.20.11
```

### Skills

* Forward lookup
* Reverse lookup
* A records
* PTR records
* DNS caching
* DNS forwarding
* Name-resolution testing
* Client DNS configuration

### Tools

```text
nslookup
Resolve-DnsName
ipconfig /displaydns
ipconfig /flushdns
```

### Troubleshooting Scenarios

* Incorrect client DNS server
* Missing DNS record
* Stale cache
* DNS server unavailable
* DNS works externally but not internally

**Status:** Planned

---

# 10. NAT

pfSense will provide Network Address Translation.

### Skills

* Understand private-to-public translation.
* Understand source NAT.
* Understand port forwarding.
* Understand outbound NAT.
* Troubleshoot NAT problems.

### Stoneleaf Application

Internal networks such as:

```text
10.20.20.0/24
10.20.30.0/24
```

will reach external networks through `SL-FW01`.

**Status:** Planned

---

# 11. Wireless Networking

Stoneleaf Systems will eventually simulate two wireless environments.

```text
Corporate Wireless
Guest Wireless
```

### Corporate Wireless

Network:

```text
10.20.50.0/24
```

### Guest Wireless

Network:

```text
10.20.60.0/24
```

### Skills

* SSIDs
* Encryption
* Authentication
* 2.4 GHz / 5 GHz concepts
* Wireless channels
* Signal strength
* Interference
* Guest isolation

**Status:** Planned

---

# 12. Virtual Networking

VMware Workstation provides the initial virtual networking platform.

### Skills

* Virtual NICs
* Virtual switches
* NAT networking
* Host-only networking
* Bridged networking
* Network isolation
* Multiple virtual networks

### Stoneleaf Application

Virtual networks will allow the lab to simulate multiple enterprise network segments without requiring extensive physical hardware.

**Status:** Planned

---

# 13. Cloud Networking

Microsoft Azure will provide cloud networking experience.

Planned Azure address space:

```text
10.50.0.0/16
```

Potential subnets include:

```text
10.50.10.0/24 — Servers
10.50.20.0/24 — Management
10.50.30.0/24 — Applications
10.50.40.0/24 — Security
```

### Skills

* Azure Virtual Networks
* Subnets
* Routing
* Network Security Groups
* Cloud virtual machines
* Hybrid connectivity
* VPN gateways

**Status:** Planned

---

# 14. VPN

Stoneleaf Systems will eventually configure secure VPN connectivity.

Potential uses include:

* Remote-user VPN
* Site-to-site VPN
* Azure connectivity

Remote VPN network:

```text
10.20.80.0/24
```

### Skills

* VPN concepts
* Authentication
* Encryption
* Remote-access VPN
* Site-to-site VPN
* Routing through VPN tunnels
* VPN troubleshooting

**Status:** Planned

---

# 15. Network Operations

Stoneleaf Systems will operate the network as if it supports a functioning business.

---

## Network Documentation

Current documentation includes:

```text
Logical-Architecture.md
IP-Addressing-Plan.md
Naming-Standards.md
Change-Management.md
Ticket-Standards.md
```

Future documentation will include:

* Network topology
* VLAN configurations
* Firewall rules
* DHCP scopes
* DNS configuration
* Network inventory
* Cloud networking

**Status:** In Progress

---

# 16. Network Diagrams

The repository will eventually include:

```text
Stoneleaf-Logical-Architecture.png
Stoneleaf-Network-Topology.png
Stoneleaf-VLAN-Design.png
Stoneleaf-Azure-Architecture.png
```

Diagrams will identify:

* Networks
* Devices
* Gateways
* Servers
* Cloud connections
* Security boundaries

**Status:** Planned

---

# 17. Network Monitoring

Stoneleaf Systems will eventually monitor:

* Device availability
* Interface status
* Latency
* Packet loss
* CPU utilization
* Memory usage
* Bandwidth
* Service availability
* Firewall activity

Potential monitoring server:

```text
SL-MON01
```

**Status:** Planned

---

# 18. Logging

Centralized logging may collect information from:

* pfSense
* Windows Server
* Windows clients
* Linux
* Azure
* Network devices

Potential server:

```text
SL-LOG01
```

### Skills

* Syslog
* Windows events
* Log aggregation
* Event correlation
* Troubleshooting from logs

**Status:** Planned

---

# 19. Network Baselines

Normal network behavior should eventually be documented.

Examples:

* Typical latency
* Normal bandwidth
* Normal CPU usage
* Expected DNS response
* Expected DHCP leases
* Normal interface utilization

Baselines can then be compared with abnormal conditions.

**Status:** Planned

---

# 20. Change Management

Networking changes will follow:

`Change-Management.md`

Examples include:

```text
CHG-#### — Create Server VLAN

CHG-#### — Modify Firewall Rules

CHG-#### — Add DHCP Scope

CHG-#### — Configure Azure VPN
```

### Skills Demonstrated

* Change planning
* Risk assessment
* Implementation planning
* Rollback
* Validation
* Documentation

**Status:** Documented

---

# 21. High Availability and Recovery

Stoneleaf Systems will introduce availability concepts through:

* Secondary domain controller
* Redundant DNS
* Backups
* Configuration exports
* Recovery testing
* Cloud resources

Network recovery scenarios may include:

* Firewall failure
* DNS failure
* DHCP failure
* VPN failure
* Routing failure

**Status:** Planned

---

# 22. Network Security

Network security will be integrated into normal infrastructure design.

---

## Segmentation

Stoneleaf Systems will separate systems according to function.

Examples:

```text
Servers
Workstations
IT Administration
Corporate Wireless
Guest Wireless
Lab/Test
```

### Skills

* VLAN segmentation
* Firewall boundaries
* Least privilege
* Traffic restrictions

**Status:** Planned

---

## Firewall Rules

Firewall rules will follow descriptive naming.

Examples:

```text
Allow-Workstations-to-DNS
Allow-ITAdmin-to-Servers-RDP
Allow-Servers-to-Internet-HTTPS
Deny-Guest-to-Internal
```

### Skills

* Source
* Destination
* Protocol
* Port
* Allow/deny
* Rule ordering
* Logging
* Validation

**Status:** Planned

---

# 23. Access Control

Network access should be determined by business need.

Examples:

* Guest clients should not access internal servers.
* Normal workstations should not access management interfaces.
* IT Administration should have greater infrastructure access.
* VPN users should only reach authorized resources.

**Status:** Planned

---

# 24. Secure Protocols

Stoneleaf Systems should favor secure protocols where practical.

Examples:

```text
SSH instead of Telnet
HTTPS instead of HTTP for management
LDAPS where appropriate
Secure VPN protocols
```

**Status:** Planned

---

# 25. Least Privilege

Network access will follow the same least-privilege principles used throughout the Stoneleaf Systems environment.

Users and devices should only communicate with resources necessary for their role.

**Status:** Documented

---

# 26. Guest Network Security

Guest clients will use:

```text
10.20.60.0/24
```

Guest traffic should be prevented from accessing:

* Servers
* Domain controllers
* Employee workstations
* IT management
* Internal applications

Internet access may still be permitted.

**Status:** Planned

---

# 27. Network Troubleshooting Methodology

Stoneleaf Systems troubleshooting exercises will follow a structured process.

1. Identify the problem.
2. Establish a theory of probable cause.
3. Test the theory.
4. Establish a plan of action.
5. Implement the solution.
6. Verify full functionality.
7. Document findings, actions, and results.

Troubleshooting results will be stored as help desk tickets or project documentation.

**Status:** Planned

---

# 28. Network Troubleshooting Tools

Stoneleaf Systems will practice tools such as:

### Windows

```text
ipconfig
ping
tracert
nslookup
netstat
arp
route
pathping
```

### PowerShell

```powershell
Get-NetIPAddress
Get-NetAdapter
Get-NetRoute
Test-NetConnection
Resolve-DnsName
```

### Linux

```bash
ip addr
ip route
ping
traceroute
ss
dig
nslookup
arp
```

Additional tools may be introduced later.

**Status:** Planned

---

# 29. Physical Connectivity Troubleshooting

Even though much of Stoneleaf Systems is virtualized, physical networking concepts will still be studied and demonstrated where possible.

Skills include:

* Ethernet cabling
* RJ45 connectors
* Cable categories
* Fiber concepts
* Link lights
* Interface status
* Speed
* Duplex
* Cable failure
* Port failure

**Status:** Planned

---

# 30. IP Configuration Troubleshooting

Planned scenarios include:

* Incorrect static IP
* Incorrect subnet mask
* Incorrect gateway
* Duplicate IP
* APIPA
* DHCP failure
* Wrong DNS server

Example ticket:

```text
INC-#### — Alicia Grant Workstation Cannot Reach Internal Network
```

**Status:** Planned

---

# 31. DNS Troubleshooting

Planned scenarios include:

* Missing record
* Incorrect DNS server
* DNS server unavailable
* Stale cache
* Incorrect DNS forwarding

Example:

```text
INC-#### — Emily Parker Cannot Resolve Internal DNS
```

**Status:** Planned

---

# 32. DHCP Troubleshooting

Planned scenarios include:

* Scope exhaustion
* Incorrect option
* DHCP service stopped
* Wrong subnet
* DHCP reservation problem
* Client fails to renew

**Status:** Planned

---

# 33. VLAN Troubleshooting

Planned failures may include:

* Incorrect VLAN assignment
* Missing VLAN
* Incorrect trunk configuration
* Firewall rules blocking VLAN
* Wrong default gateway

**Status:** Planned

---

# 34. Routing Troubleshooting

Planned scenarios include:

* Missing route
* Wrong gateway
* Incorrect static route
* VPN route missing
* Azure/local routing conflict

Tools may include:

```text
tracert
traceroute
route print
Get-NetRoute
```

**Status:** Planned

---

# 35. Firewall Troubleshooting

Scenarios may include:

* Incorrect source
* Incorrect destination
* Wrong port
* Wrong protocol
* Rule ordering
* Missing allow rule
* NAT failure

Firewall logs will be used to support troubleshooting.

**Status:** Planned

---

# 36. Performance Troubleshooting

Later network scenarios may involve:

* High latency
* Packet loss
* Bandwidth saturation
* High resource utilization
* DNS delays
* Wi-Fi interference
* Server performance issues

**Status:** Planned

---

# 37. Network+ Practical Project Matrix

| Skill                 | Stoneleaf Systems Project     | Evidence                  | Status      |
| --------------------- | ----------------------------- | ------------------------- | ----------- |
| IPv4 addressing       | Enterprise addressing plan    | `IP-Addressing-Plan.md`   | Documented  |
| Subnetting            | `/24` enterprise networks     | IP plan                   | In Progress |
| Network architecture  | Hybrid logical design         | `Logical-Architecture.md` | Documented  |
| Network documentation | Foundation documentation      | GitHub                    | In Progress |
| Naming conventions    | Infrastructure naming         | `Naming-Standards.md`     | Documented  |
| Change management     | Network change workflow       | `Change-Management.md`    | Documented  |
| Ticketing             | Troubleshooting documentation | `Ticket-Standards.md`     | Documented  |
| pfSense               | Enterprise firewall           | `SL-FW01`                 | Planned     |
| VLANs                 | Network segmentation          | VLANs 10–80               | Planned     |
| Routing               | Inter-VLAN routing            | `SL-FW01`                 | Planned     |
| DNS                   | Internal DNS                  | `SL-DC01`                 | Planned     |
| DHCP                  | Client addressing             | Workstation networks      | Planned     |
| NAT                   | Internet connectivity         | `SL-FW01`                 | Planned     |
| Windows networking    | Domain clients                | 9 workstations            | Planned     |
| Linux networking      | Ubuntu server                 | `SL-LNX01`                | Planned     |
| Wireless              | Corporate/Guest networks      | VLAN 50/60                | Planned     |
| VPN                   | Remote access                 | VLAN 80                   | Planned     |
| Cloud networking      | Azure VNet                    | `10.50.0.0/16`            | Planned     |
| Monitoring            | Network monitoring            | `SL-MON01`                | Planned     |
| Logging               | Centralized logs              | `SL-LOG01`                | Planned     |
| Network security      | Firewall/segmentation         | Security controls         | Planned     |
| Troubleshooting       | Injected failures             | Incident tickets          | Planned     |

---

# 38. Portfolio Evidence Requirements

A networking skill should ideally include more than a statement that it was studied.

Strong evidence should contain:

1. Requirement
2. Design
3. Configuration
4. Screenshot or command output
5. Validation
6. Troubleshooting where appropriate
7. Final documentation

Example:

```text
Skill:
DHCP

Evidence:

- Designed DHCP scope.
- Configured scope.
- Configured gateway and DNS options.
- Connected Windows workstation.
- Verified lease with ipconfig /all.
- Introduced incorrect DNS option.
- Diagnosed failure.
- Corrected configuration.
- Documented incident ticket.
```

This demonstrates significantly more practical ability than simply listing DHCP as a skill.

---

# 39. Certification-to-Portfolio Strategy

Network+ concepts should be converted into portfolio projects whenever practical.

Instead of only learning:

```text
What is DHCP?
```

Stoneleaf Systems will demonstrate:

```text
Design DHCP network
        ↓
Configure DHCP
        ↓
Connect client
        ↓
Verify lease
        ↓
Break configuration
        ↓
Troubleshoot failure
        ↓
Repair service
        ↓
Document ticket
```

The same methodology will be applied to:

* DNS
* Routing
* VLANs
* Firewalls
* VPNs
* Cloud networking
* Monitoring
* Network security

---

# 40. Phase Relationship

Network+ concepts will appear throughout multiple Stoneleaf Systems phases.

| Repository Section                   | Network+ Relationship                   |
| ------------------------------------ | --------------------------------------- |
| `00-Foundation`                      | Planning and network documentation      |
| `01-Network-Infrastructure`          | Primary hands-on networking             |
| `02-Windows-Server-Active-Directory` | DNS, DHCP, domain networking            |
| `03-Endpoint-Administration`         | Client network configuration            |
| `04-Linux-Administration`            | Linux networking                        |
| `05-IT-Operations`                   | Tickets and operational troubleshooting |
| `07-Virtualization`                  | Virtual networking                      |
| `08-Cloud-Infrastructure`            | Azure networking                        |
| `09-Security`                        | Network hardening                       |
| `10-Monitoring-Logging`              | Network visibility                      |
| `11-Backup-Disaster-Recovery`        | Availability and recovery               |
| `12-Projects`                        | Integrated networking projects          |

---

# 41. Final Goal

By the end of the Stoneleaf Systems project, the Network+ portion of the portfolio should demonstrate the ability to:

* Design an IPv4 network.
* Understand subnetting.
* Configure network services.
* Configure routing.
* Configure VLANs.
* Administer a firewall.
* Configure DNS.
* Configure DHCP.
* Implement NAT.
* Configure remote access.
* Understand wired and wireless networking.
* Work with virtual networks.
* Work with cloud networks.
* Document network infrastructure.
* Monitor network systems.
* Apply network security controls.
* Troubleshoot network problems systematically.
* Explain the business reason behind network configurations.

The final objective is to demonstrate both Network+ knowledge and the ability to apply that knowledge in a realistic IT environment.

---

# Foundation Phase Completion

With this document complete, the planned documentation for `00-Foundation` consists of:

```text
00-Foundation/
│
├── README.md
├── Organization-Overview.md
├── Departments-and-Users.md
├── Business-Requirements.md
├── Technical-Requirements.md
├── Logical-Architecture.md
├── IP-Addressing-Plan.md
├── Naming-Standards.md
├── Documentation-Standards.md
├── Change-Management.md
├── Ticket-Standards.md
└── NetworkPlus-Skills-Matrix.md
```

The Foundation phase establishes the design standards that will guide the technical implementation of Stoneleaf Systems.

---

## Document Status

**Organization:** Stoneleaf Systems

**Certification Alignment:** CompTIA Network+ N10-009

**Current Phase:** `00-Foundation`

**Current Document:** `NetworkPlus-Skills-Matrix.md`

**Foundation Documents:** 12 of 12

**Foundation Status:** Documentation Complete

**Next Phase:** `01-Network-Infrastructure`

**Next Document:** `01-Network-Infrastructure/README.md`
