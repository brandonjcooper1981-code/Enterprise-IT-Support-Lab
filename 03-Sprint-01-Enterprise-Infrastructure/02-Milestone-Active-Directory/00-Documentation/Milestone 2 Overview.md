# NWT-SPR-102 Sprint 2 Overview – Active Directory Infrastructure

| Property | Value |
|----------|----------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Sprint ID | NWT-SPR-102 |
| Sprint Name | Active Directory Infrastructure |
| Status | In Progress |
| Sprint Lead | Brandon J. Cooper |
| Executive Sponsor | Michael Wilson, Chief Information Officer (CIO) |
| Start Date | July 2026 |

---

## Executive Summary

Sprint 2 focuses on the deployment and validation of Northwind Technologies' Active Directory infrastructure. This sprint establishes the organization's identity and access management platform, enabling centralized administration of users, computers, security groups, Group Policy, DNS, DHCP, and enterprise authentication.

The objective is to build a scalable and maintainable directory services environment that supports current operations and future growth.

---

## Business Objectives

- Centralize user and computer management.
- Implement organizational units (OUs) aligned with business departments.
- Establish role-based access control using security groups.
- Deploy Group Policy for workstation configuration and security.
- Integrate DNS and DHCP services.
- Support enterprise file shares and authentication.
- Provide a foundation for future services, including print management and security monitoring.

---

## Sprint Scope

### Included

- Organizational Unit design.
- User account creation.
- Security group implementation.
- Active Directory administration.
- DNS configuration.
- DHCP configuration.
- Group Policy deployment.
- PowerShell automation.
- Validation testing.
- Documentation and evidence collection.

### Excluded

- Enterprise print services.
- Cloud identity integration.
- Email infrastructure.
- Disaster recovery automation.
- Production security operations.

---

## Deliverables

| Deliverable | Status |
|----------|----------|
| OU Structure | In Progress |
| User Accounts | In Progress |
| Security Groups | In Progress |
| DNS Services | Complete |
| DHCP Services | Complete |
| Group Policy Objects | In Progress |
| Validation Reports | Planned |
| Evidence Package | Planned |

---

## Success Criteria

Sprint 2 will be considered complete when:

- Users can authenticate successfully.
- Domain-joined computers receive Group Policy.
- DNS resolves internal resources.
- DHCP distributes valid network configurations.
- Security groups apply correct permissions.
- Shared drives function correctly.
- Validation tests pass.
- Documentation is finalized.

---

## Dependencies

Sprint 2 depends on the successful completion of:

- Milestone 1 – Environment Preparation
- Windows Server deployment
- VirtualBox networking configuration
- Domain Controller (DC01)
- CLIENT01 workstation deployment

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-004 DHCP Administration SOP
- NWT-RUN-003 Domain Join Failure
- NWT-RUN-005 Group Policy Failure
- NWT-RUN-006 Shared Drive Access Failure

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

