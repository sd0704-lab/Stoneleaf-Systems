# Stoneleaf Systems — Documentation Standards

## Purpose

This document defines the documentation standards used throughout the Stoneleaf Systems enterprise IT homelab.

The goal is to make the repository resemble the documentation practices of a real IT department while also creating clear portfolio evidence of technical work.

Documentation should explain not only **what was configured**, but also:

* Why the change was needed
* How it was implemented
* How it was tested
* What problems occurred
* How those problems were resolved
* What the final result was

---

# 1. Documentation Principles

Stoneleaf Systems documentation will follow these principles:

* Clear
* Accurate
* Consistent
* Concise
* Repeatable
* Professional
* Technically useful
* Easy to navigate
* Safe for a public repository

Documentation should be written so another IT professional could understand the environment without needing the original author present.

---

# 2. Documentation Platform

GitHub will serve as the primary documentation and portfolio platform.

The repository may contain:

* Markdown files
* Scripts
* Diagrams
* Screenshots
* Configuration examples
* Ticket records
* Change records
* Troubleshooting notes
* Project summaries

Markdown will be the primary format for written technical documentation.

---

# 3. Repository Structure

Documentation must be stored in the section that best matches its purpose.

Examples:

```text
00-Foundation/
01-Network-Infrastructure/
02-Windows-Server-Active-Directory/
03-Endpoint-Administration/
04-Linux-Administration/
05-IT-Operations/
06-PowerShell-Automation/
07-Virtualization/
08-Cloud-Infrastructure/
09-Security/
10-Monitoring-Logging/
11-Backup-Disaster-Recovery/
12-Projects/
13-Professional-Portfolio/
```

Each major section should contain its own:

```text
README.md
```

The section README should explain:

* Purpose
* Scope
* Technologies
* Major tasks
* Skills demonstrated
* Related documents

---

# 4. File Naming

Documentation filenames should use descriptive words separated by hyphens.

Examples:

```text
Organization-Overview.md
IP-Addressing-Plan.md
Active-Directory-Design.md
DHCP-Configuration.md
Server-Build-Procedure.md
```

Avoid vague filenames such as:

```text
notes.md
stuff.md
new.md
test.md
document1.md
```

---

# 5. Standard Document Structure

Technical documents should use a consistent structure where practical.

Recommended format:

```text
# Document Title

## Purpose

## Scope

## Requirements

## Environment

## Procedure

## Validation

## Troubleshooting

## Security Considerations

## Lessons Learned

## Document Status
```

Not every document requires every section.

The structure should fit the purpose of the document.

---

# 6. Purpose Section

Every major technical document should begin with a short explanation of why the document exists.

Example:

```text
## Purpose

This document describes the installation and configuration of the primary Stoneleaf Systems domain controller.
```

The purpose should be understandable without reading the entire document.

---

# 7. Scope

The scope section should identify what is and is not covered.

Example:

```text
## Scope

This procedure covers installation of Active Directory Domain Services on SL-DC01.

DNS configuration is included.

DHCP configuration is documented separately.
```

This helps prevent ambiguity.

---

# 8. Requirements

Technical procedures should document prerequisites when appropriate.

Examples:

* Required VM
* Required operating system
* IP address
* Administrative access
* Network connectivity
* Existing dependencies
* Required software

Example:

```text
## Requirements

- Windows Server installed
- Hostname configured as SL-DC01
- Static IP address: 10.20.20.10
- DNS temporarily configured
- Local administrator access
```

---

# 9. Environment Details

Important system documentation should identify the relevant environment.

Examples:

```text
Hostname: SL-DC01
Operating System: Windows Server
IP Address: 10.20.20.10
Network: VLAN 20 — Servers
Role: Domain Controller / DNS
```

This information should remain consistent with the IP addressing and naming standards.

---

# 10. Procedures

Procedures should be written in the order tasks are performed.

Use numbered steps for actions that must be completed sequentially.

Example:

1. Sign in using an authorized administrative account.
2. Open Server Manager.
3. Select **Add Roles and Features**.
4. Install Active Directory Domain Services.
5. Promote the server to a domain controller.
6. Restart the system.
7. Validate domain services.

Commands should be placed in code blocks.

Example:

```powershell
Get-ADDomain
```

---

# 11. Commands

Commands should be documented exactly as executed when practical.

PowerShell example:

```powershell
Get-ADUser -Filter *
```

Linux example:

```bash
ip addr
```

Network example:

```text
ping 10.20.20.10
```

Commands should not contain real passwords, secrets, or sensitive authentication information.

---

# 12. Screenshots

Screenshots should be used when they provide meaningful evidence.

Useful screenshots include:

* Successful domain join
* Active Directory structure
* Group Policy results
* Firewall rules
* Network configuration
* Azure resources
* Monitoring alerts
* Successful backup
* File permissions
* Troubleshooting evidence

Screenshots should not be added only to make documentation longer.

