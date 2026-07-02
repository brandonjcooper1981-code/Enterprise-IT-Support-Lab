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

## Phase 1 – Environment Planning

The Enterprise IT Modernization Project began with the objective of building a realistic Help Desk environment. As planning progressed and additional enterprise services were introduced, the project naturally evolved into a fully functioning Information Technology Services (ITS) department for Northwind Technologies.

A virtualized infrastructure was selected to provide a flexible, scalable, and cost-effective deployment platform. Virtualization significantly reduced the need for additional physical hardware while minimizing space requirements, simplifying maintenance, and allowing the environment to be easily modified, tested, and restored throughout the implementation process. These advantages made virtualization the preferred solution for developing and validating the enterprise infrastructure.

During the planning phase, three core systems were identified as essential to the project:
Each virtual machine was assigned a clearly defined operational role to support the enterprise services planned for Sprint 1.

- **DC01** – Windows Server 2025 to provide enterprise infrastructure services including Active Directory, DNS, DHCP, file services, and centralized administration.
- **CLIENT01** – Windows 11 Enterprise workstation used for domain integration, end-user validation, policy testing, and troubleshooting activities.
- **Ubuntu Server** – Linux server hosting the osTicket Help Desk platform and supporting services.

Although each virtual machine was assigned an initial purpose during planning, the overall environment evolved throughout implementation as additional enterprise services, documentation standards, and operational requirements were identified. This iterative approach allowed the infrastructure to grow naturally while maintaining alignment with the goals of the Enterprise IT Modernization Project.

The primary objective of the planning phase remained consistent throughout the project: to build a realistic enterprise environment that accurately reflected the daily responsibilities of an Information Technology Services department while providing practical experience with enterprise infrastructure deployment, administration, troubleshooting, and documentation.

The environment established during this phase provided the standardized foundation required for the successful implementation of Active Directory, enterprise network services, file services, and Help Desk operations documented throughout the remaining Sprint 1 milestones.

## Phase 2 – Oracle VirtualBox Configuration

Oracle VirtualBox was selected as the virtualization platform for the Enterprise IT Modernization Project due to its familiarity, flexibility, and suitability for enterprise lab development. Having previously used Oracle VirtualBox throughout the NGT Academy training program, the platform provided a reliable foundation while allowing implementation efforts to focus on enterprise infrastructure rather than learning a new virtualization solution.

Before any virtual machines were deployed, the implementation environment required careful preparation. Installation media for Windows Server 2025, Windows 11 Enterprise, Ubuntu Server were downloaded and organized to ensure each operating system was readily available throughout the deployment process. In addition, sufficient host storage, processor resources, and memory allocations were verified to support multiple simultaneously running virtual machines.

Virtual machine resource allocation was planned to provide stable performance while remaining within the capabilities of the host workstation. Each virtual machine was initially assigned a minimum of 4 GB of memory, which provided sufficient performance for operating system installation, enterprise services, validation activities, and troubleshooting throughout Sprint 1.

Enterprise network communication was established through a standardized dual-adapter configuration for every virtual machine. Each system utilized:

- **Adapter 1:** NAT Network for Internet connectivity and software updates.
- **Adapter 2:** Host-Only Adapter to provide isolated communication between enterprise systems within the Northwind Technologies environment.

This configuration allowed the environment to maintain Internet access while simultaneously supporting secure internal communication between the domain controller, client workstation, Linux servers, and supporting enterprise services.

Several implementation challenges were encountered while preparing the virtualization platform. Initial deployment issues included incorrect virtual network adapter assignments, boot failures caused by improper virtual boot order configuration, and installation media that was either improperly attached or failed to mount correctly. Each issue was investigated, corrected, and validated before continuing with subsequent infrastructure deployment activities.

Completing the virtualization platform before installing enterprise services established a stable baseline for the remainder of Sprint 1. By validating the virtualization environment first, future troubleshooting efforts could focus on operating system and infrastructure configuration rather than underlying platform issues. This phased implementation strategy reduced deployment risk while improving consistency throughout the Enterprise IT Modernization Project.

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
