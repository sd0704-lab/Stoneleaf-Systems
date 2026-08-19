# 00 - Foundation

## Overview

The **Foundation** phase establishes the business, technical, operational, and documentation standards that guide the rest of the Stoneleaf Systems environment.

Before servers, workstations, network services, cloud resources, or security controls are deployed, the organization needs a defined structure. This section documents the assumptions, requirements, standards, naming conventions, addressing plans, and operational processes that will be used throughout the lab.

The goal is to treat Stoneleaf Systems like a real organization rather than a collection of unrelated technical exercises.

---

## Objectives

This phase will define:

* What Stoneleaf Systems is and what the organization does.
* Which departments and users exist within the environment.
* Business requirements that drive technical decisions.
* Technical requirements for the lab infrastructure.
* The high-level logical architecture.
* The IPv4 addressing strategy.
* Device, server, workstation, user, and resource naming standards.
* Documentation standards used throughout the repository.
* Change-management procedures.
* Help desk and ticket documentation standards.
* Network+ concepts demonstrated throughout the environment.

---

## Foundation Documents

### `Organization-Overview.md`

Defines the fictional company, its purpose, operating model, size, locations, and general business environment.

### `Departments-and-Users.md`

Defines the departments, job roles, user accounts, administrative roles, and basic access requirements used throughout the lab.

### `Business-Requirements.md`

Documents the business needs that the IT environment must support, including availability, communication, security, remote access, file storage, administration, and growth.

### `Technical-Requirements.md`

Translates business requirements into technical requirements for networking, servers, endpoints, identity, cloud services, virtualization, security, monitoring, backup, and administration.

### `Logical-Architecture.md`

Describes the high-level relationship between the local virtual environment, network infrastructure, Windows domain, Linux systems, endpoints, security services, and Microsoft Azure resources.

### `IP-Addressing-Plan.md`

Defines the IPv4 networks, subnets, gateways, DHCP scopes, static address ranges, reserved addresses, and future segmentation strategy.

### `Naming-Standards.md`

Defines consistent naming conventions for servers, workstations, network devices, virtual machines, users, groups, cloud resources, files, tickets, and other infrastructure components.

### `Documentation-Standards.md`

Defines how technical procedures, screenshots, configurations, diagrams, troubleshooting notes, change records, and project documentation will be created and maintained.

### `Change-Management.md`

Defines the process for planning, approving, implementing, validating, documenting, and rolling back significant changes within the lab.

### `Ticket-Standards.md`

Defines standards for simulated help desk tickets, incidents, service requests, access requests, troubleshooting records, escalation, resolution notes, and closure documentation.

### `NetworkPlus-Skills-Matrix.md`

Maps networking concepts and practical tasks in the Stoneleaf Systems lab to Network+ skill areas so the environment can also reinforce certification knowledge through hands-on implementation.

---

## Design Principles

Stoneleaf Systems will follow several core design principles.

### Business Requirements Drive Technology

Technical components will be implemented because they support a defined organizational or operational requirement rather than simply because a technology is available.

### Documentation Is Part of the Work

A configuration is not considered complete until its purpose, implementation, validation, and important troubleshooting information are documented.

### Security by Design

Identity, least privilege, segmentation, patching, logging, hardening, and recovery considerations will be incorporated throughout the environment instead of being added only at the end.

### Standardization

Consistent naming, addressing, documentation, configuration, and operational processes will make the environment easier to administer and troubleshoot.

### Change Control

Major infrastructure changes will be planned and documented. Where appropriate, changes will include testing, validation, rollback procedures, and post-change notes.

### Troubleshooting Matters

The lab will include both successful deployments and intentionally introduced failures. Troubleshooting steps and root causes will be documented as portfolio evidence.

### Scalability

The environment will begin small enough to run efficiently in a homelab but will be designed so additional users, systems, networks, services, and cloud resources can be added later.

---

## Expected Outcome

When the Foundation phase is complete, Stoneleaf Systems will have a documented blueprint for the remainder of the lab.

The organization will have defined:

* Business context
* Departments and users
* Infrastructure requirements
* Network design assumptions
* IP addressing
* Naming conventions
* Documentation practices
* Ticket procedures
* Change-management procedures
* Technical standards

These documents will serve as the reference point for every later phase of the project.

---

## Phase Status

**Status:** In Progress

**Current Section:** `00-Foundation`

**Next Document:** `Organization-Overview.md`

