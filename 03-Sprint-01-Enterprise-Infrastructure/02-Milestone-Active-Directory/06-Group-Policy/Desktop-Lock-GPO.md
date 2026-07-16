# Desktop Lock GPO

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Policy Configuration Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the desktop lock and screen saver policies enforced through Group Policy Objects (GPOs) within the Northwind Technologies environment.

These policies protect unattended workstations, reduce unauthorized access, and support company security requirements.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Policy Objectives

Northwind Technologies enforces desktop lock policies to:

- Protect unattended systems.
- Reduce unauthorized access.
- Enforce workstation security.
- Standardize desktop behavior.
- Support security compliance.
- Promote good security practices.

---

## GPO Information

| Policy Name | Target |
|----------|----------|
| GPO-HelpDesk-Screen-Lock | IT OU |

---

## Policy Settings

| Setting | Standard |
|----------|----------|
| Enable Screen Saver | Enabled |
| Password Protect Screen Saver | Enabled |
| Screen Saver Timeout | 900 seconds (15 minutes) |
| Allow User Changes | Disabled |

---

## GPO Location

lab.local
├── HR
├── Finance
├── IT
│   └── GPO-HelpDesk-Screen-Lock
├── Engineering
├── Marketing
├── Operations
├── Sales
└── Executive

---

## Configuration Path

Open:
Server Manager
    → Tools
        → Group Policy Management

Forest: lab.local
    → Domains
        → lab.local
            → IT
                → GPO-HelpDesk-Screen-Lock

User Configuration
    → Policies
        → Administrative Templates
            → Control Panel
                → Personalization


---

## Standard Settings

Enable:
- Enable screen saver.
- Password protect the screen saver.
- Force a specific screen saver: scrnsave.scr.
- Set inactivity timeout.

Disable:
- Users changing screen saver settings.

---

## Security Standards

Northwind Technologies follows these principles:
- Least privilege.
- Workstation security.
- Protection of unattended devices.
- Standardized user experience.
- Regulatory compliance.

---

## Validation

Verify:

- Screen saver activates after inactivity.
- Users must enter credentials to unlock.
- Group Policy applies successfully.
- User settings cannot be modified.
- `gpupdate /force` completes successfully.

---

## Troubleshooting

| Issue | Resolution |
|----------|----------|
| Screen saver does not activate | Run `gpupdate /force` |
| Policy not applied | Verify OU membership |
| Users can change settings | Review GPO settings |
| Wrong timeout value | Check policy precedence |
| Screen remains unlocked | Verify password protection |

---

## Useful Commands

```powershell
gpupdate /force
```

```powershell
gpresult /r
```

```powershell
gpresult /h report.html
```

```powershell
Get-GPO -All
```

```powershell
gpresult /h report.html
```

---

## Related Documentation

- GPO-Standards.md
- Password-Policy-GPO.md
- User-Standards.md
- Group-Standards.md
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


