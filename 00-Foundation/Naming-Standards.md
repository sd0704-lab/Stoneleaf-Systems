# Stoneleaf Systems — Naming Standards

## Purpose

This document defines the naming conventions used throughout the Stoneleaf Systems enterprise IT environment.

Consistent naming makes systems easier to:

* Identify
* Administer
* Troubleshoot
* Monitor
* Document
* Automate
* Secure
* Scale

Names should provide useful information without becoming unnecessarily long or difficult to manage.

---

# 1. General Naming Principles

Stoneleaf Systems will follow these general rules:

* Names should be descriptive but concise.
* Naming conventions should remain consistent across similar resources.
* Spaces should be avoided in infrastructure names.
* Special characters should be avoided unless required.
* Hostnames will use uppercase letters in documentation for readability.
* Usernames will use lowercase letters.
* Resource names should identify the system's purpose whenever practical.
* Numbers will be used to distinguish multiple systems performing the same role.
* Names should not contain passwords, confidential information, or sensitive personal data.

---

# 2. Organization Prefix

Stoneleaf Systems infrastructure will use the prefix:

```text
SL
```

This identifies systems belonging to the Stoneleaf Systems environment.

Examples:

```text
SL-DC01
SL-FS01
SL-FW01
SL-LNX01
```

---

# 3. Server Naming Standard

Windows and Linux servers will follow:

```text
SL-<ROLE><NUMBER>
```

Example:

```text
SL-DC01
```

Where:

* `SL` = Stoneleaf Systems
* `DC` = Domain Controller
* `01` = Server number

---

## Server Role Abbreviations

| Code   | Role                       |
| ------ | -------------------------- |
| `DC`   | Domain Controller          |
| `FS`   | File Server                |
| `DHCP` | DHCP Server                |
| `WEB`  | Web Server                 |
| `APP`  | Application Server         |
| `DB`   | Database Server            |
| `MON`  | Monitoring Server          |
| `LOG`  | Logging Server             |
| `SIEM` | SIEM / Security Logging    |
| `BKP`  | Backup Server              |
| `LNX`  | General Linux Server       |
| `MGMT` | Management Server          |
| `JMP`  | Administrative Jump Server |
| `PKI`  | Certificate Services       |
| `WSUS` | Windows Update Server      |

---

## Examples

```text
SL-DC01
SL-DC02
SL-FS01
SL-LNX01
SL-MON01
SL-LOG01
SL-BKP01
```

When multiple servers provide the same function, numbering will increase sequentially.

Example:

```text
SL-DC01
SL-DC02
```

---

# 4. Windows Workstation Naming Standard

Employee workstations will follow:

```text
SL-WS-<DEPARTMENT><NUMBER>
```

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

Special-purpose workstations may use a descriptive role instead of a department.

Examples:

```text
SL-WS-REMOTE01
SL-WS-TEST01
```

---

# 5. Department Abbreviations

| Department                       | Code    |
| -------------------------------- | ------- |
| Executive Management             | `EXEC`  |
| Information Technology           | `IT`    |
| Operations                       | `OPS`   |
| Sales                            | `SALES` |
| Customer Service                 | `CS`    |
| Finance                          | `FIN`   |
| Human Resources / Administration | `HR`    |

These abbreviations should be reused where practical throughout the environment.

---

# 6. Network Device Naming

Network devices will follow:

```text
SL-<DEVICE><NUMBER>
```

Common abbreviations include:

| Code  | Device                |
| ----- | --------------------- |
| `FW`  | Firewall              |
| `SW`  | Switch                |
| `RTR` | Router                |
| `AP`  | Wireless Access Point |
| `VPN` | VPN Appliance         |
| `WLC` | Wireless Controller   |

Examples:

```text
SL-FW01
SL-SW01
SL-SW02
SL-AP01
SL-AP02
```

The primary pfSense firewall will be:

```text
SL-FW01
```

---

# 7. Active Directory Domain Naming

