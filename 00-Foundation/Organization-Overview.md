# Stoneleaf Systems — Organization Overview

## Purpose

This document defines the fictional organization used throughout the **Stoneleaf Systems Enterprise IT Homelab**.

Stoneleaf Systems provides the business context for the technical environment. Servers, networks, user accounts, security controls, cloud resources, help desk tickets, and infrastructure projects will be implemented in response to realistic organizational requirements rather than as isolated lab exercises.

---

## Organization Profile

**Company Name:** Stoneleaf Systems

**Company Type:** Privately owned technology and business services company

**Primary Location:** New Hampshire, United States

**Organization Size:** Approximately 40 employees

**Operating Model:** Hybrid on-site and remote workforce

**IT Model:** Centrally managed internal IT department

**Environment Type:** Hybrid on-premises and cloud infrastructure

Stoneleaf Systems is a growing small-to-medium-sized organization that relies heavily on technology for daily business operations.

Employees use company-managed computers, shared files, business applications, email, cloud services, and internal network resources to perform their jobs.

The organization maintains a small internal IT department responsible for supporting users and managing the company's technology infrastructure.

---

## Business Operations

Stoneleaf Systems provides technology-related services and business solutions to commercial customers.

Daily operations depend on reliable access to:

* Business applications
* Email and collaboration services
* Shared files
* Internet connectivity
* Internal network resources
* Remote-access services
* Customer information
* Financial records
* Employee information
* Cloud services

Because technology supports nearly every department, system availability and security are important to normal business operations.

---

## Workforce

Stoneleaf Systems employs approximately **40 users** across several business functions.

The workforce includes:

* Executive and management personnel
* Information technology personnel
* Operations employees
* Sales and customer-service employees
* Finance personnel
* Human resources personnel
* Administrative staff

Some employees work primarily from the company's main office, while others may work remotely or travel as part of their job responsibilities.

The exact departments, job roles, user accounts, security groups, and access requirements will be defined in:

`Departments-and-Users.md`

---

## Primary Office

Stoneleaf Systems operates from a primary office located in **New Hampshire**.

The main office contains the organization's core local infrastructure, including:

* Network equipment
* Firewall
* Virtualized servers
* Domain services
* DNS services
* DHCP services
* File services
* Administrative workstations
* Employee workstations
* Wireless networking
* Internet connectivity

The environment will initially simulate a single physical office while allowing the architecture to expand to additional locations in later phases.

---

## Remote Workforce

Stoneleaf Systems supports employees who occasionally or regularly work outside the primary office.

Remote users require secure access to approved company services.

Remote-work requirements may include:

* Cloud applications
* Microsoft 365 services
* Secure VPN connectivity
* Multi-factor authentication
* Company-managed endpoints
* Remote support
* Access to authorized internal resources

Remote access will follow the same identity, access-control, and security standards used for on-site users.

---

## Information Technology Department

The internal IT department is responsible for maintaining the Stoneleaf Systems technology environment.

Primary responsibilities include:

### User Support

* Help desk support
* Password resets
* Account troubleshooting
* Hardware troubleshooting
* Software troubleshooting
* Remote support
* Access requests

### Identity Administration

* User account creation
* User account removal
* Group membership
* Permissions
* Authentication
* Active Directory administration
* Microsoft Entra ID administration

### Systems Administration

* Windows Server administration
* Windows endpoint administration
* Linux administration
* File services
* Group Policy
* DNS
* DHCP
* Patch management

### Network Administration

* IP addressing
* Routing
* Firewall administration
* VLANs
* VPN services
* Wireless networking
* Network troubleshooting

### Cloud Administration

* Microsoft Azure
* Microsoft Entra ID
* Virtual networks
* Virtual machines
* Cloud security
* Identity integration
* Resource administration

### Security

* Identity security
* Least privilege
* Endpoint hardening
* Server hardening
* Security logging
* Patch management
* Vulnerability remediation
* Incident response

### IT Operations

* Ticket management
* Change management
* Asset management
* Documentation
* Monitoring
* Backup verification
* Disaster recovery
* Infrastructure maintenance

---

## Technology Strategy

Stoneleaf Systems follows a **hybrid infrastructure strategy**.

Some infrastructure will operate within the local virtualized environment while selected services and systems will be hosted in Microsoft Azure.

This model provides opportunities to demonstrate administration of both traditional enterprise infrastructure and modern cloud technologies.

The environment will eventually include:

* Windows Server
* Active Directory Domain Services
* Windows 11 endpoints
* Linux systems
* pfSense
* VMware Workstation
* DNS
* DHCP
* File services
* Microsoft Azure
* Microsoft Entra ID
* VPN connectivity
* Monitoring
* Centralized logging
* Backup and recovery
* PowerShell automation

---

## Security Requirements

Stoneleaf Systems considers security part of normal IT operations rather than a separate activity.

The organization will follow several basic security principles:

* Least-privilege access
* Role-based permissions
* Strong authentication
* Multi-factor authentication where appropriate
* Network segmentation
* Secure administrative accounts
* Regular patching
* Centralized logging
* Endpoint protection
* Backup and recovery
* Controlled remote access
* Documented security incidents
* Separation of standard and administrative accounts

Security controls will become more advanced as the environment develops.

---

## Availability Requirements

Stoneleaf Systems depends on IT systems for daily operations.

Critical services should therefore be designed to minimize unnecessary downtime.

Important services include:

* Authentication
* DNS
* DHCP
* File access
* Internet connectivity
* Cloud services
* Remote access

The lab will eventually include monitoring, backup, recovery, redundancy concepts, and disaster-recovery procedures for critical systems.

---

## Growth Assumptions

Stoneleaf Systems is expected to grow over time.

The initial environment will support approximately **40 employees**, but infrastructure will be designed with expansion in mind.

Future growth may include:

* Additional employees
* Additional departments
* Additional servers
* Additional network segments
* Additional cloud services
* Additional security controls
* Additional office locations
* Increased automation
* Increased remote access

This growth model will allow the homelab to evolve instead of remaining a fixed environment.

---

## IT Operational Philosophy

Stoneleaf Systems IT will operate according to four primary principles:

### Standardize

Systems, accounts, devices, documentation, and configurations should follow defined standards whenever possible.

### Secure

Security should be incorporated during system design and administration rather than added after deployment.

### Document

Infrastructure changes, configurations, troubleshooting, and administrative procedures should be documented.

### Automate

Repetitive administrative processes should be automated when doing so improves reliability, consistency, and efficiency.

---

## Lab Scope

The Stoneleaf Systems environment will simulate the IT infrastructure required to support this organization.

The project will include hands-on work involving:

* Networking
* Windows Server
* Active Directory
* Group Policy
* Windows endpoints
* Linux
* Virtualization
* Microsoft Azure
* Microsoft Entra ID
* PowerShell
* IT operations
* Help desk activities
* Security administration
* Monitoring
* Logging
* Backup
* Disaster recovery
* Troubleshooting
* Documentation

The environment will be expanded gradually as each project phase is completed.

---

## Organization Status

**Organization:** Stoneleaf Systems

**Employee Count:** Approximately 40

**Primary Location:** New Hampshire

**Workforce Model:** Hybrid

**Infrastructure Model:** Hybrid on-premises/cloud

**Primary Cloud Platform:** Microsoft Azure

**Current Lab Phase:** `00-Foundation`

**Next Document:** `Departments-and-Users.md`

