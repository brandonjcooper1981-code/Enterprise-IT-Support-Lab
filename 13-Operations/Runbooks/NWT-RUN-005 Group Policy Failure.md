# NWT-RUN-005 Group Policy Failure

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-005                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve Group Policy processing failures within the Northwind Technologies environment.

---

## Symptoms

- User settings are not applied.
- Desktop wallpaper or screensaver policy is missing.
- Network drives do not map automatically.
- Security settings are incorrect.
- Login scripts do not execute.
- User receives:
    - "Windows could not apply Group Policy."
    - "Failed to process Group Policy."
    - "The processing of Group Policy failed."

---

## Systems Affected

- DC01
- Active Directory
- Group Policy Management
- Windows 11 workstations
- DNS Server
- DHCP Server
- northwind.local

---

## Common Policies

| Policy               | Purpose                |
| -------------------- | ---------------------- |
| Drive Mapping        | Connect shared folders |
| Password Policy      | Security requirements  |
| Desktop Restrictions | User environment       |
| Security Baseline    | Security controls      |
| Login Scripts        | Automated actions      |
| Screensaver Policy   | Lock workstation       |

---

## Investigation

1. Verfiy user identity.
2. Confirm workstation network connectivity.
3. Verify DNS configuration: ```powershell ipconfig /all```
4. Verify domain connectivity: ```powershell ping DC01```
5. Check policy application: ``` powershell gpresult /r```
6. Generate a detailed report: ```powershell gpresult /h C:\gpreport.html```
7. Review Event Viewer:
    - Applications and Services Logs
        └── Microsoft
            └── Windows
                └── GroupPolicy
                    └── Operational
8. Verify the workstation appears in Active Directory.
9.  Confirm the user belongs to the correct security groups.

---

## Resolution

1. Force Group Policy refresh: ```powershell gpudate /force```
2. Log off and back on.
3. Reboot the workstation if necessary.
4. Verify SYVOL accessibility: ```powershell \\DC01\SYSVOL```
5. Verify NETLOGON accessibility: ```powershell \\DC01\NETLOGON```
6. Confirm GPO links in Group Policy Management.
7. Verify security filtering.
8. Check VMI filters if configured.
9. Reapply policies if required.

---

## Validation

- Group Policy updates successfully.
- Required drives appear.
- Security settings apply.
- Login scripts execute.
- User settings appear correctly.
- gpresult shows expected policies.
- No new GroupPolicy errors appear in Event Viewer.

---

## Escalation Criteria

Escalate if:
- Multiple users are affected.
- SYSVOL is unavailable.
- Domain controller replication fails.
- Security filtering is incorrect.
- DNS problems persist.
- Group Policy continues to fail after refresh.

---

## Key Event IDs

| Event ID | Description                     |
| -------- | ------------------------------- |
| 1058     | Group Policy processing failure |
| 1030     | Failed to obtain GPO            |
| 1129     | Domain controller unavailable   |
| 1502     | User policy failure             |
| 1503     | Computer policy failure         |
| 4624     | Successful logon                |
| 4625     | Failed logon                    |

---

## Common Commands

gpupdate /force

gpresult /r

gpresult /h C:\gpreport.html

ipconfig /all

ping DC01

nslookup northwind.local

whoami

whoami /groups

\\DC01\SYSVOL

\\DC01\NETLOGON

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-004 DHCP Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-RUN-003 Domain Join Failure
- NWT-RUN-004 Network Drive Missing

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
