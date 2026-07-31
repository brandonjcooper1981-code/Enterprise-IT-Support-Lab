# Active Directory Design

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Architecture Design Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose
This document defines the Active Directory architecture implemented within the Northwind Technologies enterprise environment.
The design establishes a secure, scalable, and manageable directory services infrastructure supporting user authentication, authorization, centralized management, Group Policy administration, and future organizational growth.

---

## Environment Note
Note
    The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Design Goals

The Active Directory environment has been designed to:
- Centralize identity management.
- Simplify workstation administration.
- Enforce enterprise security standards.
- Support delegated administration.
- Minimize administrative overhead.
- Provide scalability for future departments.
- Support regulatory compliance.

---

## Enterprise Overview

Northwind Technologies
        │
        ▼
Active Directory Forest
        │
        ▼
Forest: lab.local
        │
        ▼
Single Domain
        │
        ▼
Departmental OUs
        │
        ▼
Users • Groups • Computers • Group Policy

---

## Active Directory Architecture

Forest
│
└── lab.local
    │
    ├── Domain Controllers
    │
    ├── HR
    ├── Finance
    ├── IT
    ├── Engineering
    ├── Marketing
    ├── Operations
    ├── Sales
    └── Executive

---

## Organizational Unit Design

| OU | Purpose |
|----|----------|
| HR | Human Resources |
| Finance | Accounting |
| IT | IT Administration |
| Engineering | Engineering Staff |
| Marketing | Marketing |
| Operations | Operations |
| Sales | Sales |
| Executive | Executive Leadership |

Detailed information is located in OU-Design.md

---

## User Design

Northwind Technologies organizes user accounts according to departmental Organizational Units (OUs). Every employee receives a unique Active Directory account following the corporate naming convention. User accounts are created using standardized procedures, assigned to security groups based on job role, and managed according to the account lifecycle process. Temporary passwords are issued during account creation and users are required to change their password at first logon. Access permissions are granted using the principle of least privilege.

Reference:
- User-Standards.md
- User-Creation-Procedure.md

---

## Group Design

Northwind Technologies uses Security Groups to assign permissions and simplify administration. Distribution Groups may be used for email communication where appropriate. Administrative Groups are reserved for privileged accounts and are managed by Information Technology Services. Group membership follows the AGDLP methodology to simplify permission management and reduce administrative overhead.

Reference:
- Group-Standards.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md

---

### Group Policy Design

Group Policy provides centralized management for workstation security, password policies, desktop configuration, screen locking, drive mappings, and other enterprise settings. Policies are linked at the most appropriate Organizational Unit and follow the standards defined in the Group Policy documentation.

Reference:
- GPO-Standards.md
- Password-Policy-GPO.md
- Desktop-Lock-GPO.md
- Desktop-Configuration-GPO.md
- Drive-Mapping-GPO.md

---

## Security Model

The Northwind Technologies security model is based on the principle of Least Privilege and Role-Based Access Control (RBAC). Administrative privileges are assigned only when required, password policies are enforced through Group Policy, and access to resources is granted through Security Groups rather than directly to user accounts. Account lockout policies reduce the effectiveness of brute-force attacks while centralized Group Policy ensures consistent security across the enterprise.

---

## Administrative Delegation

| Role | Responsibilities |
|------|-------------------|
| Domain Admins | Full administration |
| Enterprise Admins | Forest administration (future) |
| Help Desk | Password resets, unlocks |
| Department Managers | User requests |
| Standard Users | Daily operations |

---

## Naming Standards

| Object | Example |
|---------|----------|
| User | bjcooper |
| Security Group | SG-IT-Users |
| GPO | GPO-IT-Desktop-Configuration |
| OU | IT |
| Computer | CLIENT01 |
| Server | DC01 |

## Scalability

The Active Directory environment is designed to support future business growth. Additional Organizational Units can be created as new departments are added. Multiple domain controllers may be deployed to improve redundancy and authentication performance. The design also supports future integration with Microsoft Entra ID and hybrid identity services as cloud adoption increases.

---

## Disaster Recovery Considerations

Disaster recovery planning includes regular System State backups of the Domain Controller, Active Directory database backups, integrated DNS backups, and periodic Group Policy backups. Recovery procedures are documented separately to ensure directory services can be restored following hardware failure, accidental deletion, or disaster scenarios.

---

## Validation

Verify:
- Domain operational
- Authentication functional
- DNS operational
- Group Policy functioning
- Users authenticating
- Security groups assigned correctly
- Organizational Unit structure validated

---

## Related Documentation

- OU-Design.md
- User-Standards.md
- User-Creation-Procedure.md
- Group-Standards.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md
- GPO-Standards.md
- Desktop-Configuration-GPO.md
- Desktop-Lock-GPO.md
- Password-Policy-GPO.md

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

