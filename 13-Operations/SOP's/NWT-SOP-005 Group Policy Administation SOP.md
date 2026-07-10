# NWT-SOP-005 Group Policy Administration SOP

| Property | Value |
|----------|--------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-005 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain Group Policy Objects (GPOs) throughout the Northwind Technologies environment.

Group Policy provides centralized management of user settings, workstation configuration, security controls, desktop standards, and Active Directory administration.

---

## Purpose

This SOP defines standards and procedures for:

- Group Policy administration
- GPO creation
- GPO linking
- Security filtering
- Organizational Unit (OU) management
- User configuration
- Computer configuration
- Troubleshooting
- Monitoring and health checks
- Backup and recovery
- Security controls

---

## Scope

Applies to:

- Windows Server 2025
- Active Directory
- Organizational Units (OUs)
- Domain Controllers
- Windows 11 workstations
- User accounts
- Security groups
- File shares
- Printers
- Future Microsoft Intune integration

---

## Supported Systems

- DC01
- northwind.local
- Group Policy Management Console (GPMC)
- Active Directory
- Windows 11 clients
- DNS Server
- DHCP Server
- File Services

---

## Administrative Tools

Authorized tools include:

- Group Policy Management Console (GPMC)
- Active Directory Users and Computers
- RSAT Tools
- PowerShell
- Event Viewer
- Command Prompt
- Windows Admin Center (Future)
- Wazuh (Future)

---

## Roles & Responsibilities

| Role | Responsibility |
|--------|--------|
| CIO | Approves GPO standards |
| Infrastructure Lead | GPO administration |
| System Administrator | GPO maintenance |
| Help Desk | Tier 1 troubleshooting |
| Documentation Owner | SOP maintenance |

---

## Group Policy Architecture

Enterprise Group Policy hierarchy:

northwind.local

├── Domain Policies

│   ├── Default Domain Policy

│   ├── Password Policy

│   └── Account Lockout Policy

├── Workstation Policies

│   ├── Desktop Restrictions

│   ├── Screen Saver Policy

│   ├── Mapped Drives

│   └── Printer Deployment

├── Security Policies

│   ├── Firewall

│   ├── Audit Logging

│   └── Defender

├── User Policies

│   ├── Folder Redirection

│   ├── Login Scripts

│   └── Start Menu Configuration

└── Future Policies

    ├── Intune

    ├── Sentinel

    └── Wazuh

---

## Group Policy Processing Order (LSDOU)

Group Policy is processed in the following order:

1. Local Policy
2. Site
3. Domain
4. Organizational Unit (OU)

Rules:

- Policies applied later override earlier settings.
- Child OUs override parent OUs unless inheritance is blocked.
- Enforced policies cannot be overridden.
- Group Policy is refreshed automatically every 90 minutes.

---

## Organizational Unit Structure

northwind.local

├── Servers

│   ├── Domain Controllers

│   └── Infrastructure

├── Workstations

│   ├── IT

│   ├── Finance

│   └── Human Resources

├── Users

│   ├── Administrators

│   ├── Employees

│   └── Service Accounts

└── Groups

    ├── Security Groups

    └── Distribution Groups

---

## Security Filtering

Security filtering determines which users and computers receive a Group Policy Object.

Requirements:

- Use security groups whenever possible.
- Avoid applying policies directly to individual users.
- Document all security filters.
- Review permissions quarterly.

Common Groups:

- HelpDesk
- ITAdmins
- Domain Admins
- Finance Users
- HR Users

---

## Group Policy Administrative Tasks

| Task | Frequency |
|--------|--------|
| Review GPO links | Weekly |
| Review security filtering | Monthly |
| Verify policy application | Monthly |
| Review event logs | Monthly |
| Remove obsolete GPOs | Quarterly |
| Backup GPOs | Quarterly |

---

## PowerShell Administration

Common commands:

```powershell
Get-GPO -All

Get-GPResultantSetOfPolicy -ReportType Html -Path C:\gpresult.html

gpupdate /force

gpresult /r

gpresult /h C:\gpresult.html

Get-GPInheritance

Backup-GPO -All
```

---

## Common Group Policies

### Password Policy

- Minimum length: 12 characters
- Complexity enabled
- Maximum age: 90 days

### Account Lockout

- Threshold: 5 attempts
- Lockout duration: 15 minutes

### Screen Saver Policy

- Timeout: 15 minutes
- Password protected

### Desktop Restrictions

- Disable Control Panel access
- Restrict USB storage (future)

### Drive Mapping

- Shared folders
- Department drives

### Printer Deployment

- Office printers
- Department printers

---

## Troubleshooting Playbooks

### GPO Not Applying

Severity: High
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify workstation network connectivity.
2. Verify workstation is joined to the domain.
3. Run: ```cmd gpupdate /force```
4. Run:```cmd gpresult /h gpresult.html```
5. Verify OU placement.
6. Verify security filtering.
7. Check Group Policy Operational logs.
8. Review Event Viewer.
9. Document ticket.
10. Close request.

### gpupdate Failure

