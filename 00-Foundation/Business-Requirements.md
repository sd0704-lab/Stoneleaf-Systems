# Stoneleaf Systems — Business Requirements

## Purpose

This document defines the business requirements that the Stoneleaf Systems IT environment must support.

These requirements explain **why** the organization needs specific technologies, services, security controls, and operational processes.

Technical solutions will be designed later based on these business needs.

---

# 1. Organizational Requirements

Stoneleaf Systems operates as a growing hybrid organization with approximately **40 employees** across seven departments.

The IT environment must support:

* Executive Management
* Information Technology
* Operations
* Sales
* Customer Service
* Finance
* Human Resources and Administration

The infrastructure must support both office-based and remote employees.

---

# 2. Centralized Identity Management

Stoneleaf Systems requires centralized management of user identities.

The organization must be able to:

* Create employee accounts.
* Disable terminated employee accounts.
* Reset passwords.
* Control user access.
* Assign permissions based on job role.
* Manage administrative accounts separately.
* Apply consistent authentication policies.
* Manage access to local and cloud resources.

User access should be based primarily on department and job responsibilities.

---

# 3. Role-Based Access

Employees must only have access to information and systems required for their jobs.

The environment must support:

* Department-based access.
* Role-based permissions.
* Security groups.
* Read-only and read/write permissions.
* Restricted administrative access.
* Separation of confidential information.

Sensitive departments such as Finance and Human Resources must have additional access restrictions.

---

# 4. Employee Onboarding

Stoneleaf Systems requires a repeatable onboarding process for new employees.

IT must be able to provision:

* User accounts
* Email and collaboration access
* Department permissions
* Security-group memberships
* Workstations
* Business applications
* Shared folders
* Remote access when required

Onboarding activities must be documented through the IT ticketing process.

---

# 5. Employee Offboarding

Stoneleaf Systems requires a controlled process for removing employee access.

When an employee leaves the organization, IT must be able to:

* Disable accounts.
* Revoke remote access.
* Remove unnecessary permissions.
* Protect company data.
* Recover company-owned equipment.
* Transfer business files where required.
* Preserve required records.
* Document completion of the offboarding process.

Access should be removed promptly to reduce security risk.

---

# 6. Workstation Management

Employees require reliable company-managed workstations.

IT must be able to:

* Deploy Windows endpoints.
* Configure standard workstation settings.
* Join computers to centralized identity services.
* Apply security policies.
* Install approved software.
* Manage updates.
* Troubleshoot hardware and software problems.
* Track assigned devices.
* Restrict unauthorized administrative access.

Workstations should follow a standardized configuration whenever possible.

---

# 7. Server Infrastructure

Stoneleaf Systems requires centralized server services to support business operations.

The organization needs systems capable of supporting:

* Identity services
* DNS
* DHCP
* File sharing
* Administrative services
* Logging
* Monitoring
* Backup
* Security functions

Server infrastructure should be manageable, documented, recoverable, and scalable.

---

# 8. Network Connectivity

Employees require reliable network connectivity to company resources.

The network must support:

* Wired connectivity
* Wireless connectivity
* Internet access
* Internal business systems
* Servers
* Workstations
* Printers
* Cloud services
* Remote connectivity

IT must be able to troubleshoot connectivity problems and identify failures efficiently.

---

# 9. Network Segmentation

Stoneleaf Systems requires the ability to separate different categories of devices and traffic.

Future network design should allow segmentation for systems such as:

* Servers
* Employee workstations
* Administrative systems
* Wireless clients
* Guest devices
* Management interfaces
* Lab or test systems

Segmentation should reduce unnecessary access between systems and improve security.

---

# 10. Internet Access

Employees require reliable internet connectivity for normal business operations.

Internet access is required for:

* Microsoft 365
* Cloud applications
* Customer communication
* Vendor websites
* Software updates
* Remote services
* Research
* Business applications

The organization must be able to control and troubleshoot internet connectivity.

---

# 11. Remote Work

Stoneleaf Systems supports a hybrid workforce.

Authorized employees must be able to securely access approved company services while working outside the main office.

Remote access may include:

* Microsoft 365
* Cloud applications
* Internal resources
* File access
* VPN connectivity
* Remote technical support

Remote access must require appropriate authentication and authorization.

---

# 12. File Storage and Sharing

Employees require shared storage for business documents.

