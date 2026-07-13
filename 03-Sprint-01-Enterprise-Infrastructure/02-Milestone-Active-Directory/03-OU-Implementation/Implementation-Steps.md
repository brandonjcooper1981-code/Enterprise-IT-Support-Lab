# OU Implementation Steps

## Objective

Create the Active Directory Organizational Unit structure for Northwind Technologies.

---

## Environment Note

> **Note**
>
> The current implementation environment uses the `lab.local`
> Active Directory domain. References to `northwind.local`
> throughout the Northwind Technologies documentation represent
> the planned enterprise naming standard and future production
> environment.

## Procedure

1. Open Active Directory Users and Computers.
2. Right-click the domain root (`lab.local`).
3. Select: `New > Organizational Unit`
4. Create infrastructure OUs:
   - Engineering
   - Executive
   - Finance
   - HR
   - IT
   - Marketing
   - Operations
   - Sales
   - Servers
   - Workstations
   - HelpDesk-Lab
5. Verify the Organizational Units appear under the domain.
6. Review OU permissions and inheritance settings.
7. Document the OU structure in: `02-OU-Design/`
8. Validate Group Policy targeting.

---

## Validation

- OUs appear in Active Directory.
- Objects can be placed in the correct locations.
- Group Policy can be linked successfully.

---

## Implementation Results

| OU | Status |
|-----|-----|
| Engineering | Complete |
| Executive | Complete |
| Finance | Complete |
| HR | Complete |
| IT | Complete |
| Marketing | Complete |
| Operations | Complete |
| Sales | Complete |
| Servers | Complete |
| Workstations | Complete |
| HelpDesk-Lab | Complete |

---

## Status

✅ Complete

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
