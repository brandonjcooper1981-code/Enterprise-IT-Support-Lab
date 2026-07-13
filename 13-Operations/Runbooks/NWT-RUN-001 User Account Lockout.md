# NWT-RUN-001 User Account Lockout

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Runbook ID | NWT-RUN-001 |
| Severity | Medium |
| Estimated Resolution | 15–30 minutes |
| Escalation Team | Infrastructure |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve user account lockouts within the Northwind Technologies environment.

---

## Symptoms

- User cannot log in.
- "Account locked out" message.
- Multiple failed sign-in attempts.
- VPN authentication failure.

---

## Systems Affected

- DC01
- Active Directory
- Windows 11 clients
- northwind.local

---

## Investigation

1. Verify user identity.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Verify account status.
5. Review recent failed login attempts.
6. Check Event Viewer on DC01.
7. Review account lockout events: ```powershell Event ID: 4740```

---

## Resolution

1. Unlock account.
2. Reset password if required.
3. Verify no devices are repeatedly attempting authentication:
   1. Cached workstation credentials
   2. Mobile devices
   3. VPN clients
   4. Outlook
   5. Saved RDP sessions
4. Run: ```powershell gpupdate /force```
5. Test login.
6. Verify access to mapped drives and email.

---

## Validation

- User successfully logs in.
- Account is unlocked.
- Mapped drives connect.
- Email functions normally.
- No new lockout events appear.

---

## Escalation Criteria

Escalate if:
- Lockout reoccurs.
- Domain controller errors exist.
- Multiple users are affected.

---

## Key Event IDs

| Event ID | Description |
|-----------|-----------|
| 4740 | User account locked |
| 4625 | Failed logon |
| 4624 | Successful logon |
| 4767 | Account unlocked |

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP

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
