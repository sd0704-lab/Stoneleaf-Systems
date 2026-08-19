# Stoneleaf Systems — Technical Requirements

## Purpose

This document translates the business requirements of Stoneleaf Systems into technical requirements for the lab environment.

These requirements define **what the IT environment must technically provide** in order to support the organization’s users, systems, security, operations, and future growth.

---

# 1. Virtualization Platform

Stoneleaf Systems requires a local virtualization platform capable of hosting multiple enterprise systems simultaneously.

The environment should support:

* Windows Server virtual machines
* Windows 11 workstations
* Ubuntu Linux systems
* pfSense
* Monitoring systems
* Logging systems
* Test systems
* Additional infrastructure as the lab expands

The primary local virtualization platform will be:

* VMware Workstation

Virtual machines should use documented names, IP addresses, roles, and resource allocations.

---

# 2. Windows Server Infrastructure

The environment requires Windows Server systems to support core enterprise services.

Planned server roles include:

* Active Directory Domain Services
* DNS
* DHCP
* File services
* Group Policy administration
* Administrative tools
* Logging
* Monitoring
* Backup-related services

Servers must use static IP addressing and consistent naming standards.

---

# 3. Active Directory Domain Services

Stoneleaf Systems requires centralized Windows identity management.

Active Directory must support:

* User accounts
* Computer accounts
* Security groups
* Organizational Units
* Group Policy
* Authentication
* Authorization
* Department-based administration
* Administrative account separation
* Service accounts

The directory design should support the organization’s seven departments.

---

# 4. Active Directory Organizational Units

The Active Directory environment should use a structured OU design.

Planned top-level categories include:

```text
Stoneleaf-Systems
│
├── Users
├── Admin-Accounts
├── Groups
├── Servers
├── Workstations
└── Service-Accounts
```

Department-specific OUs will exist under the user structure.

Examples include:

```text
Users
├── Executive
├── IT
├── Operations
├── Sales
├── Customer-Service
├── Finance
└── HR-Administration
```

The OU structure should support Group Policy application and delegated administration.

---

# 5. DNS

Stoneleaf Systems requires internal DNS services.

DNS must support:

* Active Directory name resolution
* Server name resolution
* Workstation name resolution
* Internal service discovery
* Forward DNS lookups
* Reverse DNS lookups where practical
* DNS troubleshooting

Domain-integrated DNS should be used where appropriate.

---

# 6. DHCP

The environment requires centralized DHCP services for dynamically addressed devices.

DHCP should provide:

* IPv4 addresses
* Default gateway information
* DNS server information
* Lease management
* Reserved addresses where needed
* Defined scopes

Servers, network infrastructure, and other critical systems should generally use static or reserved IP addresses.

---

# 7. IPv4 Addressing

Stoneleaf Systems requires a documented IPv4 addressing plan.

The addressing design must define:

* Network ranges
* Subnets
* Default gateways
* Static address ranges
* DHCP ranges
* Reserved addresses
* Server addresses
* Network device addresses
* Future VLAN addressing

The final addressing scheme will be documented in:

`IP-Addressing-Plan.md`

---

# 8. Network Segmentation

The network design should support logical segmentation.

Future segments may include:

* Servers
* Workstations
* IT administration
* Wireless clients
* Guest wireless
* Management interfaces
* Lab systems
* Cloud-connected resources

VLANs may be introduced as the lab progresses.

Traffic between segments should be controlled by firewall rules.

---

# 9. Firewall

Stoneleaf Systems requires a centrally managed firewall.

The firewall platform will be:

* pfSense

The firewall should support:

* NAT
* DHCP where required
* Routing
* Firewall rules
* Network segmentation
* VPN
* Logging
* DNS forwarding where appropriate
* Internet connectivity
* Traffic troubleshooting

Firewall configurations must be documented.

---

# 10. Routing

The environment must support routing between authorized networks.

Routing requirements may include:

* Local subnet routing
* VLAN routing
* Default routes
* Static routes
* VPN routes
* Azure-connected routes

Routing changes should follow change-management procedures.

---

