# Stoneleaf Systems — Departments and Users

## Purpose

This document defines the departments, employee roles, user identities, account names, and baseline access requirements for the Stoneleaf Systems lab environment.

Every user in the environment is assigned a realistic first and last name so that Active Directory, Microsoft Entra ID, help desk tickets, permissions, onboarding tasks, and administrative scenarios resemble a real business environment.

---

## Organization Size

Stoneleaf Systems currently has **40 employees** across seven departments:

* Executive Management
* Information Technology
* Operations
* Sales
* Customer Service
* Finance
* Human Resources and Administration

---

## Username Standard

Standard user accounts will follow the format:

`first initial + last name`

Examples:

* Ethan Brooks → `ebrooks`
* Maya Patel → `mpatel`
* Daniel Ruiz → `druiz`

If duplicate usernames occur in the future, a number or additional initial may be used.

Example:

`jsmith2`

Administrative accounts will remain separate from normal day-to-day user accounts.

Example:

* Standard account: `sdempsey`
* Administrative account: `sdempsey-admin`

Users should not perform normal email, web browsing, or productivity work while signed into privileged accounts.

---

# 1. Executive Management

Executive Management is responsible for company strategy, organizational leadership, financial direction, and business oversight.

| Employee        | Username   | Role                             |
| --------------- | ---------- | -------------------------------- |
| Michael Bennett | `mbennett` | Chief Executive Officer          |
| Rachel Morgan   | `rmorgan`  | Chief Operating Officer          |
| Thomas Keller   | `tkeller`  | Chief Financial Officer          |
| Natalie Hayes   | `nhayes`   | Director of Business Development |

### Department Access

Executive users require access to:

* Microsoft 365
* Company-wide business information
* Executive shared files
* Management reports
* Financial reports where authorized
* Remote-access services
* Collaboration platforms

Executive data should be restricted from general employees.

---

# 2. Information Technology

The Information Technology department manages the Stoneleaf Systems technical environment.

| Employee      | Username   | Role                  |
| ------------- | ---------- | --------------------- |
| Scott Dempsey | `sdempsey` | Systems Administrator |
| Ian Turner    | `iturner`  | IT Support Specialist |
| Olivia Chen   | `ochen`    | Network Administrator |
| Marcus Reed   | `mreed`    | Cloud Administrator   |
| Priya Shah    | `pshah`    | IT Support Technician |
| Kevin Wallace | `kwallace` | IT Manager            |

---

## IT Administrative Accounts

Privileged accounts will be created separately for users who require administrative permissions.

| Employee      | Administrative Account | Purpose                                    |
| ------------- | ---------------------- | ------------------------------------------ |
| Scott Dempsey | `sdempsey-admin`       | Server and Active Directory administration |
| Olivia Chen   | `ochen-admin`          | Network administration                     |
| Marcus Reed   | `mreed-admin`          | Cloud administration                       |
| Kevin Wallace | `kwallace-admin`       | Senior IT administration                   |

IT Support personnel may receive limited delegated permissions rather than full administrative access.

---

## IT Responsibilities

The IT department is responsible for:

* Active Directory
* Microsoft Entra ID
* Windows Server
* Windows endpoints
* Linux systems
* DNS
* DHCP
* Network infrastructure
* pfSense
* Microsoft Azure
* User provisioning
* Access management
* Help desk support
* Patch management
* Monitoring
* Logging
* Backup
* Security administration
* Documentation
* Troubleshooting

---

# 3. Operations

The Operations department manages day-to-day service delivery, internal processes, scheduling, logistics, and business coordination.

| Employee        | Username    | Role                   |
| --------------- | ----------- | ---------------------- |
| Daniel Foster   | `dfoster`   | Operations Manager     |
| Lauren Mitchell | `lmitchell` | Operations Supervisor  |
| Brandon Cole    | `bcole`     | Operations Coordinator |
| Samantha Price  | `sprice`    | Operations Coordinator |
| Eric Lawson     | `elawson`   | Operations Specialist  |
| Jennifer Walsh  | `jwalsh`    | Operations Specialist  |
| Nathan Cooper   | `ncooper`   | Logistics Coordinator  |
| Alicia Grant    | `agrant`    | Project Coordinator    |

