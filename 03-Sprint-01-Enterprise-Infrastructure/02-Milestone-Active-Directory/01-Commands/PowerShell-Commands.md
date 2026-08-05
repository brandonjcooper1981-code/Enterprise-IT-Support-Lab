# PowerShell Commands

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Administrative Reference |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document serves as the centralized PowerShell command reference for the Northwind Technologies Active Directory environment.
The commands listed throughout this guide were used during deployment, validation, administration, troubleshooting, and ongoing maintenance of the enterprise Active Directory infrastructure.

---

## Environment Note

Note:
The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned production naming standard and future enterprise environment.

---

## Table of Contents

- Active Directory
- Users
- Groups
- Organizational Units
- Group Policy
- DNS
- DHCP
- Network
- Validation
- Troubleshooting
- Server Administration

---

## Active Directory Commands

### Verify Domain

```powershell
Get-ADDomain
```

Purpose:
Displays Active Directory domain information.

### Verify Forest

```powershell
Get-ADForest
```

Purpose:
Displays forest configuration.

### List Domain Controllers

```powershell
Get-ADDomainController -Filter *
```

Purpose:
Displays all Domain Controllers.

---

## User Administration

### List Users

```powershell
Get-ADUser -Filter *
```

Purpose:
Displays all Active Directory users.

### User Details

```powershell
Get-ADUser bjcooper -Properties *
```

Purpose:
Displays every property for a user.

### Create User

```powershell
New-ADUser
```

Purpose:
Creates a new Active Directory user.

### Disable User

```powershell
Disable-ADAccount
```

### Unlock Account

```powershell
Unlock-ADAccount
```

### Reset Password

```powershell
Set-ADAccountPassword
```

---

## Group Administration

### List Groups

```powershell
Get-ADGroup -Filter *
```

### Group Members

```powershell
Get-ADGroupMember "SG-IT-Users"
```

### User Group Membership

```powershell
Get-ADPrincipalGroupMembership bjcooper
```

### Create Group

```powershell
New-ADGroup
```

### Add Group Member

```powershell
Add-ADGroupMember
```

### Remove Group Member

```powershell
Remove-ADGroupMember
```

---

## Organizational Unit Commands

### List OUs

```powershell
Get-ADOrganizationalUnit -Filter *
```

### Create OU

```powershell
New-ADOrganizationalUnit
```

### Search Specific OU

```powershell
Get-ADObject -SearchBase "OU=IT,DC=lab,DC=local" -Filter *
```

---

## Group Policy Commands

### Update Policies

```powershell
gpupdate /force
```

### Applied Policies

```powershell
gpresult /r
```

### HTML Report

```powershell
gpresult /h report.html
```

### List GPOs

```powershell
Get-GPO -All
```

### View GPO Inheritance

```powershell
Get-GPInheritance -Target "OU=IT,DC=lab,DC=local"
```

---

## DNS Commands

### Resolve Domain

```powershell
Resolve-DnsName lab.local
```

### Name Lookup

```powershell
nslookup dc01
```

### IP Configuration

```powershell
ipconfig /all
```

### Flush DNS

```powershell
ipconfig /flushdns
```

### Domain Computers

```powershell
Get-ADComputer -Filter *
```

Purpose:
Lists all domain-joined computers.

### Restart DNS Service

```powershell
Restart-Service DNS
```

Purpose:
Restarts the DNS service after configuration changes.

---

## DHCP Commands

### DHCP Scopes

```powershell
Get-DhcpServerv4Scope
```

### DHCP Leases

```powershell
Get-DhcpServerv4Lease
```

---

## Validation Commands

### Domain Diagnostics

```powershell
dcdiag
```

### Ping DC

```powershell
ping dc01
```

### Test Secure Channel

```powershell
Test-ComputerSecureChannel
```

---

## Server Administration

### Installed Roles

```powershell
Get-WindowsFeature
```

### Services

```powershell
Get-Service
```

### Running Processes

```powershell
Get-Process
```

### Computer Information

```powershell
Get-ComputerInfo
```

---

## Troubleshooting Commands

| Issue | Command |
|---------|---------|
| GPO Problems | `gpupdate /force` |
| GPO Verification | `gpresult /r` |
| DNS Problems | `Resolve-DnsName` |
| Network Issues | `ipconfig /all` |
| OU Validation | `Get-ADOrganizationalUnit` |
| User Validation | `Get-ADUser` |
| Group Validation | `Get-ADGroup` |
| Domain Health | `dcdiag` |

---

## Command Categories Summary

| Category | Commands |
|----------|----------:|
| Active Directory | 3 |
| Users | 6 |
| Groups | 6 |
| Organizational Units | 3 |
| Group Policy | 5 |
| DNS | 4 |
| DHCP | 2 |
| Validation | 3 |
| Server Administration | 4 |

---

## Best Practices

Northwind Technologies recommends:
- Run PowerShell as Administrator when required.
- Test commands in a lab before production.
- Verify command output before making changes.
- Document administrative actions.
- Use least privilege.
- Validate changes after execution.
- Prefer PowerShell over GUI tools when appropriate.
- Keep command history for troubleshooting and auditing.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- DHCP-Commands.md
- Troubleshooting.md
- Validation-Checklist.md
- Implementation-Steps.md
- Active-Directory-Design.md

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
