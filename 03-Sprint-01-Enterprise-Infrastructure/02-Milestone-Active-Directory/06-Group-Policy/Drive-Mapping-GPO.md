# Drive Mapping GPO

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Policy Configuration Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the network drive mapping policies enforced through Group Policy Objects (GPOs) within the Northwind Technologies environment.

These policies provide users with consistent access to departmental resources, simplify workstation configuration, and support centralized access management.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Policy Objectives

Northwind Technologies enforces drive mapping policies to:

- Standardize access to shared resources.
- Reduce manual workstation configuration.
- Simplify onboarding procedures.
- Enforce role-based access control.
- Improve user productivity.
- Centralize file-share management.

---

## GPO Information

| Policy Name | Target |
|--------------|----------|
| GPO-HR-Drive-Mapping | HR OU |
| GPO-Finance-Drive-Mapping | Finance OU |
| GPO-IT-Drive-Mapping | IT OU |
| GPO-Engineering-Drive-Mapping | Engineering OU |

---

## Standard Drive Mappings

| Drive Letter | Share | Department |
|--------------|--------|-------------|
| H: | \\FS01\HR | Human Resources |
| F: | \\FS01\Finance | Finance |
| I: | \\FS01\IT | Information Technology |
| E: | \\FS01\Engineering | Engineering |
| M: | \\FS01\Marketing | Marketing |
| O: | \\FS01\Operations | Operations |
| S: | \\FS01\Sales | Sales |

---

## GPO Location

lab.local
├── HR
│   └── GPO-HR-Drive-Mapping
├── Finance
│   └── GPO-Finance-Drive-Mapping
├── IT
│   └── GPO-IT-Drive-Mapping
├── Engineering
│   └── GPO-Engineering-Drive-Mapping
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

Navigate to:
Forest: lab.local
    → Domains
        → lab.local
            → IT
                → GPO-IT-Drive-Mapping

Configure:
User Configuration
    → Preferences
        → Windows Settings
            → Drive Maps

---

## Standard Settings

Configure:
- Action: Update
- Location: \\FS01\IT
- Label as: IT Shared Drive
- Drive Letter: I:
- Reconnect: Enabled
- Run in logged-on user's security context.

---

## Security Filtering

Drive mappings should be applied using:
- Organizational Units (preferred).
- Security groups.
- Item-level targeting when required.
- Least-privilege principles.

---

## Validation

Verify:
- Drive appears in File Explorer.
- Users can access authorized folders.
- Unauthorized users are denied access.
- Group Policy applies successfully.
- `gpupdate /force` completes successfully.

---

## Troubleshooting

| Issue | Resolution |
|--------|--------|
| Drive does not appear | Run `gpupdate /force` |
| Access denied | Verify NTFS permissions |
| Wrong drive letter | Review GPO settings |
| Drive maps incorrectly | Verify OU membership |
| GPO not applying | Check security filtering |

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
net use
```

```powershell
Get-SmbShare
```

---

## Related Documentation

- Group-Standards.md
- Group-Membership-Procedure.md
- User-Creation-Procedure.md
- OU-Design.md
- Desktop-Lock-GPO.md
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
