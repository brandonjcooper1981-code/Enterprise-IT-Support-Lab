# Active Directory Commands

| Property | Value |
|---|---|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Administrative Command Reference |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides a centralized command reference for administering and troubleshooting Active Directory Domain Services within the Northwind Technologies environment.
The commands support domain validation, user administration, group management, Organizational Unit management, computer administration, authentication troubleshooting, and routine directory maintenance.

---

## Environment Note

Note:
The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Prerequisites

Before using the commands in this guide:
- Sign in with an authorized administrative account.
- Open PowerShell as Administrator when required.
- Confirm that the Active Directory PowerShell module is installed.
- Verify network and DNS connectivity to DC01.
- Test changes in the lab environment before production deployment.
- Review command output before modifying directory objects.

---

## Active Directory Module

### Import the Active Directory Module

```powershell
Import-Module ActiveDirectory
```

Purpose:
Loads the Active Directory PowerShell module into the current session.

### Verify the Module

```powershell
Get-Module ActiveDirectory -ListAvailable
```

Purpose:
Confirms that the Active Directory module is installed.

## Domain and Forest Commands

### Display Domain Information

```powershell
Get-ADDomain
```

Purpose:
Displays the current Active Directory domain configuration.

### Display Forest Information

```powershell
Get-ADForest
```

Pupose:
Displays forest-wide configuration and domain information.

### List Domain Controllers

```powershell
Get-ADDomainController -Filter *
```

Purpose:
Displays all available domain controllers.

### Locate a Domain Controller

```powershell
Get-ADDomainController -Discover
```

Purpose:
Locates an available domain controller for the current domain.

### Display the Current Domain

```powershell
$env:USERDNSDOMAIN
```

Purpose:
Display the DNS name of the user's current domain.

---

## User Administration

### List All Users

```powershell
Get-ADUser -Filter *
```

Purpose:
Display all Active Directory user accounts.

### Display Detailed User Properties

```powershell
Get-ADUser -Filter * -Properties Department, Title, Enabled |
    Select-Object Name, SamAccountName, Department, Title, Enabled
```

Purpose:
Displays useful account attributes in a readable format.

### Display Selected User Information

```powershell
Get-ADUser -Identity "bjcooper" -Properties *
```

Purpose:
Displays all available properties for the selected user.

### Locate a User by Name

```powershell
Get-ADUser -Filter "Name -like '*Cooper*'"
```

Purpose:
Searches for users whose names match the specified value.

### Create a User

```powershell
New-ADUser `
    -Name "Brandon J. Cooper" `
    -GivenName "Brandon" `
    -Surname "Cooper" `
    -SamAccountName "bjcooper" `
    -UserPrincipalName "bjcooper@lab.local" `
    -Path "OU=IT,DC=lab,DC=local" `
    -Enabled $true `
    -AccountPassword (ConvertTo-SecureString "TemporaryPassword123!" -AsPlainText -Force) `
    -ChangePasswordAtLogon $true
```

Purpose:
Creates and enables a new Active user account.

### Enable a User account

```powershell
Enable-ADAccount -Identity "bjcooper"
```

### Disable a User Account

```powershell
Disable-ADAccount -Identity "bjcooper"
```

### Unlock a User Account

```powershell
Unlock-ADAccount -Identity "bjcooper"
```

Purpose:
Unlocks an Active Directory account after account lockout

### Reset a User Password

```powershell
Set-ADAccountPassword `
    -Identity "bjcooper" `
    -Reset `
    -NewPassword (Read-Host "Enter temporary password" -AsSecureString)
```

### Require Password Change at Next Logon

```powershell
Set-ADUser -Identity "bjcooper" -ChangePasswordAtLogon $true
```

### Update User Attributes

```powershell
Set-ADUser `
    -Identity "bjcooper" `
    -Department "Information Technology" `
    -Title "Help Desk Technician"
```

### Move a User to Another OU

```powershell
Get-ADUser -Identity "bjcooper" |
    Move-ADObject -TargetPath "OU=IT,DC=lab,DC=local"