Severity: High
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify worksations network connectivity.
2. Run ```cmd nslookup```.
3. Ping NORTHWIND.LOCAL
4. Run DISM.exe /Online /Cleanup-image /RestoreHealth.
5. Run ```cmd sfc /scannow```.
6. Open C:\Windows\System32\GroupPolicy.
7. Delete or rename Machine folder and registry.pol file.
8. Restart workstation
9. Run ```cmd gpresult /h greport.html```.
10. Open Applications and Service Logs -> Microsoft -> Windows -> GroupPolicy -> Operational.
11. Review Error Events.
12. Document ticket.
13. Close request.

### Login Script Failure

Severity: High
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify worksations network connectivity.
2. Verify user has Read and Execute NTFS permissions as well as Read share permissions Group Policy Scripts Processing.
3. Copy script locally and run it manually.
4. Run ```cmd rsop.msc``` on affected machine.
5. Run ```cmd gpupdate /force```
6. Open Event Viewer
7. Search eventvwr.msc on the user's local workstation.
8. Open Applications and Service Logs -> Microsoft -> Windows -> GroupPolicy -> Operational.
9. Filter b Event ID.
10. Verify Login Script successful.
11. Document Ticket.
12. Close request.

### Mapped Drive Missing

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Run ```cmd net use```
2. Verify mapped drive is not present.
3. Verify network connection.
4. Press Win+R, then type the UNC path directly.
5. Restart workstation.
6. Verify user has access to mapped drive.
7. Document the ticket.
8. Close the request.

### Printer Deployment Failure

Severity: Low
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify client machine is online, on the correct network and printer server is reachable.
2. Ensure Print Spooler service is running.
3. Run ```cmd gpresult /r``` ```cmd gpupdate /force```
4. Modify Group Policy to enable package-awre V3 drivers.
5. Set Point and Print Restrications to bypass the driver warning/elevation prompt.
6. Run ```cmd printui.exe /s```
7. Remove problematic driver.
8. Ensure GPO is linked to the correct Organizational Unit (OU).
9. Run Win+R, enter \\PrintServerName
10. Locate and connect the printer.
11. Allow Windows to download drivers automatically.
12. Verify printer deployment successful.
13. Document ticket.
14. Close request.

### Password Policy Not Enforcing

Severity: Medium
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Determine if the user is changing thier password locally ot through an identitiy provider.
3. Check if thier user account is subject to a Fine-Grained Password Policy (PSO) overriding the Default Domain Policy.
4. Run ```cmd gpupdate /force```
5. Lock and Unlock workstation.
6. If policy remians unenforced, Tier 2 admins should verify GPO inheritance on the Domain Controllers OU.
7. Esure Default Domain Policy has not been blocked by OUs placed higher in the tree.
8. Document ticket.
9. Close request.

### Slow Logon

Severity: High
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Execute full restart to clear cache, RAM and pending updates.
3. Unplug Ethernet cable or disconnect from Wi-Fi, then reconnect to ensure standard Domain Controller reachability.
4. Log in with local administrator account or a secondary doamin account.
5. Apply the group policy to "Show highly detailed status messages".
6. Open Event Viewer.
7. Open Applications and Service Logs -> Microsoft -> Windows -> GroupPolicy -> Operational.
8. Filter for Event Ids 8000-8004.
9. Run ```cmd taskmgr```.
10. Clear profile directory of cached files, temporary data or uneeded large folders.
11. Escalate if Group Policy processing is the primary bottleneck.
12. Document ticket
13. Close request.

### Folder Redirection Failure

Severity: Medium
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Run ```cmd gpupdate /force```
3. Run ```cmd gpresult /r```
4. Run Win+R, open \\ServerName\ShareName.
5. Check Share and NTFS Permissions.
6. Open Event Viewer
7. Open Applications and Service Logs -> Microsoft -> Windows -> GroupPolicy -> Operational.
8. Search for Event ID 502 or Event ID 1000.
9. Confirm GPO settings.
10. Ensure "Grant the user exclusive rights to the folder name" is unchecked if the files fail to sync.
11. Document ticket.
12. Close request.

---

## Monitoring & Health Checks

Verify:

- Group Policy Management Console (GPMC) health
- SYSVOL replication
- Policy processing times
- Event Viewer logs
- Security filtering
- OU inheritance
- WMI filters
- Login scripts
- Folder redirection
- Drive mappings
- Printer deployment

Recommended checks:

- Run: ```cmd gpresult /r```
- Review: Applications and Services Logs -> Microsoft -> Windows -> GroupPolicy -> Operational
- Verify SYSVOL replication: ```powershell repadmin /replsummary```

---

## Group Policy Workflow

Request Received
↓
Review Requirement
↓
Determine Scope
↓
Create or Modify GPO
↓
Apply Security Filtering
↓
Link to OU
↓
Test in Validation Environment
↓
Run gpupdate /force
↓
Verify Results
↓
Document Changes
↓
Close Request

---

## Backup Requirements

Before modifying Group Policy:

- Verify snapshot exists.
- Export existing GPOs.
- Document rollback procedures.
- Test policy changes in a lab environment.
- Obtain change approval.

Backup commands: ```powershell Backup-GPO -All -Path C:\GPOBackups Get-GPO -All```

Restore commands: ```powershell Restore-GPO```

---

## Future Improvements

- Microsoft Intune integration
- Microsoft Sentinel integration
- Wazuh monitoring
- WMI filtering
- Loopback processing
- Advanced auditing
- BitLocker management
- Windows Update policies
- Conditional access policies
- Azure Active Directory integration

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
- NWT-SOP-001 Active Directory Administration SOP

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
