# Stoneleaf Systems — Logical Architecture

## Purpose

This document defines the high-level logical architecture for the Stoneleaf Systems enterprise IT homelab.

The architecture is designed to support a fictional organization of approximately **40 employees** while remaining practical to operate within a home virtualization environment.

Stoneleaf Systems will use a **hybrid architecture** combining:

* Local virtualized infrastructure
* Windows Server
* Active Directory
* Windows 11 endpoints
* Linux systems
* pfSense networking
* Microsoft Azure
* Microsoft Entra ID
* Security, monitoring, backup, and automation services

The environment will simulate the structure and administrative responsibilities of a real small-to-medium-sized business.

---

# 1. Architecture Overview

Stoneleaf Systems will operate primarily from a local VMware-based environment connected to Microsoft Azure.

The logical environment will consist of five major layers:

1. Network and security
2. Server infrastructure
3. Endpoint infrastructure
4. Cloud infrastructure
5. IT operations and management

```text
Internet
   │
   │
   ▼
┌──────────────────────┐
│      pfSense         │
│    SL-FW01           │
└──────────┬───────────┘
           │
           ▼
┌─────────────────────────────────────────────┐
│          Stoneleaf Internal Network         │
│                                             │
│   ┌──────────────┐     ┌────────────────┐  │
│   │   Servers    │     │  Workstations  │  │
│   │              │     │                │  │
│   │ DC / DNS     │     │ Executive      │  │
│   │ DHCP         │     │ IT             │  │
│   │ File Server  │     │ Operations     │  │
│   │ Monitoring   │     │ Sales          │  │
│   │ Logging      │     │ Customer Svc   │  │
│   │ Linux        │     │ Finance        │  │
│   └──────┬───────┘     │ HR/Admin       │  │
│          │             │ Remote/Test    │  │
│          │             └────────────────┘  │
└──────────┼──────────────────────────────────┘
           │
           │ Secure Hybrid Connectivity
           ▼
┌──────────────────────────────┐
│       Microsoft Azure        │
│                              │
│  Microsoft Entra ID          │
│  Azure Virtual Network       │
│  Azure Virtual Machines      │
│  Cloud Security              │
│  Monitoring                  │
│  Hybrid Identity             │
└──────────────────────────────┘
```

---

# 2. Virtualization Layer

The local Stoneleaf Systems infrastructure will run primarily in:

**VMware Workstation**

VMware will host the virtual machines used throughout the lab.

Planned virtual systems include:

* pfSense firewall
* Windows Server domain controllers
* Windows Server file services
* Windows Server management systems
* Windows 11 workstations
* Ubuntu Linux systems
* Monitoring systems
* Logging systems
* Security systems
* Test systems

Virtual machines will be created gradually as each lab phase requires them.

---

# 3. Network Edge

The primary network edge device will be:

`SL-FW01`

**Platform:** pfSense

The firewall will provide the boundary between the Stoneleaf Systems environment and external networks.

Primary responsibilities will include:

* Internet connectivity
* Network Address Translation
* Firewall rules
* Routing
* VPN connectivity
* Network segmentation
* Traffic logging
* Troubleshooting

The firewall will eventually control traffic between VLANs and internal network segments.

---

# 4. Internal Network

Stoneleaf Systems will initially use a simplified internal network.

As the lab develops, the environment will be segmented into multiple logical networks.

Potential network segments include:

```text
Management
Servers
Workstations
IT Administration
Wireless
Guest Wireless
Lab/Test
```

Each segment will eventually receive its own IPv4 subnet and security rules where appropriate.

The detailed addressing structure will be defined in:

`IP-Addressing-Plan.md`

---

# 5. Active Directory Infrastructure

Microsoft Active Directory Domain Services will provide centralized identity and authentication for the local Windows environment.

Active Directory will manage:

* 40 fictional employee accounts
* Administrative accounts
* Workstations
* Servers
* Security groups
* Organizational Units
* Service accounts
* Group Policy

The Active Directory environment will be organized around the Stoneleaf Systems departmental structure.

---

# 6. Domain Controllers

Stoneleaf Systems will begin with one primary domain controller.

Planned initial server:

`SL-DC01`

Primary roles:

* Active Directory Domain Services
* DNS

As the lab expands, a second domain controller may be added:

`SL-DC02`

A second domain controller would provide experience with:

* Active Directory replication
* DNS redundancy
* Authentication redundancy
* Domain controller failure scenarios
* Recovery testing

---

# 7. DHCP Infrastructure

DHCP will provide dynamic IPv4 configuration to approved client systems.

Planned DHCP responsibilities include:

* IP address leases
* DNS server configuration
* Default gateway configuration
* DHCP options
* Reservations
* Scope management

The final server responsible for DHCP will be defined during implementation.

---

# 8. File Services

Stoneleaf Systems will deploy centralized file services.

Planned server:

