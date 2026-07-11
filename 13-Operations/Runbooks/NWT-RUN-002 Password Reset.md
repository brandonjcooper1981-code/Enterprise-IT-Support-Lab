# NWT-RUN-002 Password Reset

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Runbook ID | NWT-RUN-002 |
| Severity | Low |
| Estimated Resolution | 10–15 minutes |
| Escalation Team | Help Desk |

---

## Purpose

This runbook provides the procedures required to verify user identity, reset passwords, enforce password policy requirements, and restore access to Northwind Technologies systems.

---

## Symptoms

- User forgot password.
- User cannot sign in.
- Password expired.
- Account requires password reset.
- User receives "Incorrect password" errors.
- VPN authentication fails.

---

## Systems Affected

- DC01
- Active Directory
- Windows 11 clients
- northwind.local
- VPN services
- File shares
- Email services

---

## Investigation

1. Verify user identity using approved methods.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Verify account status.
5. Determine whether the account is locked.
6. Confirm password expiration status.
7. Review recent failed logon attempts.
8. Verify password policy requirements.

---

## Resolution

1. Open Active Directory Users and Computers.
2. Right-click the affected user.
3. Select **Reset Password**.
4. Enter a temporary password.
    - Password must meet complexity requirements.
5. Select:
    - User must change password at next logon.
6. Unlock the account if necessary.
7. Ask the user to sign in.
8.  Verify access to:
   - Email
   - File shares
   - VPN
   - Mapped drives

---

## Validation

- User successfully signs in.
- Password reset completed.
- User changes password successfully.
- Email functions normally.
- File shares connect.
- VPN authentication succeeds.

---

## Escalation Criteria

Escalate if:
- Password resets fail repeatedly.
- Account remains locked.
- Multiple users are affected.
- Domain controller errors exist.
- Password policy is not applying.

---

## Key Event IDs

| Event ID | Description |
|-----------|-----------|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4723 | Password change attempt |
| 4724 | Password reset |
| 4740 | Account locked |
| 4767 | Account unlocked |

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-RUN-001 User Account Lockout

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

