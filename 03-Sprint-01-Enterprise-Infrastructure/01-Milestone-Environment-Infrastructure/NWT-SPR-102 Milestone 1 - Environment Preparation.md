| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SPR-102 |
| **Document Type** | Milestone Documentation |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | June 2026 |

# NWT-SPR-102 Milestone 1 – Environment Preparation

*Enterprise IT Modernization Project*

---

# Executive Summary

Milestone 1 establishes the virtual infrastructure required to support the Northwind Technologies Enterprise IT Modernization Project.

This phase focuses on preparing a standardized deployment environment that provides the foundation for all subsequent infrastructure implementation activities, including Active Directory, enterprise networking, file services, and Help Desk operations.

---

# Project Snapshot

| Property | Value |
|----------|-------|
| Project | Enterprise IT Modernization Project |
| Sprint | Sprint 1 |
| Milestone | 1 |
| Phase | Environment Preparation |
| Project Lead | Brandon J. Cooper |
| Status | Complete |

---

# Business Impact

Establishing a standardized virtualization platform provided Northwind Technologies with a repeatable, isolated, and scalable environment for deploying enterprise infrastructure.

By investing in a consistent deployment environment before implementing production services, the organization reduced deployment risk, simplified troubleshooting, improved documentation accuracy, and created a reliable foundation for future infrastructure expansion.

This milestone ensures that all subsequent implementation activities are performed within a controlled and validated environment that reflects enterprise deployment practices.

---

# Business Need

Northwind Technologies required a dedicated enterprise infrastructure capable of supporting centralized identity management, network services, file services, and Help Desk operations.

Before production services could be deployed, a standardized virtualization platform needed to be designed, configured, and validated to ensure consistent system performance and repeatable implementation procedures.

Milestone 1 addresses these requirements by establishing the foundational infrastructure upon which all remaining Sprint 1 activities depend.

---

# Objectives

Milestone 1 was designed to accomplish the following objectives:

- Prepare the Oracle VirtualBox virtualization platform.
- Deploy Windows Server 2025.
- Deploy Windows 11 Enterprise.
- Deploy Ubuntu Server.
- Configure enterprise virtual networking.
- Assign standardized system names.
- Validate communication between systems.
- Prepare the environment for Active Directory deployment.

---

# Architecture References

This milestone supports the enterprise architecture defined in:

- NWT-ENT-001 Company Profile
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-003 Enterprise Network Diagram
- NWT-PM-001 Project Charter

---

# Implementation

1. Environment Planning

2. Oracle VirtualBox Configuration

3. Windows Server 2025 Deployment

4. Windows 11 Enterprise Deployment

5. Ubuntu Server Deployment

6. Virtual Network Configuration

7. Initial Connectivity Validation

8. Snapshot and Environment Baseline

---

# Validation

| Validation Test          | Result |
| ------------------------ | :----: |
| Windows Server Installed |    ✅   |
| Windows 11 Installed     |    ✅   |
| Ubuntu Installed         |    ✅   |
| Static IP Configured     |    ✅   |
| VM Communication         |    ✅   |

---

# Troubleshooting

VM wouldn't boot
Wrong adapter
ISO issue
Boot order
Guest Additions

---

# Lessons Learned

Plan networking before installing services.
Name systems consistently.
Validate after every major configuration.
Snapshots reduce recovery time.

---

# Project Metrics

| Metric              | Value |
| ------------------- | ----: |
| Virtual Machines    |     3 |
| Operating Systems   |     3 |
| Networks Configured |     2 |
| Validation Tests    |     7 |
| Issues Resolved     |     5 |

---

# Operational Readiness

| Component              | Status |
| ---------------------- | :----: |
| Virtual Infrastructure |    ✅   |
| Windows Server         |    ✅   |
| Windows Client         |    ✅   |
| Ubuntu Server          |    ✅   |
| Network Connectivity   |    ✅   |
| Ready for Milestone 2  |    ✅   |

| Question                                         | Status |
| ------------------------------------------------ | :----: |
| Were all milestone objectives completed?         |    ✅   |
| Were validation tests successful?                |    ✅   |
| Are known issues documented?                     |    ✅   |
| Is supporting documentation complete?            |    ✅   |
| Is the environment ready for the next milestone? |    ✅   |

## Operational Readiness Statement

Following successful implementation, validation, and documentation, Milestone 1 has been completed and approved for transition to Milestone 2 – Active Directory Infrastructure.

---

# Related Readiness

NWT-SPR-101

NWT-ENT-001

NWT-ENT-002

NWT-PM-001

NWT-STD-001

NWT-STD-002

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
| 1.0 | June 2026 | Brandon J. Cooper | Initial release |

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
