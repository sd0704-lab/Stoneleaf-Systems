# Stoneleaf Systems — Ticket Standards

## Purpose

This document defines the ticketing standards used by the Stoneleaf Systems IT department.

The goal is to simulate a realistic help desk and IT operations environment where user issues, service requests, access changes, onboarding, offboarding, incidents, and technical work are documented consistently.

Tickets should provide enough detail that another technician can understand:

* Who reported the issue
* What happened
* What systems were affected
* What troubleshooting was performed
* What action was taken
* Whether the issue was resolved
* How the final result was validated

---

# 1. Ticketing Principles

Stoneleaf Systems tickets will follow these principles:

* Every ticket must have a unique identifier.
* The requester must be identified.
* The affected department must be recorded.
* The issue or request must be clearly described.
* Priority must reflect business impact.
* Troubleshooting steps must be documented.
* Changes to access must be traceable.
* Resolution notes must explain what fixed the issue.
* Tickets should be closed only after validation.
* Ticket information must remain consistent with the rest of the lab documentation.

---

# 2. Ticket Types

Stoneleaf Systems will use four primary ticket categories.

| Prefix | Ticket Type     |
| ------ | --------------- |
| `INC`  | Incident        |
| `REQ`  | Service Request |
| `ACC`  | Access Request  |
| `CHG`  | Change Request  |

Examples:

```text
INC-0001
REQ-0001
ACC-0001
CHG-0001
```

Change requests are governed primarily by:

`Change-Management.md`

---

# 3. Incident Tickets

Incident tickets document an interruption or degradation of an existing IT service.

Examples include:

* User cannot sign in
* Workstation cannot access the network
* DNS resolution failure
* Printer unavailable
* File share unavailable
* VPN failure
* Server outage
* Application error
* DHCP failure
* Slow network performance

Incident identifier:

```text
INC-####
```

Example:

```text
INC-0007 — Megan Carter Cannot Access Sales Share
```

---

# 4. Service Requests

Service requests document standard IT services that do not represent a failure.

Examples include:

* Password reset
* Software installation
* New workstation request
* Printer installation
* Equipment request
* Standard user setup
* Approved configuration change
* Assistance with an existing service

Service request identifier:

```text
REQ-####
```

Example:

```text
REQ-0012 — Joshua Martin Password Reset
```

---

# 5. Access Requests

Access requests document requests for new or modified permissions.

Examples include:

* File-share access
* Security-group membership
* VPN access
* Azure role assignment
* Application access
* Department resource access
* Administrative permissions

Access request identifier:

```text
ACC-####
```

Example:

```text
ACC-0005 — Rebecca Adams Finance Reporting Access
```

Access requests should include approval when access involves restricted or sensitive resources.

---

# 6. Change Requests

Significant infrastructure changes will use:

```text
CHG-####
```

Examples:

```text
CHG-0001 — Deploy Primary Domain Controller
CHG-0002 — Configure Server VLAN
CHG-0003 — Create Finance File Share
```

Change requests should follow the detailed process defined in:

`Change-Management.md`

---

# 7. Ticket Numbering

Ticket numbers will increase sequentially within each ticket category.

Examples:

```text
INC-0001
INC-0002
INC-0003
```

and:

```text
REQ-0001
REQ-0002
```

The same numeric value may exist under different ticket types because the prefix distinguishes the record.

Example:

```text
INC-0004
REQ-0004
ACC-0004
CHG-0004
```

---

# 8. Ticket Titles

Ticket titles should identify the requester or affected service and briefly describe the problem.

Good examples:

```text
INC-0014 — Emily Parker Cannot Resolve Internal DNS

REQ-0008 — Hannah Scott Printer Installation

ACC-0006 — Daniel Foster VPN Access

INC-0021 — SL-FS01 Unavailable
```

Poor examples:

```text
Help

Computer problem

Broken network

Need access

Server issue
```

---

# 9. Required Ticket Fields