The organization must support:

* Department file shares
* Shared business documents
* Controlled permissions
* Read-only access
* Read/write access
* Restricted confidential folders
* Centralized administration
* Backup and recovery

Access should be assigned using security groups whenever possible.

---

# 13. Finance Data Protection

Finance information is considered sensitive business data.

Finance systems and files must be restricted to authorized personnel.

Requirements include:

* Restricted file permissions
* Limited group membership
* Controlled administrative access
* Backup protection
* Logging where appropriate
* Removal of access when no longer required

General employees should not be able to access Finance data.

---

# 14. Human Resources Data Protection

Human Resources maintains confidential employee information.

HR resources must be protected from unauthorized access.

Sensitive information may include:

* Employee records
* Hiring documentation
* Compensation information
* Benefits information
* Disciplinary records
* Personnel documents

Access must be limited to authorized HR personnel and approved management roles.

---

# 15. Cloud Services

Stoneleaf Systems requires cloud capabilities to support business growth and remote work.

Microsoft Azure will serve as the primary cloud platform.

Cloud services may support:

* Virtual machines
* Virtual networking
* Identity
* Storage
* Security
* Testing
* Hybrid connectivity
* Backup
* Monitoring

Cloud resources must follow documented naming, security, and access standards.

---

# 16. Microsoft 365 and Collaboration

Employees require business communication and collaboration capabilities.

The organization should support services such as:

* Email
* Calendars
* Document collaboration
* Meetings
* File sharing
* Team communication

User access should be centrally administered and removed when employment ends.

---

# 17. Security

Stoneleaf Systems must protect company systems and information from unauthorized access, misuse, accidental loss, and common security threats.

Security requirements include:

* Strong authentication
* Least privilege
* Role-based access
* Separate administrative accounts
* Secure remote access
* Patch management
* Endpoint protection
* Firewall controls
* Logging
* Security monitoring
* Data backup
* Recovery procedures
* Account lifecycle management

Security should be integrated into all major infrastructure decisions.

---

# 18. Administrative Account Separation

Employees with elevated IT privileges must use separate accounts for administrative work.

For example:

```text
sdempsey
sdempsey-admin
```

The standard account will be used for:

* Email
* Web browsing
* Documentation
* Normal user activities

The administrative account will be used only when elevated privileges are required.

This reduces the risk associated with performing everyday activities using privileged credentials.

---

# 19. Help Desk Support

Employees require a defined method for requesting technical assistance.

IT must be able to document and manage:

* Password resets
* Hardware problems
* Software problems
* Access requests
* Network issues
* Printer problems
* Account problems
* Application issues
* Remote-access problems

Each support request should include enough information to track the issue from initial report through resolution.

---

# 20. Ticket Management

Stoneleaf Systems requires a standardized ticketing process.

Tickets should include:

* Ticket number
* Requester
* Department
* Issue type
* Priority
* Description
* Troubleshooting performed
* Actions taken
* Resolution
* Technician
* Status
* Closure notes

Ticketing will be used to simulate real IT operational workflows.

---

# 21. Change Management

Significant infrastructure changes must be documented before implementation.

Examples include:

* Server deployment
* Firewall changes
* Network changes
* Group Policy changes
* Major software deployment
* Cloud configuration changes
* Authentication changes
* Security-policy changes

Changes should include:

* Business reason
* Technical description
* Risk assessment
* Implementation steps
* Testing procedure
* Rollback plan
* Validation results

---

# 22. System Availability

Stoneleaf Systems relies on technology for daily operations.

Important services should be designed to minimize avoidable downtime.

Critical services include:

* Authentication
* DNS
* DHCP
* Internet access
* File services
* Cloud services
* Remote access

IT must be able to identify and respond to service failures.

---

# 23. Monitoring

Stoneleaf Systems requires visibility into infrastructure health.

IT should eventually be able to monitor:

* Server availability
* Network availability
* Resource utilization
* Service status
* Security events
* System failures
* Backup status

Monitoring should help identify problems before they significantly affect users.

---

# 24. Centralized Logging

Important systems should generate logs that can be reviewed during troubleshooting and security investigations.

Logging requirements may include:

* Authentication events
* Server events
* Firewall events
* Endpoint events
* Administrative activity
* Security alerts
* Application events

Logs should be retained appropriately for troubleshooting and analysis.

---

# 25. Patch Management

