# Departmental OU Design

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Design Document |
| Status | In Progress |
| Version | 1.0 |

---

## Purpose

This document defines the departmental Organizational Units (OUs) within the Northwind Technologies Active Directory environment.

Departmental OUs provide administrative separation, targeted Group Policy deployment, and support for future growth.

---

## Environment Note

> **Note**
>
> The current implementation environment uses the `lab.local`
> Active Directory domain. References to `northwind.local`
> throughout the Northwind Technologies documentation represent
> the planned enterprise naming standard and future production
> environment.

---

## Human Resources OU

### Purpose

The Human Resources OU contains users, computers, security groups, and policies related to Human Resources operations.

### Planned Resources

- HR user accounts
- HR security groups
- Department printers
- Shared folders
- HR-specific Group Policy Objects

---

## Finance OU

### Purpose

The Finance OU contains users, computers, security groups, and policies related to financial operations.

### Planned Resources

- Finance user accounts
- Finance security groups
- Department printers
- Shared folders
- Finance-specific Group Policy Objects

---

## Information Technology OU

### Purpose

The Information Technology OU contains administrative accounts, support workstations, and infrastructure management resources.

### Planned Resources

| Resource | Status |
|----------|----------|
| User accounts | Planned |
| Security groups | Planned |
| Department printers | Future |
| Shared folders | Planned |
| Department GPOs | Planned |

---

## Current Implementation Status

| OU | Implemented |
|-----|-----|
| Engineering | Yes |
| Executive | Yes |
| Finance | Yes |
| HR | Yes |
| IT | Yes |
| Marketing | Yes |
| Operations | Yes |
| Sales | Yes |
| HelpDesk-Lab | Yes |

---

## Design Considerations

- Apply least-privilege access.
- Isolate departmental policies.
- Support delegated administration.
- Simplify future expansion.
- Minimize cross-department dependencies.

---

## Current Departmental Organizational Units

The following departmental OUs are currently deployed:
- Engineering
- Executive
- Finance
- HR
- IT
- Marketing
- Operations
- Sales
- HelpDesk-Lab

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- Milestone-02-Overview.md

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