`SL-FS01`

File services will provide department-based shared storage.

Example shares may include:

```text
Executive
IT
Operations
Sales
Customer-Service
Finance
HR
Company-Shared
```

Permissions will be controlled through Active Directory security groups.

Sensitive resources such as Finance and Human Resources will receive stricter access controls.

---

# 9. Windows Workstations

Stoneleaf Systems represents approximately **40 employees**, but the homelab will not require 40 individual virtual workstations.

Instead, the environment will use representative Windows 11 endpoints for each major department and use case.

Planned workstations:

| Hostname         | Purpose                          |
| ---------------- | -------------------------------- |
| `SL-WS-EXEC01`   | Executive Management             |
| `SL-WS-IT01`     | Information Technology           |
| `SL-WS-OPS01`    | Operations                       |
| `SL-WS-SALES01`  | Sales                            |
| `SL-WS-CS01`     | Customer Service                 |
| `SL-WS-FIN01`    | Finance                          |
| `SL-WS-HR01`     | Human Resources / Administration |
| `SL-WS-REMOTE01` | Remote employee testing          |
| `SL-WS-TEST01`   | IT testing and troubleshooting   |

This provides **nine representative workstations** for the 40-user organization.

Different fictional employees can authenticate to the appropriate departmental workstation depending on the scenario being tested.

---

# 10. Endpoint Management

Windows endpoints will eventually be centrally managed using technologies such as:

* Active Directory
* Group Policy
* Microsoft Entra ID
* Microsoft Intune where available
* Windows Update
* Microsoft Defender
* PowerShell

Endpoint administration scenarios may include:

* Domain joining
* User profile creation
* Software installation
* Group Policy deployment
* Security configuration
* Troubleshooting
* Patch management
* Remote administration

---

# 11. Linux Infrastructure

Ubuntu Linux will be included to provide hands-on Linux administration experience.

Initial Linux system:

`SL-LNX01`

Potential roles include:

* Administrative tools
* Web services
* Monitoring
* Logging
* Scripting
* Network utilities
* Security tools

Additional Linux systems may be added later if required.

---

# 12. Monitoring Infrastructure

Stoneleaf Systems will eventually deploy centralized monitoring.

Planned monitoring responsibilities include:

* Server availability
* Network availability
* CPU utilization
* Memory utilization
* Disk usage
* Critical service status
* Connectivity
* Backup status

A future monitoring server may use a hostname such as:

`SL-MON01`

The monitoring platform will be selected during the Monitoring and Logging phase.

---

# 13. Centralized Logging

Important systems will eventually send logs to a centralized platform.

Potential log sources include:

* Domain controllers
* Windows servers
* Windows workstations
* Ubuntu Linux
* pfSense
* Azure
* Authentication systems
* Security applications

A future logging server may use:

`SL-LOG01`

or

`SL-SIEM01`

depending on the final technology selected.

---

# 14. Microsoft Azure Architecture

Microsoft Azure will extend the Stoneleaf Systems environment into the cloud.

Azure components may include:

* Azure Virtual Network
* Azure subnets
* Azure Virtual Machines
* Network Security Groups
* Storage
* Monitoring
* Cloud security controls
* Backup
* Hybrid connectivity

The Azure environment will be designed as an extension of the local Stoneleaf Systems infrastructure rather than as an unrelated cloud lab.

---

# 15. Microsoft Entra ID

Microsoft Entra ID will provide cloud-based identity capabilities.

Planned features include:

* User identities
* Security groups
* Administrative roles
* Multi-factor authentication
* Cloud application access
* Role-Based Access Control
* Hybrid identity

Where technically and financially practical, local Active Directory users will be integrated with Entra ID.

---

# 16. Hybrid Connectivity

The long-term architecture will connect the local Stoneleaf Systems network with Microsoft Azure.

Potential connectivity methods include:

* Site-to-site VPN
* Secure remote-access VPN
* Azure VPN Gateway
* pfSense VPN connectivity

This will allow the lab to demonstrate hybrid networking concepts.

---

# 17. Hybrid Identity Architecture

The lab may eventually synchronize selected local identities with Microsoft Entra ID.

Logical flow:

```text
Active Directory
      │
      │ Identity Synchronization
      ▼
Microsoft Entra ID
      │
      ▼
Microsoft 365 / Azure Resources
```

This will demonstrate the relationship between traditional domain identity and modern cloud identity.

---

# 18. Administrative Access

Administrative access will be separated from standard employee activity.

Example:

```text
Standard Account
sdempsey

Administrative Account
sdempsey-admin
```

Administrative accounts will be used for tasks such as:

* Active Directory management
* Server management
* Network administration
* Cloud administration
* Security administration

Administrative permissions will follow least-privilege principles.

---

# 19. Security Architecture

Security will be integrated throughout the Stoneleaf Systems architecture.

Security layers will include:

### Network Security