Stoneleaf Systems must reduce the risk of unsupported or vulnerable systems.

IT must maintain processes for:

* Operating system updates
* Security patches
* Application updates
* Server updates
* Endpoint updates
* Maintenance windows
* Testing where appropriate
* Update verification

Failed updates should be documented and investigated.

---

# 26. Backup

Important business data and system configurations must be protected against loss.

Backup requirements include:

* Regular backups
* Defined backup schedules
* Backup verification
* Protected backup storage
* Recovery testing
* Documentation

A backup is not considered reliable unless recovery can be validated.

---

# 27. Disaster Recovery

Stoneleaf Systems must be able to recover from significant system failures.

Potential scenarios include:

* Server failure
* Storage failure
* Accidental deletion
* Configuration error
* Malware
* Network outage
* Cloud-service failure

Recovery procedures should prioritize critical services and business data.

---

# 28. Documentation

The IT environment must be documented well enough that configurations, procedures, and troubleshooting can be understood later.

Required documentation may include:

* Network diagrams
* IP addressing
* Device inventories
* Server configurations
* User procedures
* Administrative procedures
* Troubleshooting records
* Change records
* Security configurations
* Backup procedures
* Recovery procedures

Documentation must be updated when significant changes occur.

---

# 29. Automation

Stoneleaf Systems should automate repetitive IT tasks when practical.

Potential automation targets include:

* User creation
* User disabling
* Group membership
* System reporting
* Software deployment
* Configuration checks
* Account audits
* Backup verification
* Log collection

Automation should improve consistency and reduce repetitive manual work.

---

# 30. Scalability

The environment must support organizational growth.

The initial design supports approximately **40 employees**, but it should allow expansion without requiring a complete redesign.

Growth may include:

* Additional employees
* Additional departments
* More workstations
* More servers
* Additional network segments
* Additional cloud resources
* New business applications
* Additional office locations

---

# 31. Cost Awareness

Stoneleaf Systems is a small-to-medium-sized organization and must use technology efficiently.

IT solutions should balance:

* Business value
* Reliability
* Security
* Performance
* Manageability
* Cost

Cloud services should be deployed deliberately to prevent unnecessary spending.

---

# 32. Troubleshooting Capability

The IT department must be capable of diagnosing and resolving common infrastructure problems.

Troubleshooting should include:

* Identifying symptoms
* Gathering information
* Testing likely causes
* Reviewing logs
* Isolating faults
* Implementing corrective action
* Validating the solution
* Documenting the resolution

Troubleshooting evidence will be retained as part of the portfolio.

---

# Business Requirement Summary

| ID    | Business Requirement                     |
| ----- | ---------------------------------------- |
| BR-01 | Centralized user and identity management |
| BR-02 | Role-based access control                |
| BR-03 | Standardized onboarding and offboarding  |
| BR-04 | Centrally managed employee workstations  |
| BR-05 | Reliable server infrastructure           |
| BR-06 | Reliable wired and wireless networking   |
| BR-07 | Secure network segmentation              |
| BR-08 | Reliable internet connectivity           |
| BR-09 | Secure remote work capabilities          |
| BR-10 | Centralized file storage and sharing     |
| BR-11 | Protection of Finance information        |
| BR-12 | Protection of HR information             |
| BR-13 | Microsoft Azure cloud capabilities       |
| BR-14 | Email and collaboration services         |
| BR-15 | Integrated security controls             |
| BR-16 | Separation of privileged accounts        |
| BR-17 | Help desk and ticket management          |
| BR-18 | Formal change management                 |
| BR-19 | Availability of critical IT services     |
| BR-20 | Infrastructure monitoring                |
| BR-21 | Centralized logging                      |
| BR-22 | Patch management                         |
| BR-23 | Backup and recovery                      |
| BR-24 | Disaster-recovery capability             |
| BR-25 | Professional technical documentation     |
| BR-26 | Administrative automation                |
| BR-27 | Infrastructure scalability               |
| BR-28 | Cost-conscious IT design                 |
| BR-29 | Structured troubleshooting practices     |

---

## Document Status

**Organization:** Stoneleaf Systems

**Employee Count:** 40

**Infrastructure Model:** Hybrid

**Current Phase:** `00-Foundation`

**Current Document:** `Business-Requirements.md`

**Next Document:** `Technical-Requirements.md`

