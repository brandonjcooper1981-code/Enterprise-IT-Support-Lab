# NWT-ENT-006 Enterprise Naming Standards

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-006 |
| Document Type | Enterprise Governance Standard |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | June 2026 |

---

## Executive Summary

The Enterprise Naming Standards document establishes standardized naming conventions for all enterprise infrastructure, Active Directory objects, servers, workstations, network resources, documentation, automation, and future cloud services deployed within the Northwind Technologies Enterprise IT Modernization Project.

Consistent naming improves administration, troubleshooting, automation, reporting, security, documentation, and operational efficiency while reducing configuration errors across the enterprise environment.

---

## Purpose

This standard ensures that all enterprise resources follow a predictable and repeatable naming convention throughout their lifecycle.

Benefits include:

Simplified administration
Faster troubleshooting
Improved automation
Consistent documentation
Easier asset management
Reduced configuration errors
Improved scalability

---

## Enterprise Naming Principles

All enterprise resources shall follow these principles:

Consistency
Simplicity
Readability
Predictability
Scalability
Standardization
Documentation First

---

## Enterprise Prefix Standards

| Resource             | Prefix                               |
| -------------------- | ------------------------------------ |
| Domain Controller    | DC                                   |
| File Server          | FILE                                 |
| SQL Server           | SQL                                  |
| Deployment Server    | WDS                                  |
| Update Server        | WSUS                                 |
| Print Server         | PRINT                                |
| Linux Server         | UBUNTU                               |
| Security Server      | WAZUH                                |
| Workstations         | CLIENT                               |
| PowerShell Modules   | PS                                   |
| Scripts              | SCRIPT                               |
| Documentation        | NWT                                  |
| Groups               | SG                                   |
| Organizational Units | OU                                   |
| Users                | First Initial + Last Name            |
| Service Accounts     | SVC                                  |
| Shared Folders       | SHARE                                |

---

## Server Naming Standard

| Server Type       | Example  |
| ----------------- | -------- |
| Domain Controller | DC01     |
| File Server       | FILE01   |
| SQL Server        | SQL01    |
| Deployment Server | WDS01    |
| Update Server     | WSUS01   |
| Print Server      | PRINT01  |
| Ubuntu Server     | UBUNTU01 |
| Wazuh Server      | WAZUH01  |

---

## Workstation Naming

| Device                  | Example      |
| ----------------------- | ------------ |
| Enterprise Client       | CLIENT01     |
| Engineering Workstation | ENG-CLIENT01 |
| Help Desk Workstation   | HD-CLIENT01  |
| Test Machine            | TEST01       |

---

## Active Directory Naming

### Organizational Units

Executive
HR
Finance
Engineering
IT
Marketing
Operations
Sales
Service Accounts
Workstations
Servers
Groups

### Security Groups

Format:
- SG-Department-Permission
Examples:
- SG-HR-Modify
- SG-Engineering-Read
- SG-Finance-Full
- SG-IT-Admins
- SG-HelpDesk

### User Accounts

Format:
- First Initial + Last Name
Examples:
- BCooper
- JSmith
- MJones
- DMiller

### Administrative Accounts

- ADMIN-BCOOPER
- ADMIN-JSMITH

### Service Accounts

- SVC-DNS
- SVC-SQL
- SVC-BACKUP
- SVC-WAZUH

---

## Shared Folder Naming

| Share               | Example     |
| ------------------- | ----------- |
| Department          | HR          |
| Department          | Finance     |
| Department          | Executive   |
| Department          | Engineering |
| Department          | IT          |
| Department          | Sales       |
| Department          | Marketing   |
| Department          | Operations  |
| Public              | Public      |
| Software Repository | Software    |

---

## Group Policy Naming

Format:
- GPO - Department - Function
Examples:
- GPO - HR - Drive Mapping
- GPO - Finance - Desktop
- GPO - Engineering - Security
- GPO - Enterprise - Password Policy
- GPO - Enterprise - Lockout Policy

---

## PowerShell Naming

| Resource       | Example            |
| -------------- | ------------------ |
| Module         | PS-UserManagement  |
| Script         | SCRIPT-CreateUsers |
| Report         | REPORT-ADUsers     |
| Scheduled Task | TASK-DailyBackup   |

---

## Documentation Naming

| Type               | Format      |
| ------------------ | ----------- |
| Enterprise         | NWT-ENT-001 |
| Standard           | NWT-STD-001 |
| Project Management | NWT-PM-001  |
| Engineering Guide  | ENG-001     |
| SOP                | SOP-001     |
| Knowledge Base     | KB-001      |

---

## GitHub Naming Standards

| Resource   | Standard                   |
| ---------- | -------------------------- |
| Repository | lowercase-hyphen-separated |
| Markdown   | PascalCase.md              |
| Images     | descriptive-name.png       |
| Scripts    | Verb-Noun.ps1              |

Examples:
- enterprise-it-support-lab
- Create-Users.ps1
- CompanyProfile.md
- network-diagram.png

---

## IP Naming References

| Resource       | Example         |
| -------------- | --------------- |
| Domain         | NORTHWIND.LOCAL |
| Static Servers | Static          |
| Clients        | DHCP            |
| DNS            | DC01            |
| DHCP           | DC01            |

---

## Future Cloud Naming

| Resource            | Example           |
| ------------------- | ----------------- |
| Microsoft 365 Group | M365-IT           |
| Entra Group         | ENTRA-HR          |
| Intune Device       | INTUNE-CLIENT01   |
| Defender Device     | DEFENDER-CLIENT01 |

---

## Compliance Checklist

| Compliance                     | Status   |
| ------------------------------ | -------- |
| Server Names Standardized      | Verified |
| Workstation Names Standardized | Verified |
| AD Naming Standard             | Verified |
| Documentation Naming           | Verified |
| Repository Naming              | Verified |
| Future Standards Defined       | Complete |

---

## Related Documentation

- ENT-001 Company Profile
- ENT-002 Enterprise Architecture
- ENT-003 Enterprise Network Diagram
- ENT-004 Server Inventory
- ENT-005 IP Address Plan
- ENT-007 Organization Chart
- STD-001 Enterprise Documentation Standard
- STD-003 Enterprise Naming Standard