```

### Remove a User Account

```powershell
Remove-ADUser -Identity "bjcooper" -Confirm
```

Purpose:
Deletes the specified Active Directory account after confirmation.

---

## Group Administration

### List all Groups

```powershell
Get-ADGroup -Filter *
```

### Display Group Details

```powershell
Get-ADGroup -Identity "SG-IT-Users" -Properties *
```

### List Group Members

```powershell
Get-ADGroupMember -Identity "SG-IT-Users"
```

### List Nested Group Members

```powershell
Get-ADGroupMember -Identity "SG-IT-Users" -Recursive
```

### Displays a User's Group Memberships

```powershell
Get-ADPrincipalGroupMembership -Identity "bjcooper"
```

### Create a Security Group

```powershell
New-ADGroup `
    -Name "SG-IT-Users" `
    -SamAccountName "SG-IT-Users" `
    -GroupCategory Security `
    -GroupScope Global `
    -DisplayName "SG-IT-Users" `
    -Description "Information Technology department users" `
    -Path "OU=Groups,DC=lab,DC=local"
```

### Add a User to a Group

```powershell
Add-ADGroupMember `
    -Identity "SG-IT-Users" `
    -Members "bjcooper"
```

### Remove a User from a Group

```powershell
Remove-ADGroupMember `
    -Identity "SG-IT-Users" `
    -Members "bjcooper" `
    -Confirm
```

### Verify Membership

```powershell
Get-ADGroupMember -Identity "SG-IT-Users" |
    Where-Object SamAccountName -eq "bjcooper"
```

---

## Organizational Unit Administration

### List All Organizational Units

```powershell
Get-ADOrganizationalUnit -Filter *
```

### Display OU Names and Distinguished Names

```powershell
Get-ADOrganizationalUnit -Filter * |
    Select-Object Name, DistinguishedName
```

### Locate a Specific OU

```powershell
Get-ADOrganizationalUnit -Filter "Name -eq 'IT'"
```

### Create an OU

```powershell
New-ADOrganizationalUnit `
    -Name "Information Technology" `
    -Path "DC=lab,DC=local" `
    -ProtectedFromAccidentalDeletion $true
```

### Search Objects Within an OU

```powershell
Get-ADObject `
    -SearchBase "OU=IT,DC=lab,DC=local" `
    -Filter *
```

### Move an Object to an OU

```powershell
Move-ADObject `
    -Identity "CN=Brandon J. Cooper,OU=Users,DC=lab,DC=local" `
    -TargetPath "OU=IT,DC=lab,DC=local"
```

### Protect an OU from Accidental Deletion

```powershell
Set-ADOrganizationalUnit `
    -Identity "OU=IT,DC=lab,DC=local" `
    -ProtectedFromAccidentalDeletion $true
```

---

## Computer Administration

### List Domain Computers

```powershell
Get-ADComputer -Filter *
```

### Display Computer Details

```powershell
Get-ADComputer -Identity "CLIENT01" -Properties *
```

### Display Enabled Computers

```powershell
Get-ADComputer -Filter "Enabled -eq 'True'" |
    Select-Object Name, DNSHostName, Enabled
```

### Disable a Computer Account

```powershell
Disable-ADAccount -Identity "CLIENT01$"
```

### Enable a Computer Account

```powershell
Enable-ADAccount -Identity "CLIENT01$"
```

### Reset the Local Computer Machine Password

```powershell
Reset-ComputerMachinePassword -Server "DC01"
```

Purpose:
Resets the local computer's machine-account password and synchronizes it with DC01. Run this command from the affected domain-joined workstation.

### Test the Secure Channel

```powershell
Test-ComputerSecureChannel -Verbose
```

### Repair the Secure Channel

```powershell
Test-ComputerSecureChannel `
    -Repair `
    -Credential (Get-Credential) `
    -Verbose
