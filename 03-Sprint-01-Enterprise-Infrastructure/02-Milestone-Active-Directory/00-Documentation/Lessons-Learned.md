# Lessones Learned

| Property | Value |
|----------|--------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Project Retrospective |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document captures the key technical and operational lessons learned during the deployment of the Northwind Technologies Active Directory environment.
The objective is to document successful practices, challenges encountered, troubleshooting techniques, and recommendations for future deployments.

---

## Environment Note

Note:
The current implementation environment uses the lab.local Active Directory domain. References to northwind.local throughout Northwind Technologies documentation represent the planned production naming standard and future enterprise environment.

---

## Project Objectives

Milestone 2 sucesfully demonstrated:
- Active Directory deployment
- Organizational Unit design
- User administration
- Group administration
- Group Policy deployment
- Desktop standardization
- Drive mapping
- Enterprise documentation
- PowerShell administration

---

## What Went Well

- Windows Server installation completed successfully.
- Active Directory Domain Services installed without issues.
- DNS integrated correctly.
- Organizational Units designed logically.
- Department users created successfully.
- Security Groups implemented using AGDLP principles.
- Desktop Configuration GPO deployed successfully.
- Desktop Lock GPO validated.
- Drive Mapping GPO functioned correctly.
- Enterprise documentation remained consistent across all documents.

---

## Technical Challenges

### Challenge 1 — Virtual Machine Configuration

Issue:
- Initial VirtualBox networking configuration required adjustments before domain communication functioned correctly.

Resolution:
- Verified Host-Only Adapter
- Verified NAT Adapter
- Corrected IP configuration
- Confirmed DNS settings

Lesson Learned:
- Always verify networking before troubleshooting Active Directory.

### Challenge 2 — DNS Configuration

Issue:
- Clients were unable to locate the Domain Controller until DNS settings were corrected.

Resolution:
- Pointed client DNS to the Domain Controller.
- Flushed DNS cache.
- Verified name resolution.

Lesson Learned:
- DNS is the foundation of Active Directory.

### Challenge 3 — Group Policy

Issue:
- Policies did not immediately apply.

Resolution:
- gpupdate /force

Verified with:
- gpresult /r

Lesson Learned:
- Always verify GPO inheritance before troubleshooting policy settings.

### Challenge 4 — File Share Permissions

Issue:
- Inheritance caused unexpected access permissions.

Resolution:
- Disabled inheritance where appropriate.
- Assigned Security Groups.
- Tested with standard user accounts.

Lesson Learned:
- Use Security Groups instead of assigning permissions directly to users.

### Challenge 5 — Documentation

Issue:
- Documentation became difficult to navigate as the project expanded.

Resolution:
- Standardized document templates.
- Organized folders.
- Added cross-references.
- Created consistent naming standards.

Lesson Learned:
- Documentation should evolve alongside the environment.

---

## Best Practices Identified

Northwind Technologies recommends:
- Plan OU structure before deployment.
- Standardize naming conventions.
- Use Security Groups.
- Follow AGDLP methodology.
- Document every configuration change.
- Validate each deployment stage.
- Test with standard user accounts.
- Keep Group Policies modular.
- Use least privilege.
- Automate repetitive administrative tasks.

---

## Frequently Used Administrative Commands

```powershell
gpupdate /force
```

```powershell
gpresult /r
```

```powershell
dcdiag
```

```powershell
Get-ADUser -Filter *
```

```powershell
Get-ADGroup -Filter *
```

```powershell
Get-ADOrganizationalUnit -Filter *
```

```powershell
Resolve-DnsName lab.local
```

```powershell
ipconfig /all
```

---

## Skills Developed

During this milestone the following technical skills were strengthened:
- Windows Server Administration
- Active Directory Administration
- Organizational Unit Design
- User Management
- Security Group Design
- Group Policy Management
- DNS Administration
- PowerShell
- Documentation Standards
- Enterprise Change Management
- Troubleshooting Methodology

---

## Professional Competencies Strengthened

During this milestone the following professional practices were reinforced:
- Enterprise documentation
- Technical troubleshooting
- Change management
- Configuration management
- Problem analysis
- Systems thinking
- Root cause analysis
- IT operations planning

---

## Recommendations for Future Milestones

Future improvements include:
- Multiple Domain Controllers
- Active Directory replication
- DFS Namespaces
- Certificate Services
- Windows Deployment Services
- Microsoft Entra ID integration
- Azure AD Connect
- PKI implementation
- LAPS deployment
- Advanced GPO security filtering

---

## Overall Project Outcome

The Active Directory deployment achieved all planned objectives for Milestone 2.

The environment now includes:
- Functional Active Directory Domain
- Departmental Organizational Units
- Enterprise User Accounts
- Security Groups
- Standardized Group Policies
- Desktop Configuration
- Drive Mapping
- Enterprise Documentation
The completed environment provides a scalable foundation for future enterprise infrastructure projects.

The successful completion of Milestone 2 establishes the enterprise identity infrastructure required for future Northwind Technologies projects, including Microsoft 365 integration, centralized patch management, enterprise monitoring, certificate services, security operations, and cloud identity synchronization.

---

## Related Documentation

- Active-Directory-Design.md
- OU-Design.md
- Group-Design.md
- Validation-Checklist.md
- Implementation-Steps.md
- Password-Policy-GPO.md
- Desktop-Lock-GPO.md
- Desktop-Configuration-GPO.md
- Drive-Mapping-GPO.md

---

## Approval

**Approved By**

Michael Wilson

Chief Information Officer (CIO)

**Prepared By**

Brandon J. Cooper

**Department**

Information Technology Services (ITS)

---

## Revision History

| Version | Date | Author | Description |
|----------|----------|----------|----------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial release |

---

**Questions or Updates?**

Please submit documentation corrections through the Northwind Technologies Information Technology Services documentation review process.

---

____________________________________

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Innovate • Secure • Support

© 2026 Northwind Technologies

