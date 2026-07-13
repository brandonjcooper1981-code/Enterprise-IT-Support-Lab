# OU Structure

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Design Document |
| Status | In Progress |
| Version | 1.0 |

---

## Purpose

This document defines the Active Directory Organizational Unit (OU) structure used within the Northwind Technologies environment.

The OU hierarchy provides centralized administration, delegated management, Group Policy targeting, and scalability for future enterprise growth.

---

## Design Goals

- Organize users and computers logically.
- Separate administrative responsibilities.
- Support Group Policy deployment.
- Simplify permissions management.
- Improve scalability.
- Align IT infrastructure with business operations.

---

## OU Hierarchy

```text
lab.local
│
├── Engineering
├── Executive
├── Finance
├── HelpDesk-Lab
├── HR
├── IT
├── Marketing
├── Operations
├── Sales
├── Servers
└── Workstations
```

> Note:
>
> The current implementation uses the `lab.local` domain for training and validation purposes. Future enterprise deployments may use a production naming standard aligned with Northwind Technologies.
>
---

## Administrative Model

| OU | Purpose |
|---|---|
| Engineering | Engineering users and resources |
| Executive | Executive leadership accounts |
| Finance | Financial systems and users |
| HelpDesk-Lab | Training and testing environment |
| HR | Human Resources staff and policies |
| IT | IT administration and support |
| Marketing | Marketing department resources |
| Operations | Operational staff and systems |
| Sales | Sales users and applications |
| Servers | Server objects |
| Workstations | Client computers |

---

## Design Principles

- Apply least privilege.
- Separate users and devices.
- Organize by business function.
- Support delegated administration.
- Simplify Group Policy management.

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP

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
