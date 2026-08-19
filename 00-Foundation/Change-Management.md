# Stoneleaf Systems — Change Management

## Purpose

This document defines the change-management process used throughout the Stoneleaf Systems enterprise IT environment.

Change management ensures that significant modifications to infrastructure are:

* Planned
* Documented
* Reviewed
* Tested
* Implemented carefully
* Validated
* Reversible when practical

The goal is to reduce unnecessary outages, configuration errors, security problems, and undocumented changes.

---

# 1. Change Management Principles

Stoneleaf Systems will follow these principles:

* Significant changes must be documented.
* Business requirements should justify technical changes.
* Risks should be identified before implementation.
* Changes should be tested where practical.
* Rollback procedures should be defined before implementation.
* Changes should occur during appropriate maintenance windows when possible.
* Results must be validated after implementation.
* Failed changes must be documented.
* Documentation must be updated after successful changes.
* Security impact must be considered before approval.

---

# 2. Change Request Identifier

Each change request will receive a unique identifier.

Format:

```text
CHG-####
```

Examples:

```text
CHG-0001
CHG-0002
CHG-0003
```

Change numbers will increase sequentially.

---

# 3. Change Request Title

Change titles should identify the action being performed.

Examples:

```text
CHG-0001 — Deploy Primary Domain Controller

CHG-0002 — Configure Server VLAN

CHG-0003 — Create Finance File Share

CHG-0004 — Deploy Workstation Security Baseline

CHG-0005 — Configure Azure Site-to-Site VPN
```

Avoid vague titles such as:

```text
Server Change

Network Update

Fix Stuff

New Configuration
```

---

# 4. Change Categories

Changes will be classified into three primary categories.

## Standard Change

A standard change is:

* Low risk
* Well understood
* Repeatable
* Previously tested
* Performed using an established procedure

Examples:

* Creating a standard user account
* Adding an approved workstation
* Deploying an established software package
* Adding a user to an approved security group

Standard changes may use simplified approval procedures.

---

## Normal Change

A normal change requires planning and review before implementation.

Examples:

* Deploying a new server
* Creating a VLAN
* Changing firewall rules
* Modifying Group Policy
* Changing DHCP configuration
* Adding a new Azure network
* Deploying a new monitoring system
* Changing file-share permissions

Most infrastructure projects in Stoneleaf Systems will be treated as normal changes.

---

## Emergency Change

An emergency change is required to restore service, mitigate a serious security risk, or prevent significant impact.

Examples:

* Blocking malicious traffic
* Recovering a failed critical server
* Disabling a compromised account
* Reverting a configuration causing an outage
* Applying an urgent security mitigation

Emergency changes may be implemented before normal review is complete, but must still be documented afterward.

---

# 5. Change Priority

Changes may be assigned the following priorities:

| Priority | Meaning                                                  |
| -------- | -------------------------------------------------------- |
| Low      | Minimal operational impact                               |
| Medium   | Moderate impact or limited infrastructure change         |
| High     | Significant infrastructure or security impact            |
| Critical | Emergency change required to restore or protect services |

Priority is separate from risk.

A change may be important without being technically risky.

---

# 6. Risk Levels

Each normal change should receive a risk rating.

## Low Risk

Examples:

* Adding a noncritical monitoring check
* Creating a new test VM
* Updating documentation

## Medium Risk

Examples:

* Creating a new DHCP scope
* Deploying a new file share
* Changing workstation policies

## High Risk

Examples:

* Modifying firewall routing
* Changing domain-wide Group Policy
* Changing DNS infrastructure
* Modifying authentication systems
* Changing domain controller configuration

## Critical Risk

Examples:

* Changes that could disable authentication
* Changes affecting the entire network
* Major security incidents
* Disaster-recovery actions affecting core systems

---

# 7. Change Request Required Information

Each normal change request should include:

* Change ID
* Title
* Requester
* Technician
* Date requested
* Planned implementation date
* Change category
* Priority
* Risk level
* Systems affected
* Business reason
* Technical description
* Dependencies
* Security considerations
* Implementation steps
* Testing procedure
* Rollback procedure
* Expected downtime
* Approval status
* Implementation results
* Validation results
* Final status

---

# 8. Business Justification

Each significant change must explain why the organization needs it.

Example:

```text
Business Justification:

Stoneleaf Systems requires centralized authentication for users and workstations. Deploying SL-DC01 will provide Active Directory Domain Services and internal DNS for the organization.
```

Technical changes should not exist only because a technology is available.

---

# 9. Technical Description

The technical description should summarize what will change.

Example:

