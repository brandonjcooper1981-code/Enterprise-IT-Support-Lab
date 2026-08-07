# Validation Checklist

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Architecture Design Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides the standard validation procedures used to verify the successful deployment of the Northwind Technologies Active Directory environment.

The checklist ensures that Active Directory services, Organizational Units, users, security groups, Group Policy Objects (GPOs), network services, and workstation configurations function as designed before the environment is considered production-ready.

---

## Environment Note

**Note**

The current implementation environment uses the **lab.local** Active Directory domain. References to **northwind.local** throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Validation Scope

| Component | Status |
|-----------|--------|
| Active Directory | ☐ |
| DNS | ☐ |
| DHCP | ☐ |
| OUs | ☐ |
| Users | ☐ |
| Groups | ☐ |
| GPOs | ☐ |
| File Shares | ☐ |
| Drive Mapping | ☐ |
| Desktop Configuration | ☐ |

---

## Infrastructure Validation

Checklist:
- Domain Controller online
- Server reachable
- Time synchronization
- Network connectivity
- Event Viewer clean
- Windows Updates installed

---

## Active Directory Validation

Verify:
- Domain operational
- Forest healthy
- Replication healthy (future expansion)
- Authentication working
- Domain Controller advertising

PowerShell:
```powershell
dcdiag
```

```powershell
Get-ADDomain
```

```powershell
Get-ADForest
```

---

## OU Validation

Checklist:
- HR OU exists
- Finance OU exists
- IT OU exists
- Engineering OU exists
- Marketing OU exists
- Operations OU exists
- Sales OU exists
- Executive OU exists

PowerShell:
```powershell
Get-ADOrganizationalUnit -Filter *
```

---

## User Validation

Verify:
- Users created
- Naming convention correct
- Password required
- Department assignment
- OU location correct

PowerShell:
```powershell
Get-ADUser -Filter *
```

----

## Group Validation

Verify:
- Security groups created
- Users assigned
- AGDLP followed
- No direct permissions
- Group nesting correct

PowerShell:
```powershell
Get-ADGroup -Filter *
```

```powershell
Get-ADGroupMember "SG-IT-Users"
```

---

## Group Policy Validation

Checklist:
- Password Policy
- Desktop Lock
- Desktop Configuration
- Drive Mapping

Verify:
- GPO linked correctly
- Security Filtering correct
- Applies successfully

PowerShell:
```powershell
gpresult /r
```

```powershell
gpresult /h report.html
```

```powershell
gpupdate /force
```

---

## DNS Validation

Verify:
- Forward Lookup Zone
- Reverse Lookup Zone
- DC resolves
- Client resolves
- Internet access

Commands:
```powershell
nslookup dc01
```

```powershell
Resolve-DnsName lab.local
```

---

## DHCP Validation

Verify:
- Scope active
- Address assigned
- Gateway assigned
- DNS assigned
- Lease active

Commands:
```powershell
ipconfig /all
```

```powershell
Get-DhcpServerv4Scope
```

----

## File Share Validation

Verify:
- Department shares exist
- Permissions correct
- Read access
- Write access
- Hidden shares protected

---

## Drive Mapping Validation

Verify:
- Correct drive letters
- Correct department
- Persistent mappings
- GPO applied

---

## Desktop Configuration Validation

Verify:
- Wallpaper applied
- Screen saver active
- Desktop restrictions
- Taskbar standard
- File explorer settings

---

## Security Validation

Verify:
- Password policy
- Lockout policy
- Least privilege
- Administrative separation
- GPO security filtering
- Audit policy

---

## PowerShell Validation Commands

```powershell
dcdiag
```

```powershell
Get-ADUser -Filter *
```

```powershell
Get-ADGroup -Filter *
```

```powershell
Get-ADOrganizationalUnit -Filter *
```

```powershell
gpresult /r
```

```powershell
gpupdate /force
```

```powershell
ipconfig /all
```

```powershell
Resolve-DnsName lab.local
```

---

## Deployment Sign-Off Checklist

| Validation Item | Complete |
|-----------------|----------|
| Active Directory Operational | ☐ |
| DNS Operational | ☐ |
| DHCP Operational | ☐ |
| Organizational Units Verified | ☐ |
| Users Verified | ☐ |
| Groups Verified | ☐ |
| GPOs Applied | ☐ |
| Shared Folders Accessible | ☐ |
| Drive Mapping Working | ☐ |
| Desktop Configuration Applied | ☐ |
| Documentation Complete | ☐ |

---

## Related Documentation

- Active-Directory-Design.md
- OU-Design.md
- Group-Design.md
- User-Standards.md
- Group-Standards.md
- Password-Policy-GPO.md
- Desktop-Lock-GPO.md
- Desktop-Configuration-GPO.md
- Drive-Mapping-GPO.md
- Implementation-Steps.md
- PowerShell-Commands.md

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
