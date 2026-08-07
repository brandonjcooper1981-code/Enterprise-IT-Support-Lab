# Desktop Configuration GPO

---

## Property Table

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Policy Configuration Document |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document defines the standard desktop configuration enforced through Group Policy Objects (GPOs) across Northwind Technologies workstations. The policy establishes a consistent user experience, improves workstation security, reduces administrative overhead, and simplifies support operations.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Policy Objectives

- Standardize workstation configuration
- Improve user experience
- Reduce Help Desk tickets
- Improve security
- Centralize management
- Simplify onboarding

---

## GPO Information

| Policy | Target |
|---------|--------|
| GPO-Desktop-Configuration | All Workstations |
| GPO-Desktop-Restrictions | Standard Users |

---

## Standard Desktop Configuration

| Setting | Standard |
|---------|----------|
| Desktop Background | Northwind Standard Wallpaper |
| Start Menu Layout | Standard |
| Taskbar | Standard |
| Recycle Bin | Visible |
| This PC | Visible |
| Control Panel | Restricted |
| File Explorer | Open to This PC |
| Hidden Files | Disabled |
| File Extensions | Enabled |
| Windows Search | Enabled |

---

## Administrative Templates

User Configuration
    → Policies
        → Administrative Templates

Administrative Templates Included:
• Control Panel
• Desktop
• Start Menu and Taskbar
• File Explorer
• Windows Components
• System

---

## Desktop Restrictions

- Prevent users from changing the desktop wallpaper.
- Prevent access to Control Panel.
- Disable Registry editing tools.
- Disable Command Prompt where required.
- Restrict access to the Run dialog.
- Prevent modification of network settings.

---

## Standard User Experience

| Setting | Standard |
|---------|----------|
| Desktop Wallpaper | Northwind Company Wallpaper |
| Screen Saver | Company Standard |
| Screen Timeout | 15 Minutes |
| Drive Mapping | Department Shares |
| Printers | Automatically Assigned |
| Desktop Shortcuts | Standard |
| Taskbar Layout | Standard Corporate Layout |

---

## Security Settings

- Prevent unauthorized desktop modifications.
- Standardize workstation configuration.
- Reduce malware exposure.
- Enforce least-privilege principles.
- Support organizational security compliance.

---

## Validation

- Desktop matches company standard
- Wallpaper applied
- Start menu configured
- Restrictions enforced
- GPUpdate successful
- User receives the correct desktop configuration after logon.

---

## Troubleshooting

| Issue | Resolution |
|---------|------------|
| Wallpaper missing | gpupdate /force |
| Icons missing | Verify GPO |
| Settings editable | Check inheritance |
| Wrong desktop | Review OU |
| GPO not applying | gpresult /r |

---

## Useful Commands

```powershell
gpupdate /force

gpresult /r

gpresult /h report.html

Get-GPO -All

Get-GPResultantSetOfPolicy -ReportType Html -Path C:\GPReport.html
```

---

## Related Documentation
- Desktop-Lock-GPO.md
- Drive-Mapping-GPO.md
- GPO-Standards.md
- OU-Design.md
- Password-Policy-GPO.md
- User-Standards.md

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
