# Group Membership Procedure

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Procedure Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the standard procedure for assigning and removing users from Active Directory security groups within the Northwind Technologies environment.

The process ensures access permissions are granted consistently, follow the principle of least privilege, and comply with company security standards.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Prerequisites

Before modifying group membership, verify:
- User account exists.
- Target security group exists.
- Business justification has been provided.
- Manager approval has been received.
- Appropriate permissions have been granted.

---

## Required Information

| Field | Example |
|--------|--------|
| Username | bjcooper |
| Full Name | Brandon J. Cooper |
| Group Name | SG-IT-Users |
| Department | Information Technology |
| Change Type | Add |
| Requested By | Michael Wilson |

---

## Procedure (GUI Method)

### Step 1: Open Active Directory Users and Computers

Navigate to:

```text
Server Manager
    → Tools
        → Active Directory Users and Computers
```

---

### Step 2: Locate the User

Browse to:

```text
lab.local
    └── IT
```

Select the user account.

---

### Step 3: Open Group Membership

Right-click the user:

```text
Properties
    → Member Of
```

---

### Step 4: Add Group Membership

Click:

```text
Add
```

Enter:

```text
SG-IT-Users
```

Click:

```text
Check Names
```

Then:

```text
OK
```

---

### Step 5: Apply Changes

Click:

```text
Apply → OK
```

Verify the group appears under the user's membership list.

---

## Procedure (PowerShell Method)

Open PowerShell as Administrator.

Example:

```powershell
Add-ADGroupMember `
    -Identity "SG-IT-Users" `
    -Members "bjcooper"
```

Remove membership:

```powershell
Remove-ADGroupMember `
    -Identity "SG-IT-Users" `
    -Members "bjcooper"
```

View memberships:

```powershell
Get-ADPrincipalGroupMembership bjcooper
```

---

## Membership Rules

Northwind Technologies follows these standards:
- Users receive access through groups only.
- Permissions are not assigned directly to users.
- Administrative groups require approval.
- Temporary access must be documented.
- Membership reviews occur quarterly.

---

## Post-Change Tasks

After modifying membership:
- Verify shared folder access.
- Verify application access.
- Update documentation.
- Notify the requester.
- Record any temporary permissions.

---

## Validation

Verify:
- User appears in the correct group.
- Group membership follows company standards.
- Access permissions function correctly.
- No excessive permissions were granted.
- Changes replicate successfully.
- Group membership changes are reflected after user logoff/logon.

---

## Troubleshooting

| Issue | Resolution |
|--------|--------|
| User cannot access resource | Verify group membership |
| Group cannot be found | Check naming standards |
| Access denied | Verify NTFS permissions |
| Changes do not appear | Force AD replication |
| Incorrect permissions | Review group assignments |

---

## Useful Commands

```powershell
Get-ADPrincipalGroupMembership bjcooper

Add-ADGroupMember -Identity "SG-IT-Users" -Members "bjcooper"

Remove-ADGroupMember -Identity "SG-IT-Users" -Members "bjcooper"

repadmin /syncall
```

---

## Common Group Examples

| Group | Purpose |
|--------|--------|
| SG-IT-Users | Department access |
| SG-HelpDesk-Technicians | Help desk permissions |
| SG-Domain-Admins | Domain administration |
| SG-Security-Operations | Security monitoring |
| SG-Finance-Users | Finance resources |

---

## Related Documents

- User-Standards.md
- User-Creation-Procedure.md
- Group-Standards.md
- Group-Creation-Procedure.md
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
