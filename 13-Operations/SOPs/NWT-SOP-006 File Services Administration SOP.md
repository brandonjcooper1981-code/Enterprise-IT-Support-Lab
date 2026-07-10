# NWT-SOP-006 File Services Administration SOP

| Property | Value |
|----------|----------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-006 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain the Northwind Technologies file services infrastructure.

The file services environment supports departmental collaboration, centralized storage, permissions management, user home directories, and enterprise resource sharing.

---

## Purpose

This SOP defines standards and procedures for:

- File share administration
- NTFS permissions management
- Share permissions management
- Folder creation
- Access requests
- Security group integration
- Storage monitoring
- Troubleshooting
- Backup and recovery
- Security controls

---

## Scope

Applies to:

- Windows Server 2025
- Active Directory
- File shares
- Department shares
- User home folders
- Security groups
- Group Policy drive mappings
- Windows 11 workstations
- Future cloud storage solutions

---

## Supported Systems

- DC01
- northwind.local
- File Server
- Windows File Services
- Active Directory
- DNS Server
- DHCP Server
- Group Policy
- Windows 11 clients

---

## Administrative Tools

Authorized tools include:

- File Explorer
- Server Manager
- Computer Management
- Active Directory Users and Computers
- Group Policy Management Console (GPMC)
- PowerShell
- Event Viewer
- Command Prompt
- RSAT Tools
- Wazuh (Future)

---

## File Services Architecture

northwind.local

├── Shared Folders

│   ├── IT

│   ├── Finance

│   ├── Human Resources

│   └── Public

├── User Home Directories

│   ├── Employees

│   └── Administrators

├── Security Groups

│   ├── IT-Users

│   ├── Finance-Users

│   ├── HR-Users

│   └── HelpDesk

└── Drive Mappings

    ├── H: Home

    ├── S: Shared

    └── P: Public

---

## File Share Standards

- Use security groups for access control.
- Avoid assigning permissions directly to users.
- Use least privilege.
- Document all shares.
- Separate NTFS and share permissions.

---

## NTFS Permission Standards

| Permission   | Purpose               |
| ------------ | --------------------- |
| Read         | View files            |
| Modify       | Edit files            |
| Full Control | Administrative access |

---

## Share Permission Standards

| Group             | Access       |
| ----------------- | ------------ |
| Domain Users      | Read         |
| Department Groups | Modify       |
| ITAdmins          | Full Control |

---

## Administrative Tasks

| Task                 | Frequency |
| -------------------- | --------- |
| Review permissions   | Monthly   |
| Verify shares        | Monthly   |
| Review audit logs    | Monthly   |
| Validate backups     | Quarterly |
| Remove stale folders | Quarterly |

---

## Troubleshooting Playbooks

### Can not access shared folder

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify network connectivity.
2. Verify user has autherization for folders.
3. Open Active Directory Users and Computers.
4. Verify user is in the correct OU.
5. Verify group policy is active.
6. Verify user is added to the correct security groups.
7. Re-check acces to shared folder.
8. Verify user can access shared folders.
9. Document the ticket.
10. Close the request.

### Access denied

Severity: Medium
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Clear local caches.
3. Sign out and re-sign in.
4. Verify network connection.
5. Open Active Directory Users and Computers.
6. Verify user is in the correct OU.
7. Verify group policy is active.
8. Verify user is added to the correct security groups.
9. Verify account is not locked, expired or pending password change.
10. Document ticket
11. Close request.

### Mapped Drive Missing

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify mapped drive is not present.
2. Verify network connection.
3. Press Win+R, then type the UNC path directly.
4. Restart workstation.
5. Verify user has access to mapped drive.
6. Document the ticket.
7. Close the request.

### Folder permissions incorrect

Serverity: Low
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Open Active Directory Users and Computers.
3. Verify user is in the correct OU.
4. Verify group policy is active.
5. Verify user is added to the correct security groups.
6. Document ticket.
7. Close request.

### Drive mapping GPO failure

Serverity: High
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Run ```cmd gpupdate /force```
3. Open Win+R \\ServerName\ShareName.
4. Run ```cmd gpresult /h C;\temp\gpreport.html```
5. Open generated gpreport.html
6. Check if Group Policy object is under "Applied GPOs".
7. Open Event Viewer.
8. Open Applications and Service Logs -> Microsoft -> Windows -> GroupPolicy -> Operational.
9. Search for Event Id 4098.
10. Open Group Policy Management Editor.
11. Open User Configuration -> Preferences -> Windows Settings -> Drive Maps.
12. Change actione from Update to Replace.
13. Open Windows Credentials, delete any cached credentials pointing to the file server.
14. Run ```cmd ipconfig /flushdns```
15. Run ```cmd nbtstat -RR```
16. Document ticket.
17. Close request.

### Slow file access

Serverity: Medium
Estimated Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Restart Windows Explorer.
3. Uncheck "Show recently used files".
4. Disonnect unused or disconneted network drives.
5. Temporarily disable the Windows Search indexing service.
6. Ping server.
7. Update the Network Interface Card (NIC) drivers.
8. Monitor AVG. Disk Queue Length counter on the server.
9. Document ticket.
10. Close request.

### File Locked by Another User

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Ask the user to close the file.
3. Verify whether another user currently has the file open.
4. Open Computer Management.
5. Navigate to: System Tools -> Shared Folders -> Open Files
6. Locate the file.
7. Notify the user before forcibly closing the session.
8. Close the open file if approved.
9. Verify the user can reopen the file.
10. Document the ticket.
11. Close the request.

### Staorge full

Serverity: Medium
Estiamted Resolution: 15-30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Open Settings -> System -> Storage.
3. Delete temporary files.
4. Clear the Recycle Bin.
5. Uninstall unused applications.
6. Document ticket.
7. Close request.

---

## PowerShell Commands

```powershell
Get-SmbShare

Get-SmbShareAccess

Get-Acl "\\DC01\Shared"

New-SmbShare

Grant-SmbShareAccess

icacls

net use

Get-SmbOpenFile

Close-SmbOpenFile

Get-Volume

Get-PSDrive
```

---

## Monitoring & Health Checks

Verify:
- SMB share availability
- NTFS permissions
- Share permissions
- Free disk space
- Open files
- Audit logs
- Failed access attempts
- Drive mappings
- Backup status
- Client connectivity

Review monthly:
- Stale folders
- Inactive shares
- Permission changes
- Storage utilization

---

## Backup Requirements

Before major file-service changes:

- Verify backups completed successfully.
- Verify snapshots exist.
- Export share configuration.
- Document rollback procedures.
- Obtain change approval.

Backup commands: ```powershell Get-SmbShare wbadmin get versions```

---

## Future Improvements

- Dedicated file server (FS01)
- DFS namespaces
- DFS replication
- File Server Resource Manager (FSRM)
- Storage quotas
- Shadow Copies
- Azure Files integration
- Microsoft Sentinel integration
- Wazuh monitoring
- Automated permission auditing

---

## Related Documentation

- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-004 Server Inventory
- NWT-ENT-006 Enterprise Naming Standards
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Backup & Recovery Plan
- NWT-ENT-010 Disaster Recovery Plan
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard
- NWT-STD-008 Security Configuration Standard
- NWT-SOP-001 Active Directory Administration SOP

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