The Stoneleaf Systems Active Directory lab domain will use:

```text
corp.stoneleaf.test
```

The `.test` namespace is appropriate for the fictional lab environment and avoids dependence on a real publicly registered domain.

The NetBIOS domain name will be:

```text
STONELEAF
```

Example Windows sign-in format:

```text
STONELEAF\sdempsey
```

or:

```text
sdempsey@corp.stoneleaf.test
```

---

# 8. Standard User Account Naming

Standard user accounts will follow:

```text
first initial + last name
```

All usernames will use lowercase letters.

Examples:

| Employee        | Username   |
| --------------- | ---------- |
| Scott Dempsey   | `sdempsey` |
| Michael Bennett | `mbennett` |
| Rachel Morgan   | `rmorgan`  |
| Olivia Chen     | `ochen`    |
| Priya Shah      | `pshah`    |
| Rebecca Adams   | `radams`   |

---

# 9. Duplicate Usernames

If two employees would receive the same username, the second account will use an additional character or number.

Example:

```text
jsmith
jsmith2
```

A username should never be reassigned to a different employee while the original identity could still appear in logs, backups, or historical records.

---

# 10. Administrative Account Naming

Privileged IT accounts will remain separate from standard employee accounts.

Administrative accounts will use:

```text
<standard username>-admin
```

Examples:

```text
sdempsey-admin
ochen-admin
mreed-admin
kwallace-admin
```

Example:

```text
Standard Account:
sdempsey

Administrative Account:
sdempsey-admin
```

Administrative accounts should only be used when elevated privileges are required.

---

# 11. Service Account Naming

Service accounts will use:

```text
svc-<service>
```

Examples:

```text
svc-backup
svc-monitoring
svc-deployment
svc-siem
svc-scanner
```

If multiple service accounts exist for the same platform, an additional function or number may be added.

Example:

```text
svc-sql-backup
svc-sql-reporting
```

Service account names should clearly indicate that they are not normal employee accounts.

---

# 12. Security Group Naming

Stoneleaf Systems will use prefixes to identify group purpose and scope.

---

## Global Groups

Department and role membership groups will use:

```text
GG-<Department-or-Role>
```

Examples:

```text
GG-Executive-Users
GG-IT-Users
GG-Operations-Users
GG-Sales-Users
GG-CustomerService-Users
GG-Finance-Users
GG-HR-Users
```

---

## Domain Local Resource Groups

Resource permission groups will use:

```text
DL-<Resource>-<Permission>
```

Examples:

```text
DL-Finance-RW
DL-Finance-RO

DL-HR-RW
DL-HR-RO

DL-Sales-RW
DL-Sales-RO
```

Where:

```text
RW = Read / Write
RO = Read Only
```

---

# 13. Administrative Security Groups

Privileged groups created specifically for Stoneleaf Systems administration should clearly identify their purpose.

Examples:

```text
GG-Server-Admins
GG-Network-Admins
GG-Cloud-Admins
GG-HelpDesk
GG-Workstation-Admins
```

Built-in Active Directory privileged groups should be used carefully and only when required.

---

# 14. Organizational Unit Naming

Active Directory Organizational Units should use clear names without unnecessary abbreviations.

Planned structure:

```text
Stoneleaf-Systems
│
├── Users
│   ├── Executive
│   ├── IT
│   ├── Operations
│   ├── Sales
│   ├── Customer-Service
│   ├── Finance
│   └── HR-Administration
│
├── Admin-Accounts
├── Groups
├── Servers
├── Workstations
└── Service-Accounts
```

OU names should represent administrative or Group Policy boundaries rather than simply recreating the organizational chart without purpose.

---

# 15. Group Policy Naming

Group Policy Objects will use:

```text
GPO-<Scope>-<Purpose>
```

Examples:

```text
GPO-Domain-PasswordPolicy
GPO-Workstations-SecurityBaseline
GPO-Workstations-WindowsFirewall
GPO-Users-DriveMappings
GPO-Finance-Restrictions
GPO-HR-Restrictions
GPO-Servers-AuditPolicy
```