```text
Technical Description:

Deploy Windows Server as SL-DC01 with static IP address 10.20.20.10. Install Active Directory Domain Services and DNS, then create the corp.stoneleaf.test forest.
```

The description should be detailed enough to understand the scope without duplicating the entire implementation procedure.

---

# 10. Systems Affected

The change request must identify affected systems.

Example:

```text
Systems Affected:

- SL-DC01
- VLAN 20 — Servers
- Internal DNS
- Future domain-joined systems
```

For later changes, affected systems may include:

* Servers
* Workstations
* User groups
* VLANs
* Azure resources
* File shares
* Firewall rules
* Applications

---

# 11. Dependencies

Dependencies must be identified before implementation.

Examples:

* DNS availability
* Network connectivity
* Required VM resources
* Existing security groups
* Azure subscription
* Administrator access
* Backup availability
* Previous changes

Example:

```text
Dependencies:

- SL-FW01 operational
- VLAN 20 available
- 10.20.20.10 unused
- Windows Server installed
```

---

# 12. Security Impact

Each significant change should consider security.

Questions include:

* Does this create new access?
* Does this open a firewall port?
* Does this modify authentication?
* Does this affect privileged accounts?
* Does this expose data?
* Does this create a new service?
* Does this reduce segmentation?
* Does this require credentials?
* Does this change logging?

Example:

```text
Security Impact:

The domain controller becomes a critical authentication system and must be restricted to authorized administrators.
```

---

# 13. Implementation Plan

The implementation plan must describe the actual change.

Example:

```text
Implementation Plan:

1. Create the SL-DC01 virtual machine.
2. Install Windows Server.
3. Configure hostname.
4. Assign 10.20.20.10/24.
5. Configure gateway 10.20.20.1.
6. Install Active Directory Domain Services.
7. Install DNS.
8. Create corp.stoneleaf.test.
9. Restart the server.
10. Validate AD DS and DNS.
```

Implementation steps should be repeatable whenever practical.

---

# 14. Pre-Change Validation

Before implementing a significant change, verify that required conditions are met.

Examples:

* Confirm backups exist.
* Confirm the target IP is unused.
* Verify available system resources.
* Verify administrator access.
* Verify the network is functioning.
* Confirm required dependencies.
* Take a VMware snapshot where appropriate.

Example:

```text
Pre-Change Validation:

- Confirm SL-DC01 VM is operational.
- Confirm 10.20.20.10 is available.
- Confirm SL-FW01 provides connectivity.
- Create pre-change VM snapshot.
```

---

# 15. Maintenance Windows

Changes that could disrupt users should be performed during a planned maintenance window where practical.

Examples include:

* Domain controller maintenance
* Firewall changes
* Routing changes
* DHCP changes
* Major Group Policy deployment
* Server reboots

Because Stoneleaf Systems is a lab, simulated maintenance windows may be used.

Example:

```text
Maintenance Window:

Saturday
20:00–22:00
```

---

# 16. Expected Downtime

Changes should identify whether downtime is expected.

Example:

```text
Expected Downtime:

None
```

or:

```text
Expected Downtime:

Approximately 10 minutes of file-service interruption while SL-FS01 restarts.
```

If downtime cannot be estimated precisely, the affected service should still be documented.

---

# 17. Testing Plan

Every major change should have a defined testing procedure.

Testing answers:

**How will we know the change worked?**

Example:

```text
Testing Plan:

1. Verify SL-DC01 responds to ping.
2. Confirm Active Directory services are running.
3. Run Get-ADDomain.
4. Verify DNS resolves SL-DC01.corp.stoneleaf.test.
5. Join a test workstation to the domain.
6. Confirm a domain user can authenticate.
```

---

# 18. Rollback Plan

A rollback plan explains how to return to the previous working state if the change fails.

Possible rollback methods include:

* Restore previous configuration
* Remove new firewall rule
* Revert Group Policy
* Restore VM snapshot
* Restore backup
* Disable new service
* Remove new route
* Revert Azure configuration

Example:

```text
Rollback Plan:

If the domain-controller deployment fails before production use, restore the pre-change VMware snapshot or remove the VM and rebuild using the documented procedure.
```

---

# 19. Rollback Trigger

The change request should identify when rollback becomes necessary.

Examples:

```text
Rollback Trigger:

- DNS fails after implementation.
- Authentication fails.
- Network connectivity is lost.
- Critical validation tests fail.
```

This prevents repeatedly troubleshooting a failed deployment during a limited maintenance window.

---

# 20. VMware Snapshots

VMware snapshots may be used before significant lab changes.

Examples:

```text
2026-08-19_Pre-ADDS-Install

2026-08-20_Pre-GPO-Deployment

2026-08-21_Pre-Network-Change
```