Every ticket should include, where applicable:

* Ticket ID
* Ticket type
* Title
* Requester
* Username
* Department
* Assigned technician
* Date opened
* Priority
* Status
* Affected system
* Description
* Business impact
* Troubleshooting
* Actions taken
* Resolution
* Validation
* Date closed

---

# 10. Requester Information

Tickets involving an employee should identify the fictional user defined in:

`Departments-and-Users.md`

Example:

```text
Requester: Megan Carter
Username: mcarter
Department: Sales
```

Do not create random users that are not part of the Stoneleaf Systems organization unless the scenario explicitly involves a new hire.

---

# 11. Assigned Technician

Each ticket should identify the IT staff member responsible for the work.

Examples:

```text
Assigned Technician: Ian Turner
```

or:

```text
Assigned Technician: Priya Shah
```

More advanced infrastructure issues may be assigned to:

* Scott Dempsey — Systems Administrator
* Olivia Chen — Network Administrator
* Marcus Reed — Cloud Administrator
* Kevin Wallace — IT Manager

---

# 12. Ticket Priority

Stoneleaf Systems will use four priority levels.

| Priority      | Description                                                      |
| ------------- | ---------------------------------------------------------------- |
| P1 — Critical | Major business outage or serious security issue                  |
| P2 — High     | Significant impact affecting multiple users or important service |
| P3 — Medium   | Normal user issue with limited business impact                   |
| P4 — Low      | Minor issue, question, or nonurgent request                      |

---

# 13. P1 — Critical

Use P1 when a major business service is unavailable or a serious security incident is occurring.

Examples:

* Domain authentication unavailable
* Entire network outage
* Critical server unavailable
* Major security compromise
* Company-wide internet outage

P1 tickets require immediate attention.

---

# 14. P2 — High

Use P2 for significant issues that affect an important user, department, or service.

Examples:

* Finance department cannot access required files
* VPN unavailable for multiple remote users
* File server degraded
* DHCP unavailable to an entire subnet
* Executive user blocked from critical business function

---

# 15. P3 — Medium

P3 is the normal default for most user support incidents.

Examples:

* One user cannot access a file share
* One workstation cannot connect to a printer
* Software malfunction
* Password issue
* One user's mapped drive is missing

---

# 16. P4 — Low

P4 is used for minor or nonurgent work.

Examples:

* Software request
* General question
* Cosmetic issue
* Nonurgent equipment request
* Documentation update

---

# 17. Ticket Statuses

Tickets may use the following statuses:

| Status           | Meaning                                  |
| ---------------- | ---------------------------------------- |
| New              | Ticket has been submitted                |
| Assigned         | Technician assigned                      |
| In Progress      | Technician is actively working the issue |
| Pending User     | Waiting for requester response           |
| Pending Approval | Waiting for authorization                |
| Pending Vendor   | Waiting for external support             |
| Resolved         | Technical solution implemented           |
| Closed           | Resolution validated and ticket complete |
| Cancelled        | Request is no longer required            |

---

# 18. Incident Description

The initial description should record what the user reports without assuming the cause.

Example:

```text
Megan Carter reports that she receives an Access Denied message when attempting to open the Sales shared folder. She states that access worked yesterday.
```

Avoid writing the assumed root cause before investigation.

---

# 19. Business Impact

Tickets should describe how the problem affects work.

Example:

```text
Business Impact:

Megan Carter cannot access active customer proposal documents stored on the Sales shared folder, preventing her from completing current sales work.
```

Business impact helps determine priority.

---

# 20. Affected Systems

Relevant systems should be documented.

Example:

```text
Affected Systems:

- User: mcarter
- Workstation: SL-WS-SALES01
- File Server: SL-FS01
- Resource: \\SL-FS01\Sales
```

---

# 21. Initial Troubleshooting

Technicians should record useful initial checks.

Examples:

* Verified user identity
* Confirmed network connectivity
* Confirmed IP configuration
* Tested DNS resolution
* Confirmed server availability
* Reviewed group membership
* Tested access from another workstation
* Checked event logs
* Reviewed firewall logs

---

# 22. Troubleshooting Notes

Troubleshooting notes should be written in chronological order.

Example:

```text
14:05 — Confirmed SL-WS-SALES01 has valid DHCP configuration.

14:08 — Successfully pinged SL-FS01.

14:10 — Verified DNS resolves SL-FS01.corp.stoneleaf.test.

14:14 — Reviewed mcarter group membership.

14:17 — Found user missing from GG-Sales-Users.
```

Exact timestamps are optional in simpler tickets but useful in larger incidents.

---

# 23. Hypothesis-Based Troubleshooting

For complex tickets, technicians may record suspected causes.

Example:

```text
Initial Hypothesis:

The problem may be related to either Active Directory group membership or file-share permissions because network connectivity and DNS are functioning normally.
```

Hypotheses should be updated as evidence is gathered.

---

# 24. Root Cause

When the cause is identified, document it clearly.

Example:

```text
Root Cause:

Megan Carter's account had been accidentally removed from GG-Sales-Users, which prevented membership in the resource access group used for the Sales share.
```

The root cause should explain why the issue occurred, not just what action fixed it.

---

# 25. Resolution

Resolution notes should describe what was changed.

Example:

```text
Resolution:

Restored mcarter to GG-Sales-Users and refreshed the user's authentication token by signing out and signing back in.
```

Avoid vague resolution notes such as:

```text
Fixed.
```

or:

```text
Working now.
```

---

# 26. Validation

A ticket should include proof that the solution worked.

Example:

```text
Validation:

Megan Carter signed back into SL-WS-SALES01 and successfully opened \\SL-FS01\Sales with read/write access.
```

A ticket should generally not be closed until validation is complete.

---

# 27. User Confirmation

When practical, user-facing tickets should record whether the requester confirmed resolution.

Example:

```text
User Confirmation:

Megan Carter confirmed that she can access and save files in the Sales share.
```

---

# 28. Escalation

Tickets should be escalated when the assigned technician does not have the required access, knowledge, or authority.

Example path:

```text
IT Support Technician
        │
        ▼
IT Support Specialist
        │
        ▼
Systems / Network / Cloud Administrator
        │
        ▼
IT Manager
```

---

# 29. Escalation Examples

Examples include:

* Active Directory failure → Systems Administrator
* Routing issue → Network Administrator
* Azure permission problem → Cloud Administrator
* Major outage → IT Manager

Escalation should be documented in the ticket.

Example:

```text
Escalated to Olivia Chen for network-layer troubleshooting after local workstation and DNS checks passed.
```

---

# 30. Access Approval

Sensitive access requests should identify the approver.

Example:

```text
Requester: Rebecca Adams

Requested Access:
Finance Reporting — Read/Write

Approval:
Thomas Keller — CFO

Assigned Technician:
Scott Dempsey
```

IT should not grant sensitive access solely because the user requests it.

---

# 31. Finance Access

Finance resources require approval from authorized Finance management or appropriate executive leadership.

Examples:

* Finance shared folders
* Accounting applications
* Financial reports
* Payroll-related data

---

# 32. HR Access

HR resources require approval from authorized Human Resources management.

Examples:

* Employee records
* Personnel files
* Hiring documentation
* Compensation data
* Benefits information

---

# 33. Administrative Access

Requests for privileged IT access require greater scrutiny.

The ticket should document:

* Why access is needed
* What systems require access
* What privileges are requested
* Who approved it
* Whether a dedicated admin account is required

Privileged access must follow least privilege.

---

# 34. Onboarding Tickets

New employee onboarding should use a service request.

Example:

```text
REQ-0025 — Onboard New Sales Employee
```

Onboarding tasks may include:

* Create user account
* Assign username
* Place user in correct OU
* Add department security groups
* Configure email
* Assign licenses
* Prepare workstation
* Configure shared drives
* Configure applications
* Provide remote access if approved
* Validate sign-in
* Record assigned assets

