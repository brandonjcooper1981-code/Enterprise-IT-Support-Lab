# Group Creation Procedure

| Property      | Value                                 |
| ------------- | ------------------------------------- |
| Company       | Northwind Technologies                |
| Department    | Information Technology Services (ITS) |
| Document Type | Procedure Document                    |
| Status        | Active                                |
| Version       | 1.0                                   |

---

## Purpose

This document defines the standard procedure for creating Active Directory security groups within the Northwind Technologies environment.

The process ensures groups are created consistently, assigned appropriate permissions, and aligned with company security standards.

---

## Environment Note

Note: The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Prerequisites

Before creating a group, verify:
- Business justification exists.
- Department ownership has been identified.
- Required permissions are known.
- Management approval has been received.
- Naming standards have been reviewed.

---

## Required Information

| Field       | Example                |
| ----------- | ---------------------- |
| Group Name  | SG-IT-Users            |
| Department  | Information Technology |
| Group Scope | Global                 |
| Group Type  | Security               |
| Purpose     | Department access      |

---

## Procedure (GUI Method)

1. Open Active Directory Users and Computers
   - Navigate to:
     - Server Manager
    → Tools
        → Active Directory Users and Computers
2. Select the Groups OU
    - Browse to:
      - lab.local
        └── Groups
    - If department group OUs are created later:
      - lab.local
           └── Groups
                ├── HR
                ├── Finance
                ├── IT
                ├── Engineering
                ├── Marketing
                ├── Operations
                ├── Sales
                └── Executive
3. Create the Group
    - Right-click the destination OU:
      - New → Group
    - Enter:
      - Group name
      - Description
      - Group scope
      - Grout type
    - Examples:
      - Group Name: SG-IT-Users
      - Description: Information Technology department users
      - Group Scope: Global
      - Group Type: Security
4. Configure Group Settings
   - Verify:
     - Group name follows stanards.
     - Scope is correct.
     - Type is set to Security.
     - Description is populated.
5. Complete Group Creation
   - Click:
     - OK
   - Verify the group appears in the correct Organizational Unit.

---

## Procedure (PowerShell Method)
1. Open PowerShell as Administrator.
   - Example:
     - New-ADGroup `
            -Name "SG-IT-Users" `
            -SamAccountName "SG-IT-Users" `
            -GroupCategory Security `
            -GroupScope Global `
            -DisplayName "SG-IT-Users" `
            -Description "Information Technology department users" `
            -Path "CN=Users,DC=lab,DC=local"

---

## Recommended Group Scope Usage

| Scope        | Use Case                  |
| ------------ | ------------------------- |
| Global       | Department users          |
| Domain Local | Resource permissions      |
| Universal    | Multi-domain environments |

---

## Post-Creation Tasks

After creating the group:
- Add users.
- Assign permissions.
- Document ownership.
- Configure shared folder access.
- Verify Group Policy requirements.
- Update documentation.
- Add the group to shared folder ACLs if required.

---

## Validation

Verify:
- Group object exists in Active Directory.
- Group name follows standards.
- Group scope is correct.
- Group category is Security.
- Membership can be modified.
- Permissions function correctly.

---

## Troubleshooting

| Issue                   | Resolution               |
| ----------------------- | ------------------------ |
| Group creation fails    | Verify permissions       |
| Group already exists    | Check naming standards   |
| Incorrect group scope   | Recreate or modify group |
| Group not visible       | Refresh ADUC             |
| Access problems persist | Review memberships       |

---

## Common Group Examples

| Group                   | Purpose                       |
| ----------------------- | ----------------------------- |
| SG-HR-Users             | Human Resources access        |
| SG-Finance-Users        | Finance access                |
| SG-IT-Users             | Information Technology access |
| SG-HelpDesk-Technicians | Help desk support             |
| SG-Security-Operations  | Security monitoring           |

---

## Related Documents

- Group-Standards.md
- User-Standards.md
- User-Creation-Procedure.md
- OU-Design.md
- NWT-SOP-001 Active Directory Administration SOP

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