The name should make both the intended target and purpose obvious.

---

# 16. File Share Naming

Department shares should use straightforward department names.

Examples:

```text
\\SL-FS01\Executive
\\SL-FS01\IT
\\SL-FS01\Operations
\\SL-FS01\Sales
\\SL-FS01\Customer-Service
\\SL-FS01\Finance
\\SL-FS01\HR
\\SL-FS01\Company-Shared
```

Hidden administrative shares may use a `$` suffix where appropriate.

Example:

```text
\\SL-FS01\IT-Admin$
```

---

# 17. Printer Naming

Network printers will follow:

```text
SL-PRN-<LOCATION><NUMBER>
```

Examples:

```text
SL-PRN-OFFICE01
SL-PRN-FIN01
SL-PRN-HR01
```

If physical location becomes important later, building, floor, or room identifiers may be added.

---

# 18. Virtual Machine Naming

VMware virtual machine names should normally match the guest operating system hostname.

Example:

```text
VMware VM Name: SL-DC01
Guest Hostname: SL-DC01
```

This avoids confusion between the virtualization platform and the operating system.

Temporary systems may include:

```text
-TEMP
```

or:

```text
-TEST
```

Example:

```text
SL-W11-TEST01
```

Temporary systems should be removed when they are no longer required.

---

# 19. Snapshot Naming

VMware snapshots should clearly identify why and when they were created.

Recommended format:

```text
YYYY-MM-DD_<Description>
```

Examples:

```text
2026-08-18_Initial-Install
2026-08-19_Pre-Domain-Join
2026-08-19_Post-Domain-Join
2026-08-20_Pre-GPO-Testing
```

Snapshots should not be treated as long-term backups.

---

# 20. Azure Resource Naming

Azure resource names should include:

* Organization
* Resource type
* Purpose
* Environment when applicable
* Number when required

Recommended format:

```text
sl-<resource>-<purpose>-<environment>-<number>
```

Azure names will normally use lowercase letters.

---

## Azure Resource Abbreviations

| Resource                | Code    |
| ----------------------- | ------- |
| Resource Group          | `rg`    |
| Virtual Network         | `vnet`  |
| Subnet                  | `snet`  |
| Virtual Machine         | `vm`    |
| Network Security Group  | `nsg`   |
| Network Interface       | `nic`   |
| Public IP               | `pip`   |
| Storage Account         | `st`    |
| Log Analytics Workspace | `law`   |
| Key Vault               | `kv`    |
| VPN Gateway             | `vpngw` |

---

## Azure Examples

```text
sl-rg-core-lab
sl-vnet-core-lab-01
sl-snet-servers
sl-snet-management
sl-vm-admin-lab-01
sl-nsg-servers
sl-law-monitoring-lab
```

Some Azure services have unique naming restrictions. Those restrictions will take precedence where required.

---

# 21. Azure Resource Groups

Resource groups should identify the workload or function they contain.

Examples:

```text
sl-rg-core-lab
sl-rg-network-lab
sl-rg-security-lab
sl-rg-monitoring-lab
```

Resources should not be placed randomly into unrelated resource groups.

---

# 22. VLAN Naming

VLANs will use:

```text
VLAN <ID> — <PURPOSE>
```

Current standard:

```text
VLAN 10 — Management
VLAN 20 — Servers
VLAN 30 — Workstations
VLAN 40 — IT Administration
VLAN 50 — Corporate Wireless
VLAN 60 — Guest Wireless
VLAN 70 — Lab/Test
VLAN 80 — VPN
```

Where configuration syntax requires a short name, examples include:

```text
MGMT
SERVERS
WORKSTATIONS
IT-ADMIN
CORP-WIFI
GUEST-WIFI
LAB
VPN
```

---

# 23. Firewall Rule Naming

Firewall rules should describe the traffic being permitted or denied.

Recommended format:

```text
<Action>-<Source>-to-<Destination>-<Service>
```

Examples:

```text
Allow-Workstations-to-DNS
Allow-ITAdmin-to-Servers-RDP
Allow-Servers-to-Internet-HTTPS
Deny-Guest-to-Internal
```

Rules should not use vague names such as:

```text
Rule1
NewRule
Test
AllowAll
```

---

# 24. DHCP Scope Naming

DHCP scopes should identify the network they serve.

Examples:

```text
SCOPE-Workstations
SCOPE-Corporate-WiFi
SCOPE-Guest-WiFi
SCOPE-Lab
```

---

# 25. DNS Record Naming

DNS host records should normally match the system hostname.

Example:

```text
SL-DC01
SL-FS01
SL-LNX01
```

Fully qualified names would therefore appear as:

```text
SL-DC01.corp.stoneleaf.test
SL-FS01.corp.stoneleaf.test
SL-LNX01.corp.stoneleaf.test
```

---

# 26. Help Desk Ticket Naming

Stoneleaf Systems tickets will use an identifier based on ticket type.

Standard formats:

```text
INC-####
REQ-####
ACC-####
CHG-####
```

Where:

| Prefix | Type            |
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

---

# 27. Ticket Titles

Ticket titles should briefly identify the user and issue.

Good examples:

```text
INC-0007 — Megan Carter Cannot Access Sales Share

REQ-0012 — Joshua Martin Password Reset

ACC-0005 — Rebecca Adams Finance Reporting Access

INC-0018 — Emily Parker Internal DNS Failure
```

Poor titles include:

```text
Computer broken

Help

Network issue

User problem
```

---

# 28. Change Request Naming

Change records will use:

```text
CHG-####
```

Example:

```text
CHG-0001 — Deploy Primary Domain Controller

CHG-0002 — Create Workstation VLAN

CHG-0003 — Configure Finance File Share
```

---

# 29. Incident Naming

Infrastructure and security incidents will use:

```text
INC-####
```

Examples:

```text
INC-0021 — Domain Authentication Failure

INC-0022 — File Server Unavailable

INC-0023 — Workstation DHCP Failure
```

---

# 30. Script Naming

Scripts should describe the action they perform.

PowerShell scripts will use:

```text
Verb-Noun.ps1
```

Examples:

```text
New-StoneleafUser.ps1
Disable-StoneleafUser.ps1
Get-ComputerInventory.ps1
Get-ADUserReport.ps1
Test-ServerHealth.ps1
```

Bash scripts should use descriptive lowercase names separated by hyphens.

Examples:

```text
update-server.sh
check-disk-usage.sh
collect-logs.sh
```

---

# 31. Documentation File Naming

Repository documentation will use descriptive filenames with hyphens separating words.

Examples:

```text
Organization-Overview.md
Departments-and-Users.md
Business-Requirements.md
Technical-Requirements.md
Logical-Architecture.md
IP-Addressing-Plan.md
Naming-Standards.md
```

Each major repository section should contain:

```text
README.md
```

as its landing page.

---

# 32. Screenshot Naming

Screenshots used as portfolio evidence should follow:

```text
YYYY-MM-DD_System_Description.png
```

Examples:

```text
2026-08-20_SL-DC01_ADDS-Installed.png

2026-08-21_SL-WS-FIN01_Domain-Joined.png

2026-08-22_SL-FW01_VLAN20-Configuration.png
```

This makes screenshots easier to organize chronologically.

---

# 33. Diagram Naming

Network and architecture diagrams should use descriptive names.

Examples:

```text
Stoneleaf-Logical-Architecture.png

Stoneleaf-Network-Topology.png

Stoneleaf-Active-Directory-Design.png

Stoneleaf-Azure-Architecture.png
```

Editable source files should use the same base filename where possible.

---

# 34. Backup Naming

Backup jobs should identify the protected system or workload.

Examples:

```text
BKP-SL-FS01-Daily
BKP-SL-DC01-SystemState
BKP-Network-Configs
```