---

# 35. Onboarding Ticket Example

```text
Requester:
Melissa Green — Recruiting Coordinator

New Employee:
Jordan Miller

Department:
Sales

Role:
Sales Representative

Start Date:
2026-09-08

Required Access:

- Microsoft 365
- Sales shared folder
- CRM
- Corporate Wi-Fi
- Standard Windows workstation
```

A newly introduced fictional employee should be added to `Departments-and-Users.md` if they become a permanent part of the environment.

---

# 36. Offboarding Tickets

Employee termination or departure should use a service request or dedicated offboarding workflow.

Example:

```text
REQ-0031 — Offboard Tyler Murphy
```

Tasks may include:

* Disable user account
* Revoke active sessions
* Remove VPN access
* Remove cloud access
* Recover company equipment
* Transfer required business data
* Remove unnecessary group membership
* Preserve mailbox/data where required
* Document completion

---

# 37. Password Reset Tickets

Password reset requests should verify the identity of the requester before the password is changed.

Example:

```text
REQ-0012 — Joshua Martin Password Reset
```

Ticket notes should document identity verification without recording sensitive authentication answers or actual passwords.

Never place the user's new password in the ticket.

---

# 38. Repeated Incidents

If the same issue repeatedly occurs, technicians should determine whether a larger problem exists.

Example:

Three different users lose DNS access within one week.

Instead of treating each as unrelated, IT should investigate:

* DHCP configuration
* DNS service health
* Network stability
* Group Policy
* Firewall configuration

Recurring incidents may result in a problem investigation or change request.

---

# 39. Related Tickets

Tickets may reference other records.

Example:

```text
Related Incident:
INC-0023

Related Change:
CHG-0011
```

This helps connect user problems with infrastructure changes.

---

# 40. Change-Related Incidents

If a recent change causes an issue, the ticket should identify that relationship.

Example:

```text
Related Change:

CHG-0018 — Modify Workstation DNS Configuration
```

This allows change success and failure to be measured later.

---

# 41. Security Incidents

Security-related tickets should document only information appropriate for the public lab repository.

Possible scenarios include:

* Repeated failed logins
* Suspicious PowerShell activity
* Unauthorized group membership
* Malware detection
* Firewall alert
* Account compromise

Sensitive credentials or dangerous live data must not be published.

---

# 42. Ticket Evidence

Useful evidence may include:

* Sanitized screenshots
* Event-log excerpts
* `ipconfig /all`
* `ping`
* `nslookup`
* PowerShell output
* Firewall logs
* Group membership
* Service status

Evidence should support the troubleshooting narrative.

---

# 43. Ticket Storage

Actual ticket records will be stored in the IT Operations section.

Planned structure:

```text
05-IT-Operations/
│
├── README.md
│
├── Tickets/
│   ├── Incidents/
│   ├── Service-Requests/
│   └── Access-Requests/
│
└── Change-Management/
```

Example:

```text
05-IT-Operations/
└── Tickets/
    └── Incidents/
        └── INC-0001-Megan-Carter-Sales-Share-Access.md
```

---

# 44. Ticket Filename Standard

Ticket filenames should contain the identifier and short description.

Examples:

```text
INC-0001-Megan-Carter-Sales-Share-Access.md

REQ-0002-Joshua-Martin-Password-Reset.md

ACC-0003-Rebecca-Adams-Finance-Access.md
```

---

# 45. Incident Ticket Template

```text
# INC-#### — Ticket Title

## Ticket Information

Ticket ID:
Requester:
Username:
Department:
Assigned Technician:
Date Opened:
Priority:
Status:

## Problem Description

## Business Impact

## Affected Systems

## Initial Assessment

## Troubleshooting

## Root Cause

## Resolution

## Validation

## User Confirmation

## Related Records

## Date Closed
```

---

# 46. Service Request Template