# 11. Windows 11 Endpoints

Stoneleaf Systems requires Windows 11 client systems to simulate employee workstations.

Endpoints should support:

* Domain membership
* User authentication
* Group Policy
* Department-based access
* Software installation
* File share access
* Printer access
* Remote support
* Patch management
* Security controls

Workstations should follow standardized naming and configuration conventions.

---

# 12. Linux Systems

The environment requires Linux systems for administration and enterprise-service experience.

Ubuntu Linux will initially be used.

Linux systems may support:

* Administrative tools
* Networking
* Scripting
* Monitoring
* Logging
* Web services
* Security tools
* Automation

Linux configuration and troubleshooting should be documented.

---

# 13. Microsoft Azure

Stoneleaf Systems will use Microsoft Azure as its primary cloud platform.

Azure should eventually support:

* Virtual networks
* Subnets
* Virtual machines
* Network security groups
* Storage
* Identity integration
* Monitoring
* Security controls
* Hybrid connectivity
* Backup or recovery services

Azure resources should follow documented naming and tagging standards.

---

# 14. Microsoft Entra ID

The environment requires cloud identity administration using Microsoft Entra ID.

The environment should support:

* Cloud identities
* Group management
* Role assignments
* Authentication
* Multi-factor authentication
* Hybrid identity concepts
* Conditional access concepts where available
* Administrative role separation

Cloud roles should follow least-privilege principles.

---

# 15. Hybrid Identity

Stoneleaf Systems should eventually demonstrate integration between local identity and cloud identity.

Hybrid identity concepts may include:

* Active Directory
* Microsoft Entra ID
* Identity synchronization
* Common user identities
* Group synchronization
* Authentication integration

The final implementation will depend on available licensing and lab resources.

---

# 16. VPN

Stoneleaf Systems requires secure remote connectivity.

VPN capabilities may be used for:

* Remote-user access
* Administrative access
* Site-to-site connectivity
* Azure connectivity

VPN access should require authentication and be restricted to authorized users.

---

# 17. File Services

The environment requires centralized file storage.

File services should support:

* Department shares
* Security groups
* NTFS permissions
* Share permissions
* Read-only access
* Read/write access
* Restricted confidential folders
* Backup
* Recovery

Permissions should be assigned to groups rather than directly to individual users whenever practical.

---

# 18. Group Policy

Stoneleaf Systems requires centralized Windows configuration management through Group Policy.

Planned policy areas include:

* Password-related settings
* Account lockout
* Desktop configuration
* Security settings
* Windows Firewall
* Drive mappings
* Administrative restrictions
* Update configuration
* Audit settings

Group Policy changes must be documented and tested.

---

# 19. Security Groups

Active Directory security groups must support role-based resource access.

Planned global groups include:

```text
GG-Executive-Users
GG-IT-Users
GG-Operations-Users
GG-Sales-Users
GG-CustomerService-Users
GG-Finance-Users
GG-HR-Users
```

Resource-specific groups may include:

```text
DL-Finance-RW
DL-Finance-RO
DL-HR-RW
DL-HR-RO
DL-Sales-RW
DL-Sales-RO
```

The environment should practice group-based permission assignment.

---

# 20. Administrative Accounts

Privileged IT users must use separate administrative accounts.

Example:

```text
sdempsey
sdempsey-admin
```

Administrative accounts should:

* Be used only when elevated permissions are required.
* Have stronger security controls.
* Not be used for normal browsing or email.
* Receive only necessary privileges.
* Be monitored and documented.

---

# 21. Least Privilege

Access to systems and resources must follow the principle of least privilege.

Users should only receive:

* Required applications
* Required file access
* Required administrative permissions
* Required cloud roles
* Required network access

Permissions should be reviewed and removed when no longer necessary.

---

# 22. Multi-Factor Authentication

Cloud and remote-access services should support MFA where licensing and lab capabilities permit.

MFA should be prioritized for:

* Administrative users
* Cloud administrators
* Remote users
* Sensitive applications

---

# 23. Endpoint Security

Windows endpoints should support baseline security controls.

Controls may include:

