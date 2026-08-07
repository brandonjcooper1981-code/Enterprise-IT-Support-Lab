# Password Policy GPO

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Policy Configuration Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the standard password and account lockout policies enforced through Group Policy Objects (GPOs) within the Northwind Technologies environment.

These policies strengthen account security, reduce unauthorized access, and support enterprise security requirements.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Policy Objectives

Northwind Technologies enforces password policies to:
- Protect user accounts.
- Reduce unauthorized access.
- Enforce password complexity.
- Minimize brute-force attacks.
- Support regulatory and security requirements.
- Standardize account management.

---

## Password Standards

| Setting | Standard |
|----------|----------|
| Minimum Password Length | 12 characters |
| Password Complexity | Enabled |
| Password History | 24 passwords |
| Maximum Password Age | 90 days |
| Minimum Password Age | 1 day |
| Reversible Encryption | Disabled |

---

## Account Lockout Standards

| Setting | Standard |
|----------|----------|
| Account Lockout Threshold | 5 failed attempts |
| Lockout Duration | 15 minutes |
| Reset Counter After | 15 minutes |

---

## GPO Information

| Policy Name | Target |
|----------|----------|
| GPO-Domain-Password-Policy | Domain |
| GPO-Domain-Account-Lockout | Domain |

---

lab.local
└── Group Policy Objects
    ├── GPO-Domain-Password-Policy
    └── GPO-Domain-Account-Lockout

---

## Configuration Path

Open:
Server Manager
    → Tools
        → Group Policy Management
Navigate to:
Forest: lab.local
    → Domains
        → lab.local
            → Default Domain Policy
Confiure:
Computer Configuration
    → Policies
        → Windows Settings
            → Security Settings
                → Account Policies
                    ├── Password Policy
                    └── Account Lockout Policy

---

## Standard Settings

### Password Policy

- Enforce password history.
- Set minimum password length.
- Enable complexity requirements.
- Configure maximum password age.
- Disable reversible encryption.

### Account Lockout Policy

- Configure lockout threshold.
- Configure lockout duration.
- Configure reset timer.

---

## Validation

Verify:
- Password complexity is enforced.
- Weak passwords are rejected.
- Account lockout functions correctly.
- Domain users receive policy updates.
- `gpupdate /force` completes successfully.
- `Get-ADDefaultDomainPasswordPolicy` returns the expected settings.

---

## Exception Handling

- Service accounts may require alternate password policies.
- Exception requests require ITS approval.
- Exceptions must be documented.
- Exception reviews occur annually.

---

## Troubleshooting

| Issue | Resolution |
|----------|----------|
| Password accepted unexpectedly | Review complexity settings |
| Account does not lock | Verify threshold values |
| Policy does not apply | Run `gpupdate /force` |
| Settings conflict | Review GPO precedence |
| User receives old settings | Check replication |

---

## Useful Commands

```powershell
gpupdate /force
```

```powershell
gpresult /r
```

```powershell
net accounts
```

```powershell
Get-ADDefaultDomainPasswordPolicy
```

---

## Related Documentation

- User-Standards.md
- User-Creation-Procedure.md
- GPO-Standards.md
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



