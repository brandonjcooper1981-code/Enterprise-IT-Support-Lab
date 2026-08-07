# Group Design

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Architecture Design Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the Active Directory group design implemented within the Northwind Technologies environment. The design standardizes security group creation, permission assignment, delegated administration, and access management using Microsoft's recommended Active Directory best practices.


---

## Environment Note

**Note**

The current implementation environment uses the **lab.local** Active Directory domain. References to **northwind.local** throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Design Goals

The Group Design structure has been designed to:

- Centralize permission management.
- Implement Role-Based Access Control (RBAC).
- Support the AGDLP methodology.
- Simplify onboarding and offboarding.
- Reduce administrative overhead.
- Enforce least privilege.
- Improve scalability.

---

## Enterprise Group Strategy

Northwind Technologies uses Active Directory Security Groups to simplify permission management, reduce administrative overhead, and implement Role-Based Access Control (RBAC). Access permissions are assigned to groups rather than individual user accounts whenever possible.

Objectives:
- Centralized permission management
- Least privilege
- Role-Based Access Control
- Simplified onboarding
- Simplified offboarding
- Reduced administrative effort

---

## Groups Types

| Group Type | Purpose |
|------------|----------|
| Security | Permissions and access control |
| Distribution | Email distribution lists |
| Administrative | Elevated administrative access |

Although Active Directory supports multiple group types, Northwind Technologies primarily uses Security Groups for resource permissions and Role-Based Access Control (RBAC). Distribution Groups are reserved for future Microsoft Exchange or Microsoft 365 email integration.

---

## Group Scope

| Scope | Purpose |
|---------|----------|
| Global | Department users |
| Domain Local | Resource permissions |
| Universal | Multi-domain environments (future use) |

- Northwind Technologies currently operates as a single-domain forest.
- Global Groups contain users.
- Domain Local Groups receive permissions.
- Universal Groups are reserved for future multi-domain expansion.

---

## Naming Standards

| Object | Example |
|---------|----------|
| Security Group | SG-IT-Users |
| Administrative Group | SG-IT-Admins |
| File Share Group | SG-HR-Shared-RW |
| Printer Group | SG-Marketing-Printer |
| VPN Group | SG-VPN-Users |

Naming convention:
SG-<Department>-<Purpose>

Examples:
SG-IT-Users

SG-HR-Users

SG-Finance-Users

SG-Executive-Users

SG-IT-Admins

---

## Department Security Groups

| Department | Security Group |
|-------------|----------------|
| HR | SG-HR-Users |
| Finance | SG-Finance-Users |
| IT | SG-IT-Users |
| Engineering | SG-Engineering-Users |
| Marketing | SG-Marketing-Users |
| Operations | SG-Operations-Users |
| Sales | SG-Sales-Users |
| Executive | SG-Executive-Users |

---

## Administrative Groups

| Group | Purpose |
|---------|----------|
| Domain Admins | Full AD Administration |
| Enterprise Admins | Forest Administration |
| Help Desk | Password resets |
| Server Admins | Server Management |
| Backup Operators | Backup Operations |

---

## AGDLP Methodology

Accounts
   ↓
Global Security Groups
   ↓
Domain Local Resource Groups
   ↓
Permissions

Example:
bjcooper
↓
SG-IT-Users
↓
DL-IT-Shared-RW
↓
\\FS01\IT

---

## Group Membership Standards

- Users belong only to the groups required for their role.
- Administrative access uses separate administrative groups.
- Group nesting follows Microsoft's AGDLP model.
- Individual permissions are avoided whenever possible.
- Department managers approve membership requests.
- Membership changes are documented.

---

## Delegated Administration

| Role | Responsibilities |
|------|-------------------|
| Domain Admin | AD Administration |
| Help Desk | Password resets |
| Department Manager | Membership approval |
| Standard User | No administrative rights |

---

## Permission Assignment Strategy

Northwind Technologies assigns permissions using Security Groups instead of user accounts.

Resources include:
- File Shares
- Shared Folders
- Network Drives
- Printers
- Applications
- GPO Security Filtering

---

## Lifecycle Management

Group memberships are reviewed whenever an employee joins, transfers departments, changes job roles, or leaves the organization.

New Employee:
- Create user
- Add department group
- Add resource groups
- Verify access

Employee Transfer:
- Remove old groups
- Add new groups
- Validate permissions

Employee Departure:
- Disable account
- Remove memberships
- Archive mailbox
- Delete account after retention period

---

## Validation

- Security Groups created.
- Naming standards followed.
- AGDLP implemented.
- Permissions inherited correctly.
- Users receive proper access.
- Least privilege maintained.
- Administrative groups protected.
- Nested group memberships validated.

---

## Useful Commands

```powershell
Get-ADGroup -Filter *
```

```powershell
Get-ADGroupMember "SG-IT-Users"
```

```powershell
Get-ADPrincipalGroupMembership bjcooper
```

```powershell
New-ADGroup
```

```powershell
Add-ADGroupMember
```

```powershell
Remove-ADGroupMember
```

```powershell
Get-ADGroup -Identity "SG-IT-Users" -Properties *
```

```powershell
Get-ADGroupMember "SG-IT-Users" -Recursive
```

---

## Related Documentation

- Active-Directory-Design.md
- OU-Design.md
- User-Standards.md
- User-Creation-Procedure.md
- Group-Standards.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md
- Drive-Mapping-GPO.md
- Desktop-Configuration-GPO.md

---

## Approval

**Approved By**

Michael Wilson

Chief Information Officer (CIO)

**Prepared By**

Brandon J. Cooper

**Department**

Information Technology Services (ITS)

---

## Revision History

| Version | Date | Author | Description |
|----------|----------|----------|----------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial release |

---

**Questions or Updates?**

Please submit documentation corrections through the Northwind Technologies Information Technology Services documentation review process.

---

____________________________________

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Innovate • Secure • Support

© 2026 Northwind Technologies