### Department Access

Operations users require access to:

* Operations shared folders
* Scheduling information
* Internal procedures
* Project documentation
* Microsoft 365
* Approved business applications
* Shared printers
* Department collaboration resources

Operations users should not have access to confidential HR or Finance information.

---

# 4. Sales

The Sales department manages customer acquisition, account development, proposals, and revenue opportunities.

| Employee         | Username   | Role                     |
| ---------------- | ---------- | ------------------------ |
| Christopher Hall | `chall`    | Sales Manager            |
| Megan Carter     | `mcarter`  | Senior Account Executive |
| Andrew Collins   | `acollins` | Account Executive        |
| Jessica Ramirez  | `jramirez` | Account Executive        |
| Tyler Murphy     | `tmurphy`  | Sales Representative     |
| Sophia Nguyen    | `snguyen`  | Sales Representative     |

### Department Access

Sales users require access to:

* Customer records
* Sales documentation
* Proposal templates
* Sales shared folders
* Microsoft 365
* CRM resources
* Remote access when traveling

Sales users should only access customer and company data required for their assigned responsibilities.

---

# 5. Customer Service

Customer Service handles customer questions, support requests, account assistance, and service coordination.

| Employee        | Username    | Role                            |
| --------------- | ----------- | ------------------------------- |
| Amanda Sullivan | `asullivan` | Customer Service Manager        |
| Joshua Martin   | `jmartin`   | Customer Service Representative |
| Emily Parker    | `eparker`   | Customer Service Representative |
| Noah Anderson   | `nanderson` | Customer Service Representative |
| Grace Thompson  | `gthompson` | Customer Service Representative |
| Lucas Rivera    | `lrivera`   | Customer Service Representative |

### Department Access

Customer Service users require access to:

* Customer-service applications
* Customer records
* Shared customer-service files
* Microsoft 365
* Ticketing resources
* Internal knowledge base

Customer Service users should not have administrative access to infrastructure systems.

---

# 6. Finance

The Finance department manages accounting, payroll coordination, budgeting, accounts payable, accounts receivable, and financial reporting.

| Employee       | Username   | Role                           |
| -------------- | ---------- | ------------------------------ |
| Rebecca Adams  | `radams`   | Finance Manager                |
| Benjamin Clark | `bclark`   | Senior Accountant              |
| Chloe Edwards  | `cedwards` | Accounts Payable Specialist    |
| Jason Brooks   | `jbrooks`  | Accounts Receivable Specialist |
| Victoria Lewis | `vlewis`   | Financial Analyst              |

### Department Access

Finance users require access to:

* Finance shared folders
* Accounting applications
* Financial reports
* Budget information
* Microsoft 365
* Payroll-related information where authorized

Finance data must be restricted from unauthorized users.

---

# 7. Human Resources and Administration

Human Resources and Administration manages employee records, hiring, onboarding, benefits coordination, company policies, and general office administration.

| Employee        | Username  | Role                     |
| --------------- | --------- | ------------------------ |
| Kimberly Wright | `kwright` | Human Resources Manager  |
| Jonathan Evans  | `jevans`  | HR Generalist            |
| Melissa Green   | `mgreen`  | Recruiting Coordinator   |
| Hannah Scott    | `hscott`  | Administrative Assistant |
| Patrick Young   | `pyoung`  | Office Administrator     |

### Department Access

HR and Administration users require access to:

* Employee records
* HR shared folders
* Hiring documentation
* Onboarding documentation
* Company policies
* Microsoft 365
* Administrative resources

HR data must be considered confidential and restricted to authorized personnel.

---

# Employee Summary

| Department                         | Employees |
| ---------------------------------- | --------: |
| Executive Management               |         4 |
| Information Technology             |         6 |
| Operations                         |         8 |
| Sales                              |         6 |
| Customer Service                   |         6 |
| Finance                            |         5 |
| Human Resources and Administration |         5 |
| **Total**                          |    **40** |

---

# Active Directory Department Structure