```text
# REQ-#### — Request Title

## Ticket Information

Ticket ID:
Requester:
Username:
Department:
Assigned Technician:
Date Opened:
Priority:
Status:

## Request

## Business Reason

## Required Actions

## Actions Completed

## Validation

## User Confirmation

## Related Records

## Date Closed
```

---

# 47. Access Request Template

```text
# ACC-#### — Access Request Title

## Ticket Information

Ticket ID:
Requester:
Username:
Department:
Assigned Technician:
Date Opened:
Priority:
Status:

## Requested Access

## Business Justification

## Resource

## Permission Level

## Approver

## Existing Access Reviewed

## Actions Completed

## Validation

## User Confirmation

## Date Closed
```

---

# 48. Example Incident Ticket

```text
# INC-0001 — Megan Carter Cannot Access Sales Share

## Ticket Information

Ticket ID: INC-0001
Requester: Megan Carter
Username: mcarter
Department: Sales
Assigned Technician: Ian Turner
Priority: P3 — Medium
Status: Closed

## Problem Description

Megan Carter reports an Access Denied message when attempting to open the Sales department shared folder.

## Business Impact

The user cannot access active sales proposal documents.

## Affected Systems

- mcarter
- SL-WS-SALES01
- SL-FS01
- \\SL-FS01\Sales

## Troubleshooting

1. Verified workstation network connectivity.
2. Confirmed DNS resolution for SL-FS01.
3. Confirmed the file server was online.
4. Reviewed the user's Active Directory security groups.
5. Found mcarter missing from GG-Sales-Users.

## Root Cause

The user's Sales department group membership had been removed.

## Resolution

Added mcarter back to GG-Sales-Users and refreshed the user's sign-in session.

## Validation

The user successfully opened the Sales share and created a test document.

## User Confirmation

Megan Carter confirmed normal access was restored.

## Status

Closed
```

---

# 49. Ticket Quality Standards

A good ticket should answer:

* Who has the problem?
* What is the problem?
* When did it occur?
* What is the business impact?
* Which systems are involved?
* What was tested?
* What evidence was found?
* What caused the issue?
* What fixed it?
* How was the fix verified?

---

# 50. Ticket Notes to Avoid

Avoid notes such as:

```text
Checked it.

Fixed computer.

Reset stuff.

Network was broken.

User good now.
```

These provide little technical or operational value.

Instead write:

```text
Confirmed the workstation had a valid IPv4 address but was receiving an incorrect DNS server through DHCP. Updated the DHCP scope option and renewed the client lease. Internal DNS resolution then succeeded.
```

---

# 51. Ticket Metrics

As the lab grows, Stoneleaf Systems may track:

* Tickets opened
* Tickets closed
* Incidents by priority
* Incidents by department
* Average simulated resolution time
* Reopened tickets
* Escalated tickets
* Access requests
* Change-related incidents

These metrics may later be used in the Professional Portfolio section.

---

# Ticket Standard Summary

| Area               | Standard                       |
| ------------------ | ------------------------------ |
| Incident           | `INC-####`                     |
| Service Request    | `REQ-####`                     |
| Access Request     | `ACC-####`                     |
| Change Request     | `CHG-####`                     |
| Priorities         | P1, P2, P3, P4                 |
| Default user issue | P3                             |
| Requester          | Named fictional employee       |
| Technician         | Named IT employee              |
| Troubleshooting    | Document chronologically       |
| Root cause         | Required when identified       |
| Resolution         | Must explain corrective action |
| Validation         | Required before closure        |
| Sensitive access   | Requires approval              |
| Ticket storage     | `05-IT-Operations/`            |

---

## Document Status

**Organization:** Stoneleaf Systems

**Primary Ticket Types:** Incident, Service Request, Access Request, Change Request

**Current Phase:** `00-Foundation`

**Current Document:** `Ticket-Standards.md`

**Next Document:** `NetworkPlus-Skills-Matrix.md`