* Microsoft Defender
* Windows Firewall
* Automatic updates
* Secure configuration
* Local administrator restrictions
* Screen-lock policies
* Audit policies
* Application controls where practical

---

# 24. Server Hardening

Servers should be configured using secure administrative practices.

Hardening should include:

* Removal of unnecessary services
* Least privilege
* Strong administrative credentials
* Firewall rules
* Patch management
* Logging
* Secure remote administration
* Limited interactive access

---

# 25. Patch Management

Stoneleaf Systems requires a process for keeping systems current.

Patch management must cover:

* Windows Server
* Windows 11
* Linux
* Applications
* Network appliances
* Cloud systems where applicable

Update status should be monitored and documented.

---

# 26. Monitoring

Stoneleaf Systems requires centralized infrastructure monitoring.

Monitoring should eventually provide visibility into:

* Server availability
* CPU utilization
* Memory utilization
* Disk utilization
* Network connectivity
* Service status
* System health
* Backup status

Alerts should be generated for significant failures where practical.

---

# 27. Centralized Logging

Important systems must generate logs that can be reviewed centrally.

Potential log sources include:

* Windows Server
* Active Directory
* Windows endpoints
* Linux
* pfSense
* Azure
* Authentication systems
* Security tools

Logging should support both troubleshooting and security analysis.

---

# 28. Time Synchronization

Systems must maintain accurate time.

Time synchronization is required for:

* Authentication
* Logging
* Event correlation
* Troubleshooting
* Certificates
* Security investigations

Domain-joined systems should follow the Active Directory time hierarchy.

---

# 29. Backup

The environment requires backup capabilities for important systems and data.

Backup targets may include:

* File shares
* Server configurations
* Virtual machines
* Important scripts
* Documentation
* Critical application data

Backup jobs should be documented and verified.

---

# 30. Recovery Testing

Stoneleaf Systems must periodically validate that backups can actually be restored.

Recovery testing should include:

* File restoration
* Configuration restoration
* Virtual machine recovery where practical
* Documentation of results

Backup success alone should not be treated as proof of recoverability.

---

# 31. Disaster Recovery

The technical environment should support recovery from significant failures.

Recovery planning should address:

* Domain controller failure
* File server failure
* Network failure
* Firewall failure
* Cloud-service outage
* Data loss
* Virtual machine corruption
* Configuration mistakes

Recovery procedures must be documented.

---

# 32. PowerShell

PowerShell will serve as the primary Windows administration and automation language.

PowerShell tasks may include:

* User creation
* Group management
* Computer inventory
* Service management
* Event-log analysis
* Account reporting
* File permissions
* Active Directory administration
* System health checks
* Automation

Scripts should be stored in the appropriate repository section.

---

# 33. Bash

Bash will be used for Linux administration and automation.

Tasks may include:

* System updates
* User management
* File administration
* Networking
* Service management
* Log review
* Automation

---

# 34. Ticketing Simulation

Stoneleaf Systems requires a simulated IT ticketing workflow.

Tickets should support:

* Incident tickets
* Service requests
* Access requests
* Onboarding
* Offboarding
* Troubleshooting
* Change-related work

Tickets should reference real fictional employees defined in `Departments-and-Users.md`.

---

# 35. Asset Tracking

The environment should maintain records for important IT assets.

Assets may include:

* Servers
* Workstations
* Network devices
* Virtual machines
* Cloud resources
* Software
* Assigned equipment

Asset records should include identifying information and ownership where appropriate.

---

# 36. Documentation

All significant systems must be documented.

Documentation should include where appropriate:

* Purpose
* Hostname
* IP address
* System role
* Configuration
* Dependencies
* Commands
* Procedures
* Screenshots
* Validation results
* Troubleshooting notes

---

# 37. Naming Standards

The environment requires consistent naming conventions.

Naming standards must cover:

* Servers
* Workstations
* Users
* Administrative accounts
* Security groups
* Service accounts
* Network devices
* Cloud resources
* Tickets
* Scripts
* Documentation files

Naming conventions will be formally defined in:

`Naming-Standards.md`

---

# 38. Change Management

Major technical changes must be documented before implementation.

Changes should include:

* Purpose
* Systems affected
* Risk
* Implementation steps
* Testing
* Rollback
* Validation
* Results

---

# 39. Troubleshooting Documentation

Technical problems should be documented using a repeatable process.

Troubleshooting records should identify:

1. Reported symptoms
2. Systems affected
3. Initial observations
4. Tests performed
5. Evidence collected
6. Root cause
7. Corrective action
8. Validation
9. Final resolution

---

# 40. Scalability

The technical architecture must support expansion beyond the initial 40-user environment.

The design should allow for:

* More users
* More workstations
* More servers
* More VLANs
* Additional locations
* Additional cloud resources
* Increased monitoring
* Additional automation
* Additional security controls

---

# 41. Resource Efficiency

Because Stoneleaf Systems is implemented as a homelab, infrastructure must be designed efficiently.

Virtual systems should use only the CPU, memory, storage, and cloud resources necessary to support their roles.

Unused virtual machines and cloud resources should be powered off or removed when practical.

---

# 42. Security of Credentials

Credentials must not be stored in the public GitHub repository.

The repository must never contain:

* Passwords
* Private keys
* API tokens
* Cloud secrets
* Recovery codes
* Authentication cookies
* Sensitive connection strings

Example credentials used in documentation should be clearly fictional.

---

# 43. GitHub Documentation Repository

GitHub will serve as the primary portfolio and documentation repository.

The repository should contain:

* Markdown documentation
* Scripts
* Sanitized configuration examples
* Diagrams
* Screenshots
* Project evidence
* Troubleshooting documentation
* Ticket examples
* Change records

Sensitive production-style credentials must never be uploaded.

---

# Technical Requirement Summary

| ID    | Technical Requirement             |
| ----- | --------------------------------- |
| TR-01 | VMware-based local virtualization |
| TR-02 | Windows Server infrastructure     |
| TR-03 | Active Directory Domain Services  |
| TR-04 | Structured OU design              |
| TR-05 | Internal DNS                      |
| TR-06 | Centralized DHCP                  |
| TR-07 | Documented IPv4 addressing        |
| TR-08 | Network segmentation              |
| TR-09 | pfSense firewall                  |
| TR-10 | Routing between approved networks |
| TR-11 | Windows 11 endpoints              |
| TR-12 | Ubuntu Linux systems              |
| TR-13 | Microsoft Azure                   |
| TR-14 | Microsoft Entra ID                |
| TR-15 | Hybrid identity                   |
| TR-16 | Secure VPN access                 |
| TR-17 | Centralized file services         |
| TR-18 | Group Policy                      |
| TR-19 | Group-based permissions           |
| TR-20 | Separate administrative accounts  |
| TR-21 | Least privilege                   |
| TR-22 | Multi-factor authentication       |
| TR-23 | Endpoint security controls        |
| TR-24 | Server hardening                  |
| TR-25 | Patch management                  |
| TR-26 | Infrastructure monitoring         |
| TR-27 | Centralized logging               |
| TR-28 | Time synchronization              |
| TR-29 | Backup capabilities               |
| TR-30 | Recovery testing                  |
| TR-31 | Disaster recovery                 |
| TR-32 | PowerShell automation             |
| TR-33 | Bash administration               |
| TR-34 | IT ticketing simulation           |
| TR-35 | Asset tracking                    |
| TR-36 | Technical documentation           |
| TR-37 | Standard naming conventions       |
| TR-38 | Change management                 |
| TR-39 | Structured troubleshooting        |
| TR-40 | Scalable architecture             |
| TR-41 | Efficient resource utilization    |
| TR-42 | Credential protection             |
| TR-43 | GitHub portfolio documentation    |

---

## Document Status

**Organization:** Stoneleaf Systems

**Environment Size:** 40 users

**Infrastructure Model:** Hybrid local/cloud

**Current Phase:** `00-Foundation`

**Current Document:** `Technical-Requirements.md`

**Next Document:** `Logical-Architecture.md`