---

# 13. Screenshot Naming

Screenshots should follow the naming standard:

```text
YYYY-MM-DD_System_Description.png
```

Examples:

```text
2026-08-20_SL-DC01_ADDS-Installed.png
2026-08-21_SL-WS-FIN01_Domain-Joined.png
2026-08-22_SL-FW01_VLAN20-Configured.png
```

---

# 14. Screenshot Security

Before uploading a screenshot, verify it does not expose:

* Passwords
* API keys
* Private keys
* Tokens
* Recovery codes
* Sensitive email addresses
* Personal information
* Public IP information that should remain private
* Billing details
* Cloud secrets

Sensitive information must be removed or obscured before publication.

---

# 15. Diagrams

Architecture and network diagrams should be created when they improve understanding.

Useful diagrams include:

* Logical network architecture
* Physical lab topology
* Active Directory structure
* Azure architecture
* VLAN design
* Backup architecture
* Logging architecture

Diagrams should use the same hostnames, networks, and terminology as the written documentation.

---

# 16. Configuration Evidence

Relevant configurations may be included as evidence.

Examples:

* Firewall rule exports
* PowerShell scripts
* Linux configuration files
* Group Policy settings
* DHCP scope information
* DNS configuration
* Azure configuration examples

Configuration data should be sanitized before publication.

---

# 17. Validation

Major technical procedures should include validation steps.

Validation answers the question:

**How do we know the configuration works?**

Examples:

```text
- Confirm the server responds to ping.
- Confirm DNS resolves the hostname.
- Confirm a user can authenticate.
- Confirm the workstation receives DHCP configuration.
- Confirm the mapped drive appears.
- Confirm the firewall rule permits the intended traffic.
```

---

# 18. Expected Results

Where useful, expected results should be documented.

Example:

```text
Expected Result:

SL-WS-FIN01 should receive an address from the 10.20.30.0/24 network and use 10.20.20.10 for DNS.
```

This makes troubleshooting easier.

---

# 19. Troubleshooting Documentation

Troubleshooting should be treated as portfolio evidence rather than something to hide.

A troubleshooting record should include:

1. Problem reported
2. Symptoms
3. Systems affected
4. Initial hypothesis
5. Tests performed
6. Evidence collected
7. Root cause
8. Corrective action
9. Validation
10. Final resolution

---

# 20. Troubleshooting Example

```text
## Problem

SL-WS-FIN01 could not resolve internal hostnames.

## Symptoms

- Internet access worked.
- IP address was valid.
- Internal DNS names failed.

## Investigation

ipconfig /all showed the workstation was using an external DNS server.

## Root Cause

Incorrect DHCP DNS option.

## Resolution

Updated the DHCP scope to provide 10.20.20.10 as the DNS server.

## Validation

The workstation renewed its DHCP lease and successfully resolved SL-DC01.corp.stoneleaf.test.
```

---

# 21. Lessons Learned

Important projects should include a short lessons-learned section.

Examples:

* What worked well
* What caused problems
* What would be changed next time
* What technical concept became clearer

This demonstrates understanding beyond simply following instructions.

---

# 22. Change Documentation

Major infrastructure changes should reference a change request.

Example:

```text
Change Record: CHG-0003
```

The implementation documentation may then link to or reference the change-management record.

Changes should include:

* Reason
* Risk
* Implementation
* Validation
* Rollback
* Result

---

# 23. Ticket Documentation

Help desk work should be documented using the standards defined in:

```text
Ticket-Standards.md
```

Tickets should use the fictional Stoneleaf Systems employees defined in:

```text
Departments-and-Users.md
```

This keeps the operational simulation consistent.

---

# 24. User References

When documentation references employees, use their defined names and usernames.

Example:

```text
User: Megan Carter
Username: mcarter
Department: Sales
```

Avoid inventing unrelated usernames during later exercises.

---

# 25. Infrastructure References

System names must match the naming standard.

Correct:

```text
SL-DC01
SL-FS01
SL-FW01
SL-WS-FIN01
```

Incorrect:

```text
DC1
Server1
FinancePC
MyFirewall
```

Consistency across documents is required.

---

# 26. IP Address References

Static IP information should match:

```text
IP-Addressing-Plan.md
```

Example:

```text
SL-DC01 — 10.20.20.10
```

If an address changes, both the implementation documentation and IP plan must be updated.

---

# 27. Markdown Heading Standards

Documents should use Markdown heading hierarchy consistently.

Example:

```text
# Document Title

## Major Section

### Subsection
```

Avoid skipping levels unnecessarily.

For example, do not jump directly from:

```text
# Title
```

to:

```text
### Subsection
```

without a reason.

---

# 28. Lists

Use bullet lists for unordered information.

Example:

```text
- DNS
- DHCP
- Active Directory
```

Use numbered lists for sequential procedures.

Example:

```text
1. Configure the hostname.
2. Assign a static IP address.
3. Install the server role.
4. Validate the configuration.
```

---

# 29. Tables

Tables should be used when they make structured information easier to compare.

Example:

| Hostname  | IP Address    | Role              |
| --------- | ------------- | ----------------- |
| `SL-DC01` | `10.20.20.10` | Domain Controller |
| `SL-FS01` | `10.20.20.20` | File Server       |

Avoid extremely wide tables that are difficult to read on GitHub.

---

# 30. Code Blocks

Commands, scripts, configuration snippets, and directory structures should use fenced code blocks.

PowerShell:

```powershell
Get-ADComputer -Filter *
```

Bash:

```bash
systemctl status ssh
```

Plain text:

```text
10.20.20.0/24
```

---

# 31. Sensitive Information

The public repository must never contain real sensitive credentials.

Never publish:

* Passwords
* API keys
* Access tokens
* Private keys
* SSH private keys
* MFA recovery codes
* Azure secrets
* Connection strings containing credentials
* Session cookies
* Personal authentication data

---

# 32. Example Credentials

If credentials are required for demonstration, use obviously fictional placeholders.

Example:

```text
USERNAME: example-user
PASSWORD: <REDACTED>
```

or:

```text
PASSWORD: ExamplePassword-DO-NOT-USE
```

Real credentials should never appear in screenshots or scripts.

---

# 33. Personal Information

The Stoneleaf Systems employees are fictional.

Do not use real sensitive personal information for fictional users.

Avoid including:

* Social Security numbers
* Real home addresses
* Personal banking information
* Real birth dates
* Real medical information

Fictional names are sufficient for identity simulation.

---

# 34. Public Repository Review

Before committing documentation, review it for:

* Credentials
* Sensitive data
* Incorrect IP addresses
* Incorrect hostnames
* Broken Markdown
* Typographical errors
* Unnecessary personal information
* Outdated configuration details

---

# 35. Commit Practices

Git commits should use short descriptions that explain what changed.

Examples:

```text
docs: add IP addressing plan
docs: document Active Directory design
docs: add DHCP configuration
fix: correct server IP address
```

Commit messages do not need to be complicated.

They should simply make the repository history easier to understand.

---

# 36. Documentation Updates

Documentation should be updated when:

* Infrastructure changes
* IP addresses change
* Hostnames change
* Security policies change
* New systems are deployed
* Systems are retired
* Procedures change
* New troubleshooting information is discovered

Outdated documentation can be worse than missing documentation.

---

# 37. Document Status Section

Major documents should end with a status section when useful.

Example:

```text
## Document Status

Organization: Stoneleaf Systems

System: SL-DC01

Status: Complete

Current Phase: 02-Windows-Server-Active-Directory
```

Foundation documents may also identify the next document in sequence.

---

# 38. Project Documentation

Major projects should document the complete project lifecycle.

Recommended structure:

```text
# Project Title

## Objective

## Business Requirement

## Technical Requirements

## Design

## Implementation

## Testing

## Problems Encountered

## Resolution

## Final Result

## Skills Demonstrated

## Lessons Learned
```

This format is especially useful for portfolio projects.

---

# 39. Portfolio Evidence

Strong portfolio documentation should demonstrate:

* Technical planning
* Configuration ability
* Troubleshooting
* Security awareness
* Validation
* Documentation skill
* Understanding of business requirements

The goal is not to produce the largest amount of documentation.

The goal is to produce evidence that demonstrates competent IT work.

---

# 40. Documentation Quality Standard

A technical document should allow another person to answer:

* What system is this?
* Why does it exist?
* How is it configured?
* What does it depend on?
* How was it tested?
* What went wrong?
* How was it fixed?
* Is the implementation complete?

If those questions cannot be answered, the documentation may need additional detail.

---

# 41. Documentation Standard Summary

| Area            | Standard                                   |
| --------------- | ------------------------------------------ |
| Primary format  | Markdown                                   |
| Platform        | GitHub                                     |
| File naming     | Descriptive hyphenated names               |
| Commands        | Fenced code blocks                         |
| Procedures      | Numbered steps                             |
| Screenshots     | Meaningful evidence only                   |
| Diagrams        | Consistent with written architecture       |
| Troubleshooting | Symptoms through validated resolution      |
| Credentials     | Never publish real credentials             |
| Hostnames       | Must follow Naming Standards               |
| IP addresses    | Must match IP Addressing Plan              |
| Users           | Must match Departments and Users           |
| Changes         | Reference change records where appropriate |
| Tickets         | Follow Ticket Standards                    |
| Updates         | Documentation changes with infrastructure  |

---

## Document Status

**Organization:** Stoneleaf Systems

**Documentation Platform:** GitHub

**Primary Format:** Markdown

**Current Phase:** `00-Foundation`

**Current Document:** `Documentation-Standards.md`

**Next Document:** `Change-Management.md`

