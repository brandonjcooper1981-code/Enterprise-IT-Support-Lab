# NWT-RUN-004 Network Drive Missing

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Runbook ID | NWT-RUN-004 |
| Severity | Medium |
| Estimated Resolution | 15–30 minutes |
| Escalation Team | Infrastructure |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve missing network drives within the Northwind Technologies environment.

---

## Symptoms

- Mapped drives do not appear in File Explorer.
- User receives "Network path not found."
- Drive displays a red X.
- User cannot access shared folders.
- Logon scripts fail.
- Department shares are unavailable.

---

## Systems Affected

- DC01
- File Server
- Windows 11 workstations
- Group Policy
- Active Directory
- northwind.local
- Department file shares

---

## Standard Drive Mappings

| Drive | Purpose |
|--------|--------|
| H: | User home directory |
| S: | Shared department files |
| P: | Public share |

---

## Investigation

1. Verify user identity using approved methods.
2. Verify workstation network connectivity.
3. Verify the drive is missing from File Explorer.
4. Check current mappings: ```powershell net use```
5. Verify DNS resolution: ```powershell nslookup DC01```
6. Verify access to the share: ```powershell \\DC01\Shared```
7. Verify the user belongs to the correct security group.
8. Verify Group Policy application: ```powershell gpresult /r```
9. Review Event Viewer logs.

---

## Resolution

1. Disconnect stale mappings: ```powershell net use * /delete```
2. Refresh Group Policy: ```powershell gpupdate /force```
3. Reboot the workstation if necessary.
4. Open: \\DC01\Shared
5. Manually remap the drive if required: ```powershell net use S: \\DC01\Shared```
6. Verify drive permissions.
7. Verify login scripts and GPO settings.

---

## Validation

- Drive appears in File Explorer.
- User can access files.
- Security permissions are correct.
- Group Policy applies successfully.
- Drive reconnects after reboot.

---

## Escalation Criteria

Escalate if:
- Multiple users are affected.
- File server is unavailable.
- Group Policy fails.
- Share permissions are incorrect.
- DNS issues persist.

---

## Key Event IDs

| Event ID | Description |
|-----------|-----------|
| 4098 | Group Policy Preferences drive mapping failure |
| 1058 | Group Policy processing failure |
| 1129 | Domain controller unavailable |
| 4624 | Successful logon |
| 4625 | Failed logon |

---

## Common Commands

```powershell
net use

net use * /delete

net use S: \\DC01\Shared

gpupdate /force

gpresult /r

gpresult /h C:\gpreport.html

nslookup DC01

ipconfig /all

whoami

whoami /groups
```

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-SOP-006 File Services Administration SOP
- NWT-RUN-003 Domain Join Failure

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

