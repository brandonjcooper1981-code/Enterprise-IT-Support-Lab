# NWT-RUN-003 Domain Join Failure

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Runbook ID | NWT-RUN-003 |
| Severity | High |
| Estimated Resolution | 15–30 minutes |
| Escalation Team | Infrastructure |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve workstation failures when joining systems to the Northwind Technologies Active Directory domain.

---

## Symptoms

- "The specified domain either does not exist or could not be contacted."
- "An Active Directory Domain Controller could not be contacted."
- Domain join wizard fails.
- User cannot authenticate with domain credentials.
- DNS resolution failures.
- Computer account creation fails.

---

## Systems Affected

- DC01
- CLIENT01
- Active Directory
- DNS Server
- DHCP Server
- northwind.local
- Windows 11 workstations

---

## Investigation

1. Verify user identity using approved methods.
2. Verify workstation network connectivity.
3. Verify IP configuration: ```powershell ipconfig /all```
4. Verify DNS server settings.
5. Ping the domain controller: ```powershell ping DC01```
6. Test domain name resolution: ```powershell nslookup northwind.local```
7. Verify time synchronization.
8. Verify the computer object does not already exist in Active Directory.
9. Review Event Viewer logs.
10. Verify the workstaton time is synchronized: ``` powershell w32tm /query /status```

---

## Resolution

1. Open: Settings → System → About → Domain or Workgroup
2. Verify DNS points to DC01.
3. Remove any stale computer account from Active Directory.
4. Restart the workstation.
5. Retry domain join.
6. Run: ```powershell gpupdate /force```
7. Verify secure channel: ```powershell nltest /sc_verify:northwind.local```
8. Restart workstation if required.

---

## Validation

- Workstation joins the domain.
- Computer object appears in Active Directory.
- User can authenticate.
- Group Policy applies successfully.
- DNS resolves correctly.

---

## Escalation Criteria

Escalate if:
- DNS errors persist.
- Domain controller is unavailable.
- Multiple systems cannot join the domain.
- Replication errors exist.
- Group Policy fails after successful join.

---

## Key Event IDs

| Event ID | Description |
|-----------|-----------|
| 1058 | Group Polciy proccessing failed |
| 1129 | Domain controller unavailable during startup |
| 5719 | Domain controller unavailable |
| 5722 | Secure channel failure |
| 4624 | Successful logon |
| 4625 | Failed logon |
| 40960 | Authentication error |
| 40961 | Kerberos error |

---

## Common Commands

```powershell
ipconfig /all

ipconfig /flushdns

ipconfig /registerdns

ping DC01

nslookup northwind.local

gpupdate /force

nltest /sc_verify:northwind.local

w32tm /query /status

netdom verify CLIENT01

Test-NetConnection DC01 -Port 53

Test-NetConnection DC01 -Port 88

whoami

hostname
```

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-004 DHCP Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-RUN-001 User Account Lockout
- NWT-RUN-002 Password Reset

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