Snapshots should be used as temporary recovery tools.

They should not replace proper backups.

---

# 21. Approval

Normal changes should receive simulated approval before implementation.

Because Stoneleaf Systems is a homelab, approval may be recorded as:

```text
Approval Status: Approved
Approved By: Kevin Wallace — IT Manager
```

The purpose is to simulate enterprise change-control workflow.

---

# 22. Change Roles

The following roles may participate in a change.

## Requester

The person requesting the change.

## Implementer

The IT employee performing the work.

## Reviewer

The person reviewing technical risk and implementation steps.

## Approver

The person authorizing the change.

## Validator

The person confirming the change works correctly.

In the lab, one person may simulate several of these roles.

---

# 23. Example Change Roles

Example:

```text
Requester:
Scott Dempsey — Systems Administrator

Implementer:
Scott Dempsey — Systems Administrator

Reviewer:
Olivia Chen — Network Administrator

Approver:
Kevin Wallace — IT Manager
```

These names should come from `Departments-and-Users.md`.

---

# 24. Emergency Change Process

Emergency changes may bypass normal pre-approval when immediate action is necessary.

The emergency process is:

1. Identify the critical issue.
2. Determine the minimum change required.
3. Document the reason for emergency action.
4. Implement the change.
5. Validate service or security.
6. Notify the appropriate simulated stakeholders.
7. Complete the change record afterward.
8. Review whether additional corrective work is required.

---

# 25. Emergency Change Example

```text
CHG-0027 — Block Malicious External IP

Category: Emergency

Reason:

Repeated malicious authentication attempts are originating from a known external address.

Action:

Add a firewall rule on SL-FW01 blocking traffic from the source address.

Validation:

Confirm the traffic no longer reaches the targeted service.
```

---

# 26. Failed Changes

Failed changes must still be documented.

A failed change should include:

* What happened
* At what step it failed
* Symptoms
* Troubleshooting performed
* Whether rollback occurred
* Root cause if known
* Required follow-up

Failed changes are useful portfolio evidence because they demonstrate troubleshooting and recovery.

---

# 27. Post-Implementation Validation

After implementation, confirm:

* The intended change is active.
* Required services function.
* No unexpected impact exists.
* Security controls still function.
* Monitoring reports correctly.
* Users can access intended resources.
* Logs show expected behavior.

---

# 28. Post-Change Monitoring

Higher-risk changes should be monitored after completion.

Examples:

* Review event logs.
* Review firewall logs.
* Monitor server availability.
* Check service status.
* Test user authentication.
* Verify network connectivity.
* Review system performance.

---

# 29. Documentation Updates

A change is not fully complete until related documentation is updated.

Potential documents include:

```text
IP-Addressing-Plan.md
Naming-Standards.md
Logical-Architecture.md
Active-Directory-Design.md
Network-Topology.md
Firewall-Rules.md
```

Configuration and documentation must remain synchronized.

---

# 30. Change Statuses

Changes may use the following statuses:

| Status         | Meaning                                |
| -------------- | -------------------------------------- |
| Draft          | Change is being prepared               |
| Pending Review | Awaiting technical review              |
| Approved       | Authorized for implementation          |
| Scheduled      | Planned for a maintenance window       |
| In Progress    | Currently being implemented            |
| Completed      | Successfully implemented and validated |
| Failed         | Implementation unsuccessful            |
| Rolled Back    | Previous state restored                |
| Cancelled      | Change will not be implemented         |

---

# 31. Change Record Storage

Change records will eventually be stored in the appropriate IT Operations area.

Example:

```text
05-IT-Operations/
└── Change-Management/
    ├── README.md
    ├── CHG-0001-Deploy-Primary-Domain-Controller.md
    ├── CHG-0002-Create-Server-VLAN.md
    └── CHG-0003-Deploy-File-Server.md
```

This Foundation document defines the standard.

The later IT Operations section will contain the actual change records.

---

# 32. Change Request Template

A standard Stoneleaf Systems change record may use the following structure:

```text
# CHG-#### — Change Title

## Change Information

Change ID:
Requester:
Implementer:
Reviewer:
Approver:
Date Requested:
Planned Date:
Category:
Priority:
Risk:
Status:

## Business Justification

## Technical Description

## Systems Affected

## Dependencies

## Security Impact

## Pre-Change Validation

## Implementation Plan

## Testing Plan

## Rollback Plan

## Rollback Trigger

## Expected Downtime

## Implementation Results

## Validation Results

## Problems Encountered

## Documentation Updated

## Final Status

## Lessons Learned
```

---

# 33. Example Change Request

