# GPO Standards

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Standards Document |
| Status | In Progress |
| Version | 1.0 |

---

## Purpose

This document defines the standards used to create, manage, and maintain Group Policy Objects (GPOs) within the Northwind Technologies environment.

These standards ensure consistent policy deployment, simplify administration, and support enterprise security requirements.

---

## Environment Note

**Note**

The current implementation environment uses the `lab.local` Active Directory domain. References to `northwind.local` throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## GPO Design Goals

Northwind Technologies designs Group Policy to:
- Enforce security standards.
- Centralize configuration management.
- Simplify desktop administration.
- Reduce manual configuration.
- Support future growth.
- Apply the principle of least privilege.

---

## GPO Naming Standards

### Naming Format

Northwind Technologies uses the following naming convention:

```text
GPO-<Department>-<Purpose>
```

Examples:

| Group Policy Object | Purpose |
|---------------------|----------|
| GPO-Domain-Password-Policy | Password requirements |
| GPO-IT-Desktop-Config | IT workstation settings |
| GPO-HR-Drive-Mapping | Shared drive mappings |
| GPO-HelpDesk-Screen-Lock | Screen lock policy |
| GPO-Security-Audit-Policy | Logging and auditing |

---

## Group Policy Categories

| Category | Purpose |
|----------|----------|
| Security | Passwords, lockout, auditing |
| Desktop | Wallpapers, taskbar, screen saver |
| Network | Drive mappings and printers |
| Administrative | Windows settings |
| Software | Application deployment |
| Compliance | Security baselines |

---

## GPO Linking Standards

Group Policy Objects should be linked to the most specific Organizational Unit possible.

Hierarchy:
```text
lab.local
├── Domain Policies
├── HR
├── Finance
├── IT
├── Engineering
├── Marketing
├── Operations
├── Sales
└── Executive
```

Standards:
- Avoid linking policies at the domain level unless required.
- Link policies to departmental OUs whenever possible.
- Separate user policies from computer policies.
- Minimize inheritance blocking.
- Use security filtering only when necessary.

---

## Security Standards

Northwind Technologies follows these security principles:
- Least privilege.
- Separation of duties.
- Centralized management.
- Documented approvals.
- Change tracking.
- Regular policy reviews.

---

## Change Management

Before deploying a new Group Policy Object:
- Verify business requirements.
- Test in a lab environment.
- Document the change.
- Obtain approval.
- Validate policy application.

After deployment:
- Monitor affected systems.
- Verify policy functionality.
- Update documentation.
- Record rollback procedures.

---

## Standard Group Policies

| Policy | Target |
|----------|----------|
| Password Policy | Domain |
| Account Lockout Policy | Domain |
| Screen Lock Policy | Users |
| Desktop Restrictions | Users |
| Drive Mapping Policy | Department OUs |
| Windows Firewall | Computers |
| Audit Policy | Servers |
| Power Settings | Workstations |
| Folder Redirection | Department Ous |

---

## Validation

Verify:
- GPO names follow standards.
- Policies are linked to the correct OU.
- Security filtering is correct.
- Policies apply successfully.
- Documentation is complete.
- No conflicting policies exist.

---

## Troubleshooting

| Issue | Resolution |
|----------|----------|
| Policy does not apply | Run `gpupdate /force` |
| Incorrect settings applied | Check inheritance |
| User missing policy | Verify OU membership |
| Conflicting settings | Review GPO precedence |
| Slow logon | Review startup policies |

---

## Useful Commands

```powershell
gpupdate /force

gpresult /r

gpresult /h report.html

Get-GPO -All

Get-GPInheritance -Target "OU=IT,DC=lab,DC=local"

Get-GPResultantSetOfPolicy
```

---

## Related Documentation

- OU-Design.md
- User-Standards.md
- Group-Standards.md
- User-Creation-Procedure.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md
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