Backup files should include dates when appropriate.

Example:

```text
SL-FW01_Config_2026-08-18.xml
```

---

# 35. Monitoring Naming

Monitoring objects should use the same hostname as the device being monitored whenever possible.

Examples:

```text
SL-DC01
SL-FS01
SL-FW01
```

Alerts should clearly identify both the affected system and condition.

Example:

```text
SL-FS01 — Disk Space Critical
```

---

# 36. Asset Naming

Asset identifiers may use:

```text
SL-AST-####
```

Examples:

```text
SL-AST-0001
SL-AST-0002
SL-AST-0003
```

Asset records can then associate the identifier with:

* Hostname
* Serial number
* Assigned employee
* Department
* Device type
* Status

---

# 37. Environment Identifiers

When multiple environments exist, the following abbreviations may be used:

| Environment           | Code  |
| --------------------- | ----- |
| Production Simulation | `PRD` |
| Test                  | `TST` |
| Development           | `DEV` |
| Lab                   | `LAB` |

Because Stoneleaf Systems is primarily a homelab, these identifiers should only be added when they provide useful distinction.

---

# 38. Names That Should Be Avoided

Infrastructure should not use vague or generic names such as:

```text
SERVER1
SERVER2
PC1
TEST
NEWPC
ADMINPC
USER1
USER2
ROUTER
WINDOWS
UBUNTU
```

These names provide little information about the system's function.

Instead use:

```text
SL-DC01
SL-FS01
SL-WS-FIN01
SL-LNX01
SL-FW01
```

---

# 39. Naming Standard Summary

| Resource           | Format                      | Example                             |
| ------------------ | --------------------------- | ----------------------------------- |
| Server             | `SL-<ROLE><##>`             | `SL-DC01`                           |
| Workstation        | `SL-WS-<DEPT><##>`          | `SL-WS-FIN01`                       |
| Firewall           | `SL-FW<##>`                 | `SL-FW01`                           |
| Switch             | `SL-SW<##>`                 | `SL-SW01`                           |
| Access Point       | `SL-AP<##>`                 | `SL-AP01`                           |
| User               | Initial + surname           | `sdempsey`                          |
| Admin User         | `<username>-admin`          | `sdempsey-admin`                    |
| Service Account    | `svc-<service>`             | `svc-backup`                        |
| Global Group       | `GG-<role>`                 | `GG-Finance-Users`                  |
| Domain Local Group | `DL-<resource>-<access>`    | `DL-Finance-RW`                     |
| Group Policy       | `GPO-<scope>-<purpose>`     | `GPO-Workstations-SecurityBaseline` |
| Incident           | `INC-####`                  | `INC-0001`                          |
| Service Request    | `REQ-####`                  | `REQ-0001`                          |
| Access Request     | `ACC-####`                  | `ACC-0001`                          |
| Change Request     | `CHG-####`                  | `CHG-0001`                          |
| PowerShell Script  | `Verb-Noun.ps1`             | `New-StoneleafUser.ps1`             |
| Azure Resource     | `sl-<type>-<purpose>-<env>` | `sl-vnet-core-lab-01`               |

---

# 40. Naming Standard Enforcement

New infrastructure should be checked against this document before deployment.

When a naming convention must be changed:

1. Identify why the existing standard no longer works.
2. Determine the impact on existing systems.
3. Document the proposed change.
4. Update this document.
5. Apply the new standard consistently going forward.
6. Rename existing resources only when the operational benefit outweighs the risk.

Consistency is more important than unnecessarily renaming functioning systems.

---

## Document Status

**Organization:** Stoneleaf Systems

**Active Directory Domain:** `corp.stoneleaf.test`

**NetBIOS Domain:** `STONELEAF`

**Infrastructure Prefix:** `SL`

**Current Phase:** `00-Foundation`

**Current Document:** `Naming-Standards.md`

**Next Document:** `Documentation-Standards.md`