The planned Active Directory structure will use Organizational Units to separate users by department.

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
│
├── Groups
│
├── Servers
│
├── Workstations
│
└── Service-Accounts
```

The final OU structure will be implemented during the Windows Server and Active Directory phase.

---

# Security Group Strategy

Users will receive access primarily through security-group membership rather than through individual permissions.

Planned examples include:

```text
GG-Executive-Users
GG-IT-Users
GG-Operations-Users
GG-Sales-Users
GG-CustomerService-Users
GG-Finance-Users
GG-HR-Users
```

Resource access groups may include:

```text
DL-Finance-RW
DL-Finance-RO

DL-HR-RW
DL-HR-RO

DL-Sales-RW
DL-Sales-RO

DL-Operations-RW
DL-Operations-RO
```

This structure will allow Stoneleaf Systems to practice role-based access control and proper Active Directory permission management.

---

# Standard User Permissions

Standard users should be able to:

* Sign into assigned workstations
* Access Microsoft 365
* Use approved applications
* Access department resources
* Print to approved printers
* Access authorized file shares
* Change their own passwords

Standard users should not be able to:

* Install unauthorized software
* Modify system-wide settings
* Create Active Directory users
* Modify Group Policy
* Change firewall configuration
* Administer servers
* Modify other users' permissions

---

# Administrative Access

Administrative access will follow the principle of least privilege.

Privileged access will be divided where practical between:

* Help desk administration
* Active Directory administration
* Server administration
* Network administration
* Cloud administration
* Security administration

Administrative users will use separate privileged accounts.

For example:

```text
sdempsey
sdempsey-admin
```

The normal account will be used for everyday work.

The administrative account will only be used when elevated permissions are required.

---

# Service Accounts

Service accounts will be created only when a technical service specifically requires them.

Examples may include:

```text
svc-backup
svc-monitoring
svc-deployment
svc-siem
```

Service accounts should:

* Not be used for normal interactive login.
* Receive only required permissions.
* Use strong credentials.
* Be documented.
* Have ownership assigned.
* Be reviewed periodically.

---

# User Lifecycle

Stoneleaf Systems will simulate the complete employee account lifecycle.

## New Hire

Typical onboarding tasks will include:

1. Receive approved onboarding request.
2. Create Active Directory account.
3. Assign department OU.
4. Configure username.
5. Assign security groups.
6. Provision Microsoft 365 or cloud access.
7. Assign workstation.
8. Configure department resources.
9. Verify access.
10. Document completion in the help desk ticket.

## Role Change

When an employee changes roles:

1. Review existing permissions.
2. Remove permissions no longer required.
3. Add new department or role access.
4. Update job-title information.
5. Verify application access.
6. Document the change.

## Termination

Employee offboarding will include:

1. Disable the user account.
2. Revoke active sessions where applicable.
3. Remove remote access.
4. Protect or transfer business data.
5. Remove unnecessary group memberships.
6. Recover company equipment.
7. Preserve required records.
8. Document completion.

---

# Example Help Desk Scenarios

These users will also provide realistic identities for future help desk and troubleshooting scenarios.

Examples may include:

* Megan Carter cannot access the Sales shared folder.
* Joshua Martin forgot his password.
* Rebecca Adams needs access to a Finance reporting folder.
* Alicia Grant receives an IP-address conflict.
* Hannah Scott cannot connect to a network printer.
* Daniel Foster needs VPN access while traveling.
* Emily Parker's workstation cannot resolve internal DNS.
* Marcus Reed needs an Azure role assignment.
* Priya Shah needs delegated password-reset permissions.
* Jonathan Evans requests access for a newly hired employee.

These scenarios will become tickets within the IT Operations portion of the lab.

---

# Design Principles

## Realistic Identities

All user accounts represent named fictional employees rather than generic numbered accounts.

## Least Privilege

Users receive only the permissions required to perform their assigned roles.

## Group-Based Access

Permissions will be assigned through groups whenever possible.

## Separate Administrative Accounts

Privileged IT work will use dedicated administrative accounts.

## Documented Account Lifecycle

Account creation, modification, access changes, and termination will be documented through simulated IT processes.

---

## Document Status

**Organization:** Stoneleaf Systems

**Employee Count:** 40

**Departments:** 7

**Current Phase:** `00-Foundation`

**Current Document:** `Departments-and-Users.md`

**Next Document:** `Business-Requirements.md`

