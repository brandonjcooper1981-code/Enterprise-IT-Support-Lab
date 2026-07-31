# Organizational Unit (OU) Design

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Architecture Design Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the Organizational Unit (OU) structure implemented within the Northwind Technologies Active Directory environment.

The Organizational Unit design provides a logical hierarchy for users, computers, security groups, and Group Policy Objects (GPOs). The structure simplifies administration, supports delegated management, improves security, and allows the Active Directory environment to scale as the organization grows.

---

## Environment Note

**Note**

The current implementation environment uses the **lab.local** Active Directory domain. References to **northwind.local** throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Design Goals

The Organizational Unit structure has been designed to:

- Simplify Active Directory administration.
- Separate departments logically.
- Support delegated administration.
- Apply Group Policy efficiently.
- Reduce administrative overhead.
- Support future organizational growth.
- Follow Microsoft Active Directory best practices.

---

## Organizational Structure

Forest
│
└── lab.local
    │
    ├── Domain Controllers
    ├── HR
    ├── Finance
    ├── IT
    ├── Engineering
    ├── Marketing
    ├── Operations
    ├── Sales
    └── Executive

---

## Department Organizational Units

| OU | Purpose | Typical Objects |
|----|----------|----------------|
| HR | Human Resources | Users, Computers, Groups |
| Finance | Accounting | Users, Computers, Groups |
| IT | Information Technology | Admin accounts, Help Desk, Workstations |
| Engineering | Engineering Staff | Users and Devices |
| Marketing | Marketing Team | Users and Devices |
| Operations | Operations Staff | Users and Devices |
| Sales | Sales Department | Users and Devices |
| Executive | Executive Leadership | Executive accounts and devices |

## OU Design Principles

Northwind Technologies follows several Active Directory design principles:

- Separate departments into individual Organizational Units.
- Apply Group Policy at the lowest practical level.
- Delegate administration when appropriate.
- Avoid unnecessary nested OUs.
- Separate administrative accounts from standard users whenever possible.
- Maintain consistent naming conventions across the environment.

---

## Group Policy Strategy

Group Policy Objects are linked to Organizational Units rather than individual users whenever possible.  Whenever possible, GPOs are linked directly to Organizational Units instead of the domain to reduce policy scope, simplify troubleshooting, and minimize unintended policy inheritance.

Examples include:

- Password Policy
- Desktop Configuration
- Desktop Lock
- Drive Mapping
- Software Deployment
- Security Baselines

---

## Security Considerations

The Organizational Unit design supports the following security principles:

- Least Privilege
- Role-Based Access Control (RBAC)
- Centralized Policy Management
- Security Group Based Permissions
- Departmental Administrative Isolation
- Administrative Separation

---

## Naming Standards

| Object | Example |
|---------|----------|
| Domain | lab.local |
| OU | IT |
| User | bjcooper |
| Computer | CLIENT01 |
| Server | DC01 |
| Security Group | SG-IT-Users |
| GPO | GPO-IT-Desktop-Configuration |
| Shared Folder | IT-Shared |

---

## Furture Expansion

The OU structure has been designed to support future growth.

Possible future additions include:

- Child Organizational Units
- Service Accounts OU
- Servers OU
- Computers OU
- Workstations OU
- Disabled Accounts OU
- Administrative Accounts OU
- Remote Offices
- Multiple Sites
- Hybrid Microsoft Entra ID integration

---

## Validation

Verify:
- Organizational Units exist.
- Naming standards are followed.
- Group Policy links correctly.
- Delegation functions properly.
- Users and computers reside in the proper OU.
- Security groups align with departmental structure.

---

## Useful Commands

```powershell
Get-ADOrganizationalUnit -Filter *
```

```powershell
Get-ADOrganizationalUnit -Filter * | Select Name
```

```powershell
Get-ADObject -SearchBase "OU=IT,DC=lab,DC=local" -Filter *
```

```powershell
Get-GPInheritance -Target "OU=IT,DC=lab,DC=local"
```

---

## Related Documentation
- Active-Directory-Design.md
- User-Standards.md
- Group-Standards.md
- GPO-Standards.md
- User-Creation-Procedure.md
- Group-Creation-Procedure.md
- Desktop-Configuration-GPO.md
- Department-OU-Design.md

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

---

