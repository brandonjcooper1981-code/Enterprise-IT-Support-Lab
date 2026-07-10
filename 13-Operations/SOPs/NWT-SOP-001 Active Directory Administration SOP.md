# NWT-SOP-001 Active Directory Administration

| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-001 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

The Active Directory Administration Standard Operating Procedure establishes the standardized processes used by Information Technology Services (ITS) to administer, maintain, monitor, and secure the Northwind Technologies Active Directory environment. This SOP provides consistent procedures for user administration, group management, organizational unit maintenance, Group Policy administration, password management, and directory services supporting the Enterprise IT Modernization Project.

---

## Scope

Applies To
  • Windows Server 2025
  • Active Directory Domain Services
  • DNS
  • DHCP
  • Group Policy
  • Security Groups
  • Organizational Units
  • Shared Resources

---

## Prerequisites

Before performing Active Directory administrative tasks, administrators must:

  - Use a designated administrative account (ADMIN-<username>).
  - Log on from an approved administrative workstation or server.
  - Ensure the requested change has been authorized.
  - Verify a current backup or VirtualBox snapshot exists for high-risk changes.
  - Follow NWT-STD-005 Enterprise Change Management Standard for changes affecting production services.

---

## Administrative Tools

Authorized administration tools include:
  - Active Directory Users and Computers
  - Active Directory Administrative Center
  - Group Policy Management
  - DNS Manager
  - DHCP Manager
  - Windows Admin Center (Future)
  - PowerShell
  - RSAT
  - Event Viewer
  - Computer Management

---

## Roles & Responsibilities

| Role                 | Responsibility               |
| -------------------- | ---------------------------- |
| CIO                  | Approves directory standards |
| Infrastructure Lead  | Directory administration     |
| Help Desk            | User administration          |
| System Administrator | Server maintenance           |
| Documentation Owner  | Documentation updates        |

---

## Administrative Account Standards

Administrative account names as followed:

Standard User:
  - <username>
Administrative User
  - ADMIN-<username>
Service accounts:
  - SVC-<service>
Groups:
  - GG-Daprtment-Role
  - DL-Department
Requirements
  - Least Privilege
Separate Credentials
  - MFA (Future)
  - Administrative Logon Only
  - Password Policy Compliance

---

## Daily Administration Tasks

| Task                    | Frequency      |
| ----------------------- | -------------- |
| Review Event Logs       | Daily          |
| Verify Replication      | Daily (Future) |
| Unlock Accounts         | As Needed      |
| Reset Passwords         | As Needed      |
| Review Group Membership | Weekly         |
| Review OUs              | Weekly         |
| Review GPOs             | Monthly        |

---

## User Account Management

New User:
  - Verify Request
  - Create User
  - Assign OU
  - Assign Groups
  - Set Password
  - Force Password Change
  - Verify Login
  - Document

Disable User:
  - Verify Authorization
  - Disable Account
  - Remove Groups (if required)
  - Archive Home Folder
  - Document
  - Close Ticket

---

## Group Management

Group Types:

### Security Groups
  - Domain Admins
  - ServerAdmins
  - HelpDesk
  - FileAccess
  - PrinterAccess

### Department Groups
  - HR
  - Finance
  - IT
  - Engineering
  - Marketing
  - Sales

Administration Rules:

  - Least Privilege
  - Nested Groups Preferred
  - Document Membership Changes
  - Quarterly Membership Review

---

## Organizational Unit Administration

- Northwind.local
- Users
- Departments
- Servers
- Workstations
- Groups
- Service Accounts
- Administration

---

## Password Management

- Minimum Length
  - 14
- Complexity
  - Enabled
- History
  - 24
- Maximum Age
  - 90 Days
- Lockout
  - 5 Attempts
- Duration
  - 15 Minutes

---

## Group Policy Administration

- Password Policy
- Lockout Policy
- Windows Firewall
- Microsoft Defender
- Windows Update
- Desktop Restrictions
- Mapped Drives
- Audit Policy
- Future
- Software Restriction Policy
- BitLocker
- LAPS

---

## Shared Folder Administration

- Departments
- HR
- Finance
- Engineering
- Operations
- Sales
- Marketing
- IT
- Public
- Software Repository

---

## Administrative Workstations

Active Directory administration shall only be performed from approved administrative systems.

