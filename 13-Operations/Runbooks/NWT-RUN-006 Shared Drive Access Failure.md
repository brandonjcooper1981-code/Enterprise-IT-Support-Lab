# NWT-RUN-006 Shared Drive Access Failure

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-006                           |
| Severity             | Medium                                |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve user access failures involving shared folders and file shares within the Northwind Technologies environment.

---

## Symptoms

- User receives "Access Denied."
- Shared folder opens but files cannot be modified.
- User can see the share but cannot enter it.
- Department folders are missing.
- Mapped drives display permission errors.
- Applications cannot save files to network storage.

---

## Systems Affected

- DC01
- File Server
- Shared folders
- Windows 11 workstations
- Active Directory
- Group Policy
- northwind.local

---

## Common Shares

| Share           | Purpose               |
| --------------- | --------------------- |
| `\\DC01\Shared` | Department data       |
| `\\DC01\Public` | Company-wide files    |
| `\\DC01\Home`   | User home directories |

---

## Investigation

1. Verify user identity.
2. Confirm network connectivity.
3. Verify the share is reachable: ``` \\DC01\Shared```
4. Verify current drive mappings: ```powershell net use```
5. Verify user group membership: ```powershell whoami /groups```
6. Review NTFS permissions: ```powershell Get-Acl \\DC01\Shared```
7. Review share permissions: ``` Get-SmbShareAccess -Name Shared```
8. Verify Group Policy applied successfully: ```powershell gpresult /r```
9. Review Event Viewer logs.

---

## Resolution

1. Vreify the user belongs to the correct security group.
2. Verify NTFS permissions.
3. Verify share permissions.
4. Verify inheritance settings.
5. Verify both Share and NTFS permissions.
   1. Notes:
      1. Effective permissions are the most restrictive combination of Share and NTFS permissions.
      2. Deny permissions overide Allow permissions.
6. Force Group Policy refresh: ```powershell gpupdate /force```
7. Disconnect stale mappings: ```powershell net use * /delete```
8. Remap the drive: ```powershell net use S: \\Dc01\Shared```
9.  Test file creation and modification.
10. Log off and back on if neccassary.

---

## Validation

- User can open the share.
- User can create folders.
- User can edit files.
- Permissions match department requirements.
- Drive reconnects after login.
- No new access errors appear.
- User can create, modify and delete files according to assigned permissions.

---

## Escalation Criteria

Escalate if:
- Multiple users are affected.
- NTFS permissions are corrupted.
- Share permissions conflict with NTFS permissions.
- File server storage issues exist.
- Inheritance failures occur.
- File system errors are detected.

---

## Key Event IDs

| Event ID | Description            |
| -------- | ---------------------- |
| 5140     | Network share accessed |
| 5145     | Share access check     |
| 4624     | Successful logon       |
| 4625     | Failed logon           |
| 4663     | Object access          |
| 4670     | Permission change      |

---

## Common Commands

net use

net use * /delete

net use S: \\DC01\Shared

whoami

whoami /groups

Get-Acl \\DC01\Shared

Get-SmbShare

Get-SmbShareAccess -Name Shared

Get-SmbOpenFile

Close-SmbOpenFile

icacls \\DC01\Shared

gpupdate /force

Get-ADUser username -Properties MemberOf

Get-LocalGroupMember Administrators

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-SOP-006 File Services Administration SOP
- NWT-RUN-004 Network Drive Missing
- NWT-RUN-005 Group Policy Failure

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