* pfSense
* Firewall rules
* Network segmentation
* VPN
* Controlled routing

### Identity Security

* Active Directory
* Microsoft Entra ID
* Least privilege
* Separate administrative accounts
* MFA where available
* Group-based permissions

### Endpoint Security

* Microsoft Defender
* Windows Firewall
* Group Policy
* Patch management
* User restrictions

### Server Security

* Server hardening
* Firewall controls
* Limited administrator access
* Logging
* Updates

### Cloud Security

* Azure Network Security Groups
* Role-Based Access Control
* MFA
* Monitoring
* Least privilege

---

# 20. Backup Architecture

Stoneleaf Systems will eventually deploy backup capabilities for important systems and information.

Potential backup targets include:

* File server data
* Virtual machines
* Server configurations
* Network configurations
* Scripts
* Documentation
* Cloud resources

Backup systems should be isolated from normal user access where practical.

---

# 21. Disaster Recovery

The architecture will support testing of common recovery scenarios.

Examples include:

* Domain controller failure
* Deleted user account
* Lost file
* Failed workstation
* Firewall configuration failure
* Corrupted virtual machine
* Failed server
* Cloud connectivity failure

Recovery procedures will be developed during the Backup and Disaster Recovery phase.

---

# 22. IT Operations Layer

Stoneleaf Systems will operate as a simulated IT department.

Operational workflows will interact with the technical architecture.

Examples include:

```text
Employee
   │
   ▼
Help Desk Ticket
   │
   ▼
IT Technician
   │
   ▼
Troubleshooting
   │
   ├── Active Directory
   ├── Workstation
   ├── Server
   ├── Network
   ├── Cloud
   └── Application
   │
   ▼
Resolution
   │
   ▼
Ticket Documentation
```

This allows technical configuration and operational support skills to be demonstrated together.

---

# 23. Automation Layer

PowerShell and Bash will be used throughout the environment.

PowerShell will primarily support:

* Active Directory
* Windows Server
* Windows endpoints
* Microsoft Azure
* Reporting
* User management
* Automation

Bash will primarily support:

* Linux administration
* Networking
* Log analysis
* System maintenance
* Automation

---

# 24. Logical System Inventory

The initial and planned logical infrastructure includes:

| System           | Role                               |
| ---------------- | ---------------------------------- |
| `SL-FW01`        | pfSense firewall/router            |
| `SL-DC01`        | Primary domain controller and DNS  |
| `SL-DC02`        | Future secondary domain controller |
| `SL-FS01`        | File server                        |
| `SL-LNX01`       | Ubuntu Linux server                |
| `SL-MON01`       | Future monitoring server           |
| `SL-LOG01`       | Future centralized logging server  |
| `SL-WS-EXEC01`   | Executive workstation              |
| `SL-WS-IT01`     | IT workstation                     |
| `SL-WS-OPS01`    | Operations workstation             |
| `SL-WS-SALES01`  | Sales workstation                  |
| `SL-WS-CS01`     | Customer Service workstation       |
| `SL-WS-FIN01`    | Finance workstation                |
| `SL-WS-HR01`     | HR/Admin workstation               |
| `SL-WS-REMOTE01` | Remote-user workstation            |
| `SL-WS-TEST01`   | IT testing workstation             |

Additional systems will be added only when a defined business or technical requirement requires them.

---

# 25. Architecture Principles

## Representative Infrastructure

The lab will represent a 40-user business without requiring one virtual machine for every employee.

## Hybrid Design

Local infrastructure and Microsoft Azure will operate as parts of the same logical environment.

## Least Privilege

Access will be restricted according to job role and administrative responsibility.

## Segmentation

Networks and systems will be logically separated when doing so improves security and manageability.

## Centralized Administration

Identity, networking, endpoints, servers, and cloud resources should be centrally manageable wherever practical.

## Scalability

The architecture should allow the environment to grow without requiring a complete redesign.

## Documentation

Important architecture changes must be reflected in repository documentation.

---

# 26. Future Architecture Expansion

Later phases may introduce:

* Additional VLANs
* Secondary domain controller
* Azure virtual machines
* Site-to-site VPN
* Intune
* Microsoft 365
* SIEM
* Centralized monitoring
* Vulnerability scanning
* Backup infrastructure
* Additional Linux services
* Wireless network simulation
* Guest network
* More automation
* Additional cloud security controls

These capabilities will be introduced gradually rather than deployed all at once.

---

## Document Status

**Organization:** Stoneleaf Systems

**Users Represented:** 40

**Representative Windows Workstations:** 9

**Infrastructure Model:** Hybrid local/cloud

**Primary Virtualization Platform:** VMware Workstation

**Primary Cloud Platform:** Microsoft Azure

**Current Phase:** `00-Foundation`

**Current Document:** `Logical-Architecture.md`

**Next Document:** `IP-Addressing-Plan.md`

