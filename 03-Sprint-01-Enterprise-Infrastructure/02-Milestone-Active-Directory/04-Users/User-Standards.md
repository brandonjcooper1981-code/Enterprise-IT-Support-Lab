# User Standards

| Property      | Value                                 |
| ------------- | ------------------------------------- |
| Company       | Northwind Technologies                |
| Department    | Information Technology Services (ITS) |
| Document Type | Standards Document                    |
| Status        | Active                                |
| Version       | 1.0                                   |

---

## Purpose

This document defines the standards used to create, manage, and maintain Active Directory user accounts within the Northwind Technologies environment.

These standards provide consistency, improve security, and simplify administration across all departments.

---

## Environment Note
- Note
  - The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## User Naming Standards

### Username Format

Northwind Technologies uses the following username convention:
- [first initial][lastname]

Examples:
| Employee Name  | Username  |
| -------------- | --------- |
| Brandon Cooper | bjcooper  |
| John Smith     | jsmith    |
| Sarah Johnson  | sjohnson  |
| Michael Wilson | mwilson   |

---

### Display Name Standard

Display names follow the format:
- FirstName LastName

Examples:
- Brandon J. Cooper
- Sarah Johnson
- Michael Wilson

---

### Email Address Standard

Corporate email addresses follow:
- username@northwind.local

Examples:
- bjcooper@northwind.local
- jsmith@northwind.local
- sjohnson@northwind.local

---

## Department Assignment

All users must be assigned to the appropriate department OU.

| Department             | Organizational Unit |
| ---------------------- | ------------------- |
| Human Resources        | HR                  |
| Finance                | Finance             |
| Information Technology | IT                  |
| Engineering            | Engineering         |
| Marketing              | Marketing           |
| Operations             | Operations          |
| Sales                  | Sales               |
| Executive              | Executive           |
| Help Desk Training     | HelpDesk-Lab        |

---

## Account Lifecycle

### Account Creation

New accounts require:
- First and last name.
- Department assignment.
- Security group membership.
- Manager approval.
- Temporary password.

### Account Changes

The following changes must be documented:
- Name changes.
- Department transfers.
- Permission updates.
- Group membership changes.

### Account Disablement

Accounts must be disabled when:
- Employment ends.
- Extended leave occurs.
- Security concerns exist.

### Account Deletion

Disabled accounts are reviewed before permanent removal.

### Account States

User accounts may exist in one of the following states:
- Active
- Disabled
- Locked Out
- Pending Removal

---

## Password Standards

### Temporary Password Requirements

Temporary passwords must:
- Contain uppercase letters.
- Contain lowercase letters.
- Include numbers.
- Include special characters.
- Meet domain complexity requirements.

Example:
- TempPassword123!

### Password Policies

- Minimum length: 12 characters.
- Password history enabled.
- Complexity requirements enabled.
- Users must change passwords at first login.
- Shared accounts are prohibited.
- Maximum password age: 90 days.
- Minimum password age: 1 day.
- Account lockout threshold: 5 failed attempts.

---

## Security Principles

Northwind Technologies follows these principles:
- Least privilege access.
- Separation of duties.
- Department-based permissions.
- Group-based access management.
- Regular access reviews.

---

## User Attributes

Each account should include:
- Full name
- Username
- Department
- Job title
- Email address
- Manager
- Office location
- Telephone number

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- OU-Design.md
- Implementation-Steps.md

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
