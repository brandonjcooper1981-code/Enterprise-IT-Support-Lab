| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SPR-101 |
| **Document Type** | Sprint Overview |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | June 2026 |

# NWT-SPR-101 Sprint 1 – Enterprise Infrastructure Deployment

*Enterprise IT Modernization Project*

---

# Executive Summary

This document serves as the authoritative overview for Sprint 1. All milestone documentation, validation reports, and implementation records reference this document for project scope, objectives, and success criteria.

Sprint 1 marks the initial implementation phase of the Northwind Technologies Enterprise IT Modernization Project. The primary objective of this sprint is to deploy the foundational infrastructure required to support centralized identity management, enterprise networking, file services, and Help Desk operations.

This sprint establishes the technical baseline for future phases by implementing a Windows Server domain environment, centralized network services, enterprise file sharing, and a service desk platform. All work performed during this sprint is documented in accordance with Northwind Technologies documentation standards and serves as the operational foundation for subsequent project phases.

---

# Document Purpose

This document serves as the authoritative planning and governance reference for Sprint 1 of the Enterprise IT Modernization Project.

It defines the business objectives, implementation strategy, project scope, success criteria, deliverables, dependencies, and governance requirements that guide all milestone activities completed during this sprint.

---

# Project Overview

The Enterprise Infrastructure Deployment sprint represents the first major implementation phase of the Enterprise IT Modernization Project.

The deployment focuses on establishing a secure, scalable, and maintainable infrastructure capable of supporting business operations across Northwind Technologies.

Core services deployed during this sprint include:

- Active Directory Domain Services
- DNS
- DHCP
- Enterprise File Services
- NTFS Permissions
- Windows 11 Domain Integration
- osTicket Help Desk
- Enterprise Documentation

---

# Business Value

Sprint 1 establishes the foundational infrastructure required for Northwind Technologies to standardize identity management, network services, enterprise file storage, and Help Desk operations.

Completing this sprint reduces administrative overhead, improves security, enables centralized management, and provides the technical platform required for future modernization initiatives.

---

# Project Objectives

The objectives of Sprint 1 are to:

- Deploy Windows Server 2025 infrastructure.
- Establish the **NORTHWIND.LOCAL** Active Directory domain.
- Configure enterprise DNS and DHCP services.
- Deploy centralized file services.
- Implement role-based access through Active Directory.
- Configure department file shares and NTFS permissions.
- Deploy the osTicket Help Desk platform.
- Validate all deployed infrastructure services.
- Produce enterprise-quality documentation.

---

# Project Scope

Sprint 1 includes the deployment, configuration, validation, and documentation of the following components:

- Virtual infrastructure
- Windows Server 2025
- Windows 11 Enterprise client
- Ubuntu Server
- Active Directory Domain Services
- DNS
- DHCP
- Organizational Units
- User Accounts
- Security Groups
- File Services
- NTFS Permissions
- osTicket
- Validation Testing
- Troubleshooting Documentation

Activities outside the scope of Sprint 1 include cloud services, Microsoft 365 integration, enterprise monitoring, automation expansion, and Security Operations Center (SOC) deployment.

---

# Project Snapshot

| Property | Value |
|----------|-------|
| Project | Enterprise IT Modernization Project |
| Sprint | Sprint 1 |
| Phase | Enterprise Infrastructure Deployment |
| Organization | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Project Lead | Brandon J. Cooper |
| Status | Complete |
| Related Architecture | NWT-ENT-002 |
| Related Charter | NWT-PM-001 |

---

# Milestone Overview

| Milestone | Description | Status |
|-----------|-------------|:------:|
| Milestone 1 | Environment Preparation | ✅ |
| Milestone 2 | Active Directory Infrastructure | ✅ |
| Milestone 3 | Enterprise Network Services | ✅ |
| Milestone 4 | Enterprise File Services | ✅ |
| Milestone 5 | Enterprise Help Desk Deployment | ✅ |
| Milestone 6 | Infrastructure Validation | ✅ |
| Milestone 7 | Project Retrospective & Lessons Learned | ✅ |

---

# Implementation Strategy

Sprint 1 follows a structured implementation methodology designed to minimize deployment risk while ensuring each infrastructure component is validated before proceeding to the next phase.

Implementation activities are organized into the following sequence:

