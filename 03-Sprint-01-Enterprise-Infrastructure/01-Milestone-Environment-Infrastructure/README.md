# Milestone 1 – Environment Infrastructure

**Company:** Northwind Technologies

**Department:** Information Technology Services (ITS)

**Sprint:** Sprint 1 – Enterprise Infrastructure Deployment

**Milestone:** 1 – Environment Infrastructure

**Classification:** Internal Use

**Status:** Approved

**Version:** 1.0

**Last Updated:** June 2026

---

# Overview

This engineering binder documents the deployment of the foundational virtualization environment supporting the Northwind Technologies Enterprise IT Modernization Project.

Milestone 1 establishes the infrastructure required for all subsequent Sprint 1 activities by deploying and validating the enterprise virtualization platform, operating systems, and supporting network configuration. The completed environment provides the stable foundation necessary for Active Directory, enterprise networking, file services, and Help Desk deployment.

Unlike the Sprint documentation, which describes the overall implementation strategy and business outcomes, this engineering binder contains the technical procedures, validation activities, troubleshooting guidance, and supporting documentation required to reproduce and maintain the environment.

---

# Quick Reference

| Item                     | Value                                  |
| ------------------------ | -------------------------------------- |
| **Estimated Build Time** | ~90 Minutes                            |
| **Difficulty**           | Intermediate                           |
| **Systems**              | DC01, CLIENT01, Ubuntu Server          |
| **Prerequisites**        | Oracle VirtualBox, Installation Media  |
| **Validation Required**  | Yes                                    |
| **Expected Outcome**     | Environment Ready for Active Directory |

---

# Objectives

This milestone accomplishes the following objectives:

- Deploy the enterprise virtualization platform.
- Install Windows Server 2025.
- Install Windows 11 Enterprise.
- Install Ubuntu Server.
- Configure initial virtual networking.
- Validate system communication.
- Document implementation procedures.
- Record troubleshooting activities.

---

# Engineering Documentation

| Document | Purpose |
|----------|---------|
| 01 – Oracle VirtualBox Configuration | Configure the enterprise virtualization platform. |
| 02 – Windows Server 2025 Installation | Deploy the enterprise server platform. |
| 03 – Windows 11 Enterprise Installation | Deploy the enterprise client workstation. |
| 04 – Ubuntu Server Installation | Deploy the Linux server supporting enterprise services. |
| 05 – Environment Validation | Verify infrastructure readiness before Active Directory deployment. |
| 06 – Troubleshooting | Document implementation issues and resolutions encountered during deployment. |

---

# Prerequisites

Before beginning this milestone, verify the following:

- Oracle VirtualBox installed
- Windows Server 2025 installation media
- Windows 11 Enterprise installation media
- Ubuntu Server installation media
- Host workstation meets virtualization requirements
- Sufficient storage, memory, and processor resources available

---

# Expected Outcome

Upon successful completion of this milestone:

- Virtual machines are operational.
- Windows Server is installed.
- Windows 11 Enterprise is installed.
- Ubuntu Server is installed.
- Network communication between systems is functioning.
- The environment is validated and ready for Active Directory deployment.

---

# Related Documentation

- NWT-SPR-101 Sprint 1 – Overview
- NWT-SPR-102 Sprint 1 – Enterprise Infrastructure Implementation
- NWT-ENT-002 Enterprise Architecture
- NWT-STD-001 Enterprise Documentation Standard
- NWT-STD-002 Markdown & Document Style Guide

---

# Milestone Status

**Status:** ✅ Complete

**Operational Readiness:** Approved

**Next Milestone:** Active Directory Domain Services

---

## Revision History

| Version | Date | Author | Description |
|----------|------|--------|-------------|
| 1.0 | June 2026 | Brandon J. Cooper | Initial release |

---

## Questions or Updates?

Questions, suggested improvements, and documentation corrections should be reviewed during the appropriate milestone review or sprint retrospective to maintain documentation accuracy and consistency.

---

**Northwind Technologies**

**Information Technology Services (ITS)**

**Enterprise IT Modernization Project**

*Innovate • Secure • Support*

© 2026 Northwind Technologies