```text
# CHG-0001 — Deploy Primary Domain Controller

## Change Information

Change ID: CHG-0001

Requester: Scott Dempsey

Implementer: Scott Dempsey

Reviewer: Olivia Chen

Approver: Kevin Wallace

Category: Normal

Priority: High

Risk: Medium

Status: Approved

## Business Justification

Stoneleaf Systems requires centralized user authentication and identity management.

## Technical Description

Deploy SL-DC01 using Windows Server and configure Active Directory Domain Services and DNS.

## Systems Affected

- SL-DC01
- VLAN 20
- Internal DNS
- Future domain clients

## Implementation Plan

1. Deploy VM.
2. Install Windows Server.
3. Configure hostname.
4. Assign 10.20.20.10.
5. Install AD DS.
6. Install DNS.
7. Create corp.stoneleaf.test.
8. Restart.
9. Validate.

## Rollback Plan

Restore the pre-change VM snapshot or rebuild the server if deployment fails before production use.

## Validation

- AD DS operational
- DNS operational
- Domain resolves correctly
- Test workstation joins domain
- Test user authentication succeeds
```

---

# 34. Changes That Require Change Records

Examples of work requiring formal change documentation include:

* Domain controller deployment
* DNS changes
* DHCP changes
* Firewall changes
* VLAN deployment
* Routing changes
* New production-style servers
* Major file permissions
* Group Policy changes
* VPN configuration
* Azure network changes
* Hybrid connectivity
* Monitoring deployment
* Backup infrastructure
* Major security controls

---

# 35. Changes That May Not Require Formal Change Records

Routine low-risk activities may be documented through tickets instead.

Examples:

* Password reset
* Standard user creation
* Approved software installation
* Adding a user to an existing approved group
* Basic workstation troubleshooting

These actions should still be documented where appropriate.

---

# 36. Unauthorized Changes

Infrastructure should not be changed without documentation when the change could materially affect:

* Availability
* Security
* Connectivity
* Authentication
* Data access
* Configuration
* Other users

If an undocumented change is made during troubleshooting, it should be recorded afterward.

---

# 37. Change Freeze

Stoneleaf Systems may simulate a change freeze during periods when infrastructure stability is especially important.

During a change freeze:

* Routine changes are postponed.
* Only emergency or approved critical changes proceed.
* Risk is minimized.

This can be used later as part of operational scenarios.

---

# 38. Configuration Baselines

Where possible, systems should have known baseline configurations.

Examples:

* Firewall baseline
* Domain-controller baseline
* Workstation security baseline
* Group Policy baseline
* Server baseline

Changes can then be compared against known-good configurations.

---

# 39. Change Metrics

As the simulated IT operation grows, Stoneleaf Systems may track:

* Total changes
* Successful changes
* Failed changes
* Rolled-back changes
* Emergency changes
* Change-related incidents

Example:

```text
Total Changes: 25
Successful: 22
Failed: 2
Rolled Back: 1
Emergency: 3
```

These metrics can later become part of the professional portfolio.

---

# 40. Change Management Workflow

```text
Business Need
     │
     ▼
Change Request
     │
     ▼
Risk Review
     │
     ▼
Technical Review
     │
     ▼
Approval
     │
     ▼
Schedule
     │
     ▼
Pre-Change Validation
     │
     ▼
Implementation
     │
     ▼
Testing
     │
     ├── Failure ──► Rollback
     │
     ▼
Validation
     │
     ▼
Documentation Update
     │
     ▼
Change Closed
```

---

# 41. Change Management Goals

Stoneleaf Systems change management is intended to demonstrate:

* Planning
* Risk awareness
* Technical documentation
* Business justification
* Testing
* Troubleshooting
* Recovery
* Security awareness
* Operational discipline

The process should support the technical work rather than create unnecessary paperwork.

---

# Change Management Summary

| Area              | Standard                                      |
| ----------------- | --------------------------------------------- |
| Change identifier | `CHG-####`                                    |
| Categories        | Standard, Normal, Emergency                   |
| Risk levels       | Low, Medium, High, Critical                   |
| Normal changes    | Reviewed and approved before implementation   |
| Emergency changes | Documented immediately afterward if necessary |
| Testing           | Required for significant changes              |
| Rollback          | Required where practical                      |
| Validation        | Required before closure                       |
| Documentation     | Updated after implementation                  |
| Failed changes    | Documented, not hidden                        |
| Primary goal      | Controlled, repeatable infrastructure changes |

---

## Document Status

**Organization:** Stoneleaf Systems

**Change Identifier:** `CHG-####`

**Current Phase:** `00-Foundation`

**Current Document:** `Change-Management.md`

**Next Document:** `Ticket-Standards.md`