1. Prepare the virtual environment.
2. Deploy Windows Server infrastructure.
3. Configure centralized identity services.
4. Implement enterprise network services.
5. Deploy enterprise file services.
6. Implement Help Desk services.
7. Perform validation testing.
8. Document troubleshooting activities.
9. Conduct project retrospective and capture lessons learned.

---

# Success Criteria

Sprint 1 will be considered successful when:

- Windows Server infrastructure is operational.
- NORTHWIND.LOCAL domain is functional.
- DNS and DHCP services are validated.
- CLIENT01 successfully joins the domain.
- Organizational Units, users, and security groups are configured.
- Department file shares function correctly.
- NTFS permissions enforce role-based access.
- osTicket is operational.
- Validation testing is successfully completed.
- Documentation complies with Northwind Technologies documentation standards.
- Enterprise documentation is finalized.

---

# Project Deliverables

The following deliverables are produced during Sprint 1:

- Enterprise Infrastructure
- Active Directory Environment
- DNS Configuration
- DHCP Configuration
- Enterprise File Services
- Help Desk Platform
- Validation Documentation
- Troubleshooting Documentation
- Sprint Documentation

---

# Dependencies

Sprint 1 depends upon the successful completion of:

- NWT-PM-001 Project Charter
- NWT-ENT-001 Company Profile
- NWT-ENT-002 Enterprise Architecture
- NWT-STD-001 Enterprise Documentation Standard
- NWT-STD-002 Markdown & Document Style Guide
- Oracle VirtualBox Virtualization Platform

---

# Risks

Potential implementation risks include:

| Risk                   | Mitigation                                         |
| ---------------------- | -------------------------------------------------- |
| Virtualization Issues  | Validate VM configuration prior to deployment      |
| DNS Misconfiguration   | Perform validation after each configuration change |
| Domain Join Failure    | Verify DNS and network configuration               |
| NTFS Permission Errors | Validate permissions using test accounts           |
| Documentation Drift    | Follow NWT-STD-001 and NWT-STD-002                 |

Each identified issue is documented and resolved through the Sprint 1 troubleshooting process.

---

# Architecture References

Sprint 1 aligns with the enterprise architecture defined in:

- NWT-ENT-001 Company Profile
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-003 Enterprise Network Diagram
- NWT-ENT-004 Server Inventory
- NWT-ENT-005 IP Address Plan

---

# Sprint Outcomes

Sprint 1 successfully established the foundational enterprise infrastructure required to support future modernization initiatives at Northwind Technologies.

Major accomplishments include:

- Active Directory deployment
- Enterprise DNS implementation
- DHCP deployment
- Centralized file services
- Departmental security groups
- NTFS permissions
- osTicket deployment
- Enterprise validation testing
- Operational documentation

Completion of Sprint 1 provides the operational foundation required to begin Sprint 2 – Enterprise Operations.

---

# Project Metrics

| Metric              | Planned | Actual |
| ------------------- | ------- | ------ |
| Milestones          | 7       | 7      |
| Validation Tests    | 15      | 17     |
| Screenshots         | 50      | 61     |
| Documentation Files | 10      | 12     |

---

# Related Documentation

Project Management
- NWT-PM-001 Project Charter
- NWT-002 Roadmap

Enterprise Documentation
- NWT-ENT-001 Company Profile
- NWT-ENT-002 Enterprise Architecture

Standards
- NWT-STD-001 Enterprise Documentation Standard
- NWT-STD-002 Markdown & Document Style Guide

---

# Approval

| Role        | Name                                                      |
| ----------- | --------------------------------------------------------- |
| Approved By | Michael Wilson, Chief Information Officer (CIO)           |
| Prepared By | Brandon J. Cooper, Enterprise Infrastructure Project Lead |
| Department  | Information Technology Services (ITS)                     |

---

# Revision History

| Version | Date | Author | Description |
|----------|------|--------|-------------|
| 1.0 | June 2026 | Brandon J. Cooper | Initial release |

---

# Questions or Updates?

This document is maintained as part of the Northwind Technologies Enterprise IT Support Lab.

Questions, corrections, or enhancement suggestions are documented through the Revision History section to ensure the documentation remains accurate and consistent across the project.

---

**Northwind Technologies**

**Information Technology Services (ITS)**

*Innovate • Secure • Support*

© 2026 Northwind Technologies

Enterprise IT Support Lab