Requirements include:
  - Domain joined workstation
  - Dedicated administrative account
  - Windows Defender enabled
  - Windows Firewall enabled
  - Current Windows Updates
  - PowerShell 7 (future)
  - RSAT Tools Installed
  - Event Viewer available
  - Git access for documentation
  - VirtualBox access for lab infrastructure

Future:
  - Privileged Access Workstations (PAW)
  - Microsoft LAPS
  - MFA

---

## PowerShell Administration

- Approved Scripts
- Version Control
- Git Repository
- Documentation Required
- Code Review
- Execution Policy
- Signed Scripts (Future)

---

## Routine Maintenance

Routine maintenance includes:

Daily
  - Review Event Viewer
  - Verify Authentication
  - Review Failed Logons

Weekly
  - Review Group Membership
  - Review Disabled Accounts
  - Verify DNS

Monthly
  - Review Group Policy
  - Review Security Groups
  - Validate Shared Folder Permissions
  - Review Documentation

Quarterly
  - Administrative Account Review
  - Password Policy Review
  - Disaster Recovery Validation

---

## Approved Administrative Changes

Routine
  - Unlock User
  - Password Reset
  - Add User to Group
Standard
  - Create OU
  - New Security Group
  - New GPO
High Risk
  - Delete OU
  - Modify Domain Policy
  - FSMO Changes
  - Schema Updates

---

## Monitoring & Health Checks

- Domain Controller
- DNS
- DHCP
- Authentication
- Event Viewer
- Disk Space
- Services
- Replication (Future)

---

## Backup Requirements

Before performing high-risk administrative changes:

  - Verify VirtualBox Snapshot
  - Verify Configuration Export
  - Verify Git Repository is Current
  - Validate Documentation
  - Confirm Rollback Procedure

Changes requiring backups include:

  - Active Directory
  - DNS
  - DHCP
  - Group Policy
  - Organizational Units
  - Security Groups

---

## Emergency Procedures

For emergency administrative changes:

- Notify Infrastructure Lead
- Create Emergency Change Record
- Backup if possible
- Implement Change
- Validate Services
- Update Documentation
- Perform Post-Implementation Review

---

## Audit Requirements

Administrative actions shall be logged and reviewed.

Review includes:

- User Creation
- User Deletion
- Group Membership Changes
- GPO Modifications
- OU Changes
- Administrative Logons
- Failed Administrative Attempts

Retention:
- Event Logs
- Documentation
- Change Records

---

## Security Requirements

All Active Directory administration shall follow the Enterprise Security Baseline.

Requirements include:

- Least Privilege
- Administrative Separation
- RBAC
- Password Policy Compliance
- Account Lockout Policy
- Secure Authentication
- Administrative Logging
- Documentation Required

---

## Validation Checklist

| Validation              | Status   |
| ----------------------- | -------- |
| User Creation Tested    | Verified |
| Password Reset Tested   | Verified |
| Group Membership Tested | Verified |
| GPO Applied             | Verified |
| DNS Functional          | Verified |
| DHCP Functional         | Verified |
| Documentation Updated   | Complete |

---

## Active Directory Administration Workflow

Request Received
        │
        ▼
Verify Authorization
        │
        ▼
Perform Change
        │
        ▼
Validate
        │
        ▼
Document
        │
        ▼
Close Request

---

## Future Improvements

- Microsoft LAPS
- Microsoft Entra ID
- Azure AD Connect
- Self-Service Password Reset
- Microsoft Intune
- Conditional Access
- Privileged Identity Management
- PowerShell Automation
- Wazuh Monitoring
- Microsoft Sentinel

---

## Related Documentation

- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-004 Server Inventory
- NWT-ENT-006 Enterprise Naming Standards
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Backup & Recovery Plan
- NWT-ENT-010 Disaster Recovery Plan
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard
- NWT-STD-008 Security Configuration Standard

---

# Approval

**Approved By**

Michael Wilson
Chief Information Officer (CIO)

**Prepared By**

Brandon J. Cooper

**Department**

Information Technology Services (ITS)

---

# Revision History

| Version | Date | Author | Description |
|----------|------|--------|-------------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial release |

---

**Questions or Updates?**

Please submit documentation corrections through the Northwind Technologies Information Technology Services documentation review process.

---

────────────────────────────────────────

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Innovate • Secure • Support

© 2026 Northwind Technologies

────────────────────────────────────────
