# User Creation Procedure

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Procedure Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the standard procedure for creating Active Directory user accounts within the Northwind Technologies environment.

The process ensures that accounts are created consistently, assigned to the correct department, and configured according to company security standards.

---

## Environment Note

> **Note:** The current implementation environment uses the `lab.local`
> Active Directory domain. References to `northwind.local`
> throughout Northwind Technologies documentation represent
> the planned enterprise naming standard and future production
> environment.

---

## Prerequisites

Before creating an account, verify:

- Employee name has been approved.
- Department assignment is known.
- Required security groups are identified.
- Manager approval has been received.
- Temporary password has been generated.

---

## Required Information

| Field | Example |
|----------|----------|
| First Name | Brandon |
| Last Name | Cooper |
| Username | bjcooper |
| Department | IT |
| Job Title | Help Desk Technician |
| Email Address | bjcooper@northwind.local |
| Temporary Password | TempPassword123! |

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

### Step 2: Select the Department OU

Browse to:

```text
lab.local
    ├── HR
    ├── Finance
    ├── IT
    ├── Engineering
    ├── Marketing
    ├── Operations
    ├── Sales
    └── Executive
```

Example departmental OUs:
- HR
- Finance
- IT
- Engineering
- Marketing
- Operations
- Sales
- Executive

---

### Step 3: Create the User

Right-click the department OU:

```text
New → User
```

Enter:
- First Name
- Last Name
- Full Name
- User Logon Name

Example:

```text
First Name: Brandon
Last Name: Cooper
Full Name: Brandon J. Cooper
User Logon Name: bjcooper
```

---

### Step 4: Configure the Password

Assign a temporary password.

Enable:
- User must change password at next logon.

Disable:
- User cannot change password.
- Password never expires.

---

### Step 5: Complete User Creation

Click:

```text
Next → Finish
```

Verify the user appears in the correct Organizational Unit.

---

## Procedure (PowerShell Method)

Open PowerShell as Administrator.

Example:

```powershell
New-ADUser `
    -Name "Brandon J. Cooper" `
    -GivenName "Brandon" `
    -Surname "Cooper" `
    -SamAccountName "bjcooper" `
    -UserPrincipalName "bjcooper@lab.local" `
    -Path "OU=IT,DC=lab,DC=local" `
    -Enabled $true `
    -AccountPassword (ConvertTo-SecureString "TempPassword123!" -AsPlainText -Force) `
    -ChangePasswordAtLogon $true
```

---

## Post-Creation Tasks

After creating the account:
- Add user to department security groups.
- Configure shared folder permissions.
- Verify Group Policy application.
- Update employee documentation.
- Test login functionality.

---

## Validation

Verify:
- User object exists in Active Directory.
- Username follows company standards.
- User is in the correct OU.
- Group memberships are correct.
- Login succeeds.
- Password reset requirement is enforced.

---

## Troubleshooting

| Issue | Resolution |
|----------|----------|
| User cannot log in | Verify password and account status |
| Account is disabled | Enable the account |
| User placed in wrong OU | Move object to correct OU |
| Group Policy does not apply | Run `gpupdate /force` |
| Username conflict exists | Modify naming convention |

---

## Related Documentation

- User-Standards.md
- OU-Design.md
- Implementation-Steps.md
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
