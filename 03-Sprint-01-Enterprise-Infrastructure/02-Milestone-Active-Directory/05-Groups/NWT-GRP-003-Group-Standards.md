# Group Standards

| Property      | Value                                 |
| ------------- | ------------------------------------- |
| Company       | Northwind Technologies                |
| Department    | Information Technology Services (ITS) |
| Document Type | Standards Document                    |
| Status        | In Progress                           |
| Version       | 1.0                                   |

---

## Purpose

This document defines the standards used to create, manage, and maintain Active Directory security groups within the Northwind Technologies environment.

These standards ensure consistent permission assignment, simplify administration, and support the principle of least privilege.

---

## Environment Note

Note: The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Group Naming Standards

### Security Group Format

Northwind Technologies uses the following naming convention for security groups:
SG-<Department>-<Purpose>

Examples:
| Group Name           | Purpose                  |
| -------------------- | ------------------------ |
| SG-HR-Users          | Human Resources access   |
| SG-Finance-Users     | Finance access           |
| SG-IT-Admins         | IT administrative access |
| SG-Engineering-Users | Engineering access       |
| SG-Marketing-Users   | Marketing access         |
| SG-Operations-Users  | Operations access        |
| SG-Sales-Users       | Sales access             |

### Distribution Group Format

Email distribution groups follow:
DL-<Department>

Examples:
| Group Name      | Purpose                      |
| --------------- | ---------------------------- |
| DL-HR           | Human Resources mailing list |
| DL-Finance      | Finance mailing list         |
| DL-AllEmployees | Company-wide communication   |

### Distribution Group Implementation Status

Distribution groups are included as part of the Northwind Technologies enterprise design standard but are not currently implemented in the lab.local environment.

Future phases may integrate:
- Microsoft 365
- Exchange Online
- Hybrid email services

### Group Categories

| Category              | Description                  |
| --------------------- | ---------------------------- |
| Security Groups       | Control access to resources  |
| Distribution Groups   | Email communication          |
| Administrative Groups | Elevated privileges          |
| Project Groups        | Temporary access assignments |

### Department Group Assignments

| Department             | Standard Security Group |
| ---------------------- | ----------------------- |
| Human Resources        | SG-HR-Users             |
| Finance                | SG-Finance-Users        |
| Information Technology | SG-IT-Users             |
| Engineering            | SG-Engineering-Users    |
| Marketing              | SG-Marketing-Users      |
| Operations             | SG-Operations-Users     |
| Sales                  | SG-Sales-Users          |
| Executive              | SG-Executive-Users      |

---

## Group Lifecycle

### Group Creation

New groups require:
- Business justification.
- Department ownership.
- Manager approval.
- Defined permissions.
- Documentation.

### Group Membership Changes

The following changes must be documented:
- User additions.
- User removals.
- Permission changes.
- Department transfers.
- Temporary access assignments.

### Group Review

Group memberships must be reviewed:
- Quarterly.
- During employee transfers.
- During offboarding.
- Following security incidents.

### Group Deletion

Groups may be removed when:
- The business need no longer exists.
- The project is complete.
- The department is reorganized.
- The group has no members.

---

## Permission Standards

Northwind Technologies follows these principles:
- Apply least-privilege access.
- Assign permissions to groups, not individual users.
- Use nested groups only when required to simplify administration.
- Separate administrative and standard access.
- Remove unused groups promptly.

---

## Administrative Groups

| Group                   | Purpose               |
| ----------------------- | --------------------- |
| SG-IT-Admins            | Server administration |
| SG-HelpDesk-Technicians | User support          |
| SG-Domain-Admins        | Domain administration |
| SG-Security-Operations  | Security monitoring   |
| SG-FileShare-Admins     |                       |
| SG-Server-Operators     |                       |

---

## Security Principles

Northwind Technologies follows these security principles:
- Least privilege.
- Separation of duties.
- Role-based access control.
- Periodic access reviews.
- Documented approvals.

---

## Validation

Verify:
- Groups follow naming standards.
- Memberships are accurate.
- Permissions are assigned correctly.
- Group ownership is documented.
- Unused groups are removed.

---

## Related Documentation
- User-Standards.md
- User-Creation-Procedure.md
- OU-Design.md
- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP

---

## Approval

**Approved By**

Michael Wilson

Chief Information Officer (CIO)

---

**Prepared By**

Brandon J. Cooper

---

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

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Innovate • Secure • Support

© 2026 Northwind Technologies
