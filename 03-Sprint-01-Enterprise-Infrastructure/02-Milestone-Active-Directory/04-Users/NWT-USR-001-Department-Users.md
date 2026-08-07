# NWT-USR-001-Department Users

# Department Users

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Active Directory User Inventory |
| Document Number | NWT-USR-001 |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides the official inventory of Active Directory user accounts within the Northwind Technologies enterprise environment.

The document identifies departmental users, job roles, organizational unit placement, security group membership, home department, and account purpose. It serves as the primary reference for user administration, access reviews, troubleshooting, and security audits.

---

> [!NOTE]
>
> **Quick Facts**
>
> • Total Departments: 7
>
> • Total Active Users: 7
>
> • Administrative Accounts: 2
>
> • Disabled Accounts: 0
>
> • Service Accounts: 0
>
> • Domain: lab.local

---

## Scope

This document includes:

- Employee user accounts
- Administrative accounts
- Service accounts (where applicable)
- Department assignments
- Organizational Unit placement
- Security group membership
- Account status

---

## Environment Note

The current implementation environment uses the **lab.local** Active Directory domain.

Future enterprise deployments will use the planned **northwind.local** naming standard.

---

## User Naming Standards

Northwind Technologies follows standardized naming conventions for all Active Directory users.

| Item | Standard |
|------|----------|
| Username | firstname.lastname |
| Display Name | Firstname Lastname |
| Email | firstname.lastname@northwind.local |
| UPN | firstname.lastname@lab.local |
| Password Policy | NWT-GPO-001 |

---

## Organizational Structure

Departments currently implemented:

- Executive
- Human Resources
- Finance
- Information Technology
- Sales
- Marketing
- Operations

---

## Northwind Employee ID Standard

| Employee ID | Department | Employee |
|-------------|------------|----------|
| EMP-0001 | IT | Brandon Cooper |
| EMP-0002 | IT | John Carter |
| EMP-0003 | HR | Sarah Adams |
| EMP-0004 | Finance | Emily Brown |
| EMP-0005 | Sales | Michael Davis |
| EMP-0006 | Marketing | Olivia Wilson |
| EMP-0007 | Operations | James Miller |

---

## Department User Inventory

## Department User Inventory

| Employee ID | Employee | Username | Job Title | Department | OU | Account Type | Manager | Status |
|-------------|----------|----------|-----------|------------|----|--------------|---------|--------|
| EMP-0001 | Brandon Cooper | brandon.cooper | Systems Administrator | IT | IT | Standard | Self | Active |
| EMP-0002 | John Carter | john.carter | Help Desk Technician | IT | IT | Standard | Brandon Cooper | Active |
| EMP-0003 | Sarah Adams | sarah.adams | HR Manager | Human Resources | HR | Standard | Executive | Active |
| EMP-0004 | Emily Brown | emily.brown | Accountant | Finance | Finance | Standard | Finance Manager | Active |
| EMP-0005 | Michael Davis | michael.davis | Sales Representative | Sales | Sales | Standard | Sales Manager | Active |
| EMP-0006 | Olivia Wilson | olivia.wilson | Marketing Specialist | Marketing | Marketing | Standard | Marketing Manager | Active |
| EMP-0007 | James Miller | james.miller | Operations Manager | Operations | Operations | Standard | Executive | Active |

---

## Administrative Accounts

| Employee ID | Account | Username | Purpose | Account Type | Privileged | Enabled |
|-------------|----------|----------|----------|--------------|------------|---------|
| ADM-0001 | Domain Administrator | Administrator | Domain Administration | Built-in | Yes | Yes |
| ADM-0002 | Brandon Cooper | brandon.admin | Administrative Account | Privileged | Yes | Yes |

---

## Deaprtment Breakdown

### Information Technology

Manager:
- Brandon Cooper

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| Brandon Cooper | brandon.cooper | Systems Administrator | IT Admins |
| John Carter | john.carter | Help Desk | Help Desk |

### Human Resources

Manager:
- Sarah Adams

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| Sarah Adams | sarah.adams | HR Manager | HR |

### Finance

Manager:
- Pending Assignment

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| Emily Brown | emily.brown | Accountant | Finance |

### Sales

Manager:
- Pending Assignment

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| Michael Davis | michael.davis | Sales Representative | Sales |

### Marketing

Manager:
- Pending Assignment

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| Olivia Wilson | olivia.wilson | Marketing Specialist | Marketing |

### Operations

Manager:
- James Miller

Users:

| Name | Username | Job Title | Groups |
|------|----------|-----------|--------|
| James Millers | james.miller | Operations Manager | Operations |

---

## Group Membership Summary

| Security Group | Purpose | Members |
|---------------|---------|---------|
| IT Admins | Infrastructure Administration | Brandon Cooper |
| HR Users | HR Resources | Sarah Adams |
| Finance Users | Finance Resources | Emily Brown |
| Sales Users | Sales Resources | Michael Davis |
| Marketing Users | Marketing Resources | Olivia Wilson |
| Operations Users | Operations Resources | James Miller |

---

## Administrative Accounts

| Account | Purpose | Used By | Privileged | Enabled |
|----------|----------|-------|-----------|---------|
| Administrator | Domain Administration | Domain | Yes | Yes |
| Brandon.Admin | Administrative Account | Brandon Cooper | Yes | Yes |

---

## Disabled Accounts

| Username | Reason | Date |
|----------|--------|------|
| None | N/A | N/A |

---

## Account Lifecycle

User Request
      │
      ▼
Manager Approval
      │
      ▼
Account Created
      │
      ▼
Added to OU
      │
      ▼
Added to Security Groups
      │
      ▼
Initial Password Assigned
      │
      ▼
User Validation
      │
      ▼
Active Account

---

## Related Documentation

- NWT-USR-002 – User Creation Procedure
- NWT-USR-003 – User Standards
- NWT-GRP-001 – Group Creation Procedure
- NWT-GRP-002 – Group Membership Procedure
- NWT-OU-001 – Department OU Design
- NWT-GPO-001 – Password Policy
- NWT-OPS-001 – Active Directory Commands

---

## Best Practices

- Assign users to security groups rather than directly to resources.
- Follow standardized naming conventions.
- Apply least privilege.
- Disable unused accounts promptly.
- Review group memberships regularly.
- Separate administrative and standard user accounts.

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
|----------|------|--------|-------------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial Release |

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