```

---

## Password and Account Policy

### Display the Default Domain Password Policy

```powershell
Get-ADDefaultDomainPasswordPolicy
```

### Display Locked Accounts

```powershell
Search-ADAccount -LockedOut
```

### Display Expired Accounts

```powershell
Search-ADAccount -AccountExpired
```

### Display Inactive User Accounts

```powershell
Search-ADAccount `
    -UsersOnly `
    -AccountInactive `
    -TimeSpan 90.00:00:00
```

----

## Authentication and Directory Validation

### Run Domain Controller Diagnostics

```powershell
dcdiag
```

### Run Detailed Domain Controller Diagnostics

```powershell
dcdiag /v
```

### Verify Domain Controller Discovery

```powershell
nltest /dsgetdc:lab.local
```

### Verify the Workstation Secure Channel

```powershell
nltest /sc_verify:lab.local
```

### Display the Logged-In User

```powershell
whoami
```

### Display User Security Groups

```powershell
whoami /groups
```

### Display the Current Logon Server

```powershell
$env:LOGONSERVER
```

---

## Active Directory Service Commands

### Check the AD DS Service

```powershell
Get-Service NTDS
```

### Check DNS Service Status

```powershell
Get-Service DNS
```

### Check Netlogon Service Status

```powershell
Get-Service Netlogon
```

### Restart Netlogon

```powershell
Restart-Service Netlogon
```

### Display Related Services

```powershell
Get-Service NTDS, DNS, Netlogon, KDC
```

---

## Export and Reporting Commands

### Export Users to CSV

```powershell
Get-ADUser -Filter * -Properties Department, Title, Enabled |
    Select-Object Name, SamAccountName, Department, Title, Enabled |
    Export-Csv "C:\Reports\AD-Users.csv" -NoTypeInformation
```

### Export Groups to CSV

```powershell
Get-ADGroup -Filter * |
    Select-Object Name, GroupCategory, GroupScope |
    Export-Csv "C:\Reports\AD-Groups.csv" -NoTypeInformation
```

### Export Organizational Units

```powershell
Get-ADOrganizationalUnit -Filter * |
    Select-Object Name, DistinguishedName |
    Export-Csv "C:\Reports\AD-OUs.csv" -NoTypeInformation
```

### Ecport Group Membership

```powershell
Get-ADGroupMember -Identity "SG-IT-Users" |
    Select-Object Name, SamAccountName, ObjectClass |
    Export-Csv "C:\Reports\SG-IT-Users-Members.csv" -NoTypeInformation
```

---

## Troubleshooting Reference

| Issue | Recommended Command |
|---|---|
| Domain cannot be located | `nltest /dsgetdc:lab.local` |
| User account is locked | `Search-ADAccount -LockedOut` |
| User cannot authenticate | `Get-ADUser -Identity "username" -Properties *` |
| Group access is missing | `Get-ADPrincipalGroupMembership "username"` |
| Group membership is incorrect | `Get-ADGroupMember "group-name"` |
| Computer trust relationship fails | `Test-ComputerSecureChannel -Verbose` |
| Domain Controller health issue | `dcdiag /v` |
| AD service unavailable | `Get-Service NTDS` |
| Netlogon issue | `Get-Service Netlogon` |
| Object is in the wrong OU | `Get-ADObject -SearchBase "<OU path>" -Filter *` |

---

## Best Practices

Northwind Technologies recommends:
- Use security groups instead of assigning permissions directly to users.
- Follow the AGDLP permission model.
- Use separate administrative and standard user accounts.
- Verify the target OU before creating or moving objects.
-Avoid embedding passwords in scripts.
- Use -WhatIf when supported before performing bulk changes.
- Export directory information before major modifications.
- Document account, group, and OU changes.
- Apply least privilege.
- Validate changes after execution.

Example:
```powershell
Remove-ADUser -Identity "bjcooper" -WhatIf
```

---

## Related Documentation

- PowerShell-Commands.md
- DNS-Commands.md
- DHCP-Commands.md
- Troubleshooting.md
- User-Standards.md
- User-Creation-Procedure.md
- Group-Standards.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md
- OU-Design.md
- Active-Directory-Design.md
- Validation-Checklist.md

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
