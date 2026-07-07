| Property           | Value                                 |
| ------------------ | ------------------------------------- |
| **Company**        | Northwind Technologies                |
| **Department**     | Information Technology Services (ITS) |
| **Document ID**    | NWT-ENT-002                           |
| **Document Type**  | Enterprise Architecture               |
| **Classification** | Internal Use                          |
| **Version**        | 1.0                                   |
| **Status**         | Approved                              |
| **Author**         | Brandon J. Cooper                     |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated**   | June 2026                             |

# NWT-ENT-002 Enterprise Architecture

*Northwind Technologies – Enterprise IT Modernization Project*

---

# Executive Summary

The Enterprise Architecture document defines the technical design, infrastructure standards, and operational architecture supporting Northwind Technologies.

The objective is to provide a secure, scalable, and maintainable enterprise environment that reflects the technologies, processes, and operational practices commonly found in a modern corporate IT department.

This architecture serves as the technical foundation for all implementation sprints documented within the Enterprise IT Support Lab.

---

# Enterprise Design Philosophy

Northwind Technologies follows a centralized enterprise architecture
designed around simplicity, repeatability, scalability, and operational
consistency.

Core architectural decisions prioritize standardized configurations,
centralized identity management, documentation-first engineering,
automation, and least-privilege security.

Every implementation sprint expands the enterprise without modifying the
core architectural foundation established during Sprint 1.

---

# Architecture Overview

The following diagram illustrates the high-level enterprise architecture supporting Northwind Technologies.

```text
                         Northwind Technologies
                                  │
                     Information Technology Services
                                  │
          ┌───────────────────────┴───────────────────────┐
          │                                               │
   Windows 11 Clients                              Ubuntu Server
 (Domain Joined Workstations)               (osTicket / Future Wazuh)
          │                                               │
          └───────────────────────┬───────────────────────┘
                                  │
                          NORTHWIND.LOCAL
                                  │
                                DC01
                Windows Server 2025 Domain Controller
                                  │
        ┌───────────────┬───────────────┬───────────────┐
        │               │               │               │
 Active Directory      DNS            DHCP       File Services
        │
        ├── Organizational Units
        ├── Security Groups
        ├── Users
        └── Group Policy

                                  │
                    Department Shared Resources

 Executive │ HR │ Finance │ Engineering │ IT │
 Marketing │ Sales │ Operations │ Public │ Software
```

The Enterprise Architecture serves as the technical blueprint for the Enterprise IT Support Lab and defines the relationship between infrastructure, identity management, network services, file services, automation, and operational support.

---

# Layered Enterprise Architecture

Business Layer
──────────────────────────
Executive
HR
Finance
Engineering
Sales
Marketing
Operations

───────────────

Application Layer
──────────────────────────
Active Directory
File Services
osTicket
PowerShell
GitHub

───────────────

Infrastructure Layer
──────────────────────────
DC01
Windows 11
Ubuntu
DNS
DHCP
NTFS
Group Policy

───────────────

Security Layer
──────────────────────────
Defender
Windows Firewall
Security Groups
Wazuh (Future)
Sysmon (Future)

---

# Enterprise Design Principles

Northwind Technologies follows the following enterprise architecture principles.

- Centralized Administration
- Standardization
- Least Privilege
- Security by Design
- Scalability
- High Availability (Future)
- Automation First
- Documentation First

---

# Technology Stack Summary

| Layer                | Technologies                                                                                  |
| -------------------- | --------------------------------------------------------------------------------------------- |
| **Business**         | Executive, HR, Finance, Engineering, Sales, Marketing, Operations                             |
| **Identity**         | Active Directory, Organizational Units, Security Groups, Group Policy                         |
| **Infrastructure**   | Windows Server 2025, Windows 11 Enterprise, Ubuntu Server, Oracle VirtualBox                  |
| **Network Services** | DNS, DHCP, IPv4, SMB File Services                                                            |
| **Operations**       | osTicket, PowerShell, GitHub Documentation                                                    |
| **Security**         | Microsoft Defender, Windows Firewall, NTFS Permissions, Wazuh *(Planned)*, Sysmon *(Planned)* |
| **Cloud (Future)**   | Microsoft Entra ID, Microsoft 365, Exchange Online, SharePoint Online, OneDrive               |

---

# Architecture Standards

| Standard        | Description                |
| --------------- | -------------------------- |
| Authentication  | Active Directory           |
| Authorization   | Security Groups            |
| Naming          | Enterprise Naming Standard |
| Documentation   | NWT-STD-001                |
| Permissions     | Least Privilege            |
| File Access     | NTFS + SMB                 |
| Automation      | PowerShell                 |
| Version Control | GitHub                     |

---

# Architecture Goals

The enterprise architecture has been designed to support the following objectives:

* Centralized identity management
* Secure authentication and authorization
* Reliable network services
* Standardized enterprise documentation
* Scalable file services
* Enterprise Help Desk operations
* Infrastructure automation
* Cybersecurity monitoring
* Future cloud integration

---

# Current Enterprise Environment

| Component               | Technology              |
| ----------------------- | ----------------------- |
| Hypervisor              | Oracle VirtualBox       |
| Domain                  | NORTHWIND.LOCAL         |
| Domain Controller       | DC01                    |
| Client Operating System | Windows 11 Enterprise   |
| Linux Server            | Ubuntu Server 24.04 LTS |
| Help Desk               | osTicket                |
| Documentation           | Markdown / GitHub       |
| Automation              | PowerShell              |
| Version Control         | GitHub                  |

---

# Business Architecture

Northwind Technologies supports multiple business departments through centralized Information Technology Services (ITS).

Business Units include:

* Executive
* Human Resources
* Finance
* Information Technology
* Engineering
* Sales
* Marketing
* Operations

Each department utilizes centralized authentication, shared storage, and standardized security policies managed through Active Directory.

---

# Technology Lifecycle

Technology Evolution

Sprint 1
-----------
Windows Server 2025
Windows 11 Enterprise
Ubuntu Server
Active Directory

↓

Sprint 2
-----------
Enterprise Operations
File Services
Documentation Standards

↓

Sprint 3
-----------
osTicket
Help Desk Operations

↓

Sprint 4
-----------
Wazuh
Sysmon
Security Operations

↓

Sprint 5
-----------
Microsoft 365
Entra ID

↓

Sprint 6
-----------
PowerShell
Automation

↓

Sprint 7
-----------
Enterprise Capstone
Operational Readiness

---

# Infrastructure Architecture

| Server   | Purpose                | Primary Services                |
| -------- | ---------------------- | ------------------------------- |
| DC01     | Enterprise Identity    | AD DS, DNS, DHCP, File Services |
| Ubuntu01 | Enterprise Linux       | osTicket, Future Wazuh          |
| CLIENT01 | Enterprise Workstation | Domain Validation, GPO Testing  |

---

### Client Systems

Windows 11 Enterprise workstations joined to the NORTHWIND.LOCAL domain.

---

# Network Architecture

Core network services include:

* DNS
* DHCP
* IPv4 addressing
* Static server addressing
* Dynamic client addressing

The network has been designed to support centralized management while maintaining scalability for future enterprise expansion.

---

# Active Directory Architecture

The Active Directory environment is organized using Organizational Units aligned with business departments.

Examples include:

* Forest
  ↓
* Domain
  ↓
* Organizational Units
  ↓
* Securitiy Groups
  ↓
* Users
  ↓
* Department Resources

Administrative delegation is performed using security groups following least-privilege principles.

---

# File Services Architecture

Enterprise file services are hosted centrally and organized by department.

Current shared resources include:

* Executive
* HR
* Finance
* Engineering
* IT
* Marketing
* Operations
* Sales
* Public
* Software Repository

Access is controlled using NTFS permissions and Active Directory security groups.

---

# Identity & Access Management

Identity management is provided through Active Directory.

Authentication is centralized through Active Directory Domain Services. Authorization is controlled through departmental security groups and NTFS permissions. Administrative delegation follows the principle of least privilege while Group Policy provides standardized workstation configuration across the enterprise.

Security principles include:

* Least Privilege
* Role-Based Access Control (RBAC)
* Group-Based Permissions
* Password Policies
* Account Lockout Policies
* Administrative Separation

---

# Help Desk Architecture

Northwind Technologies utilizes osTicket as the centralized Help Desk platform.

Capabilities include:

* Ticket Management
* User Support
* Incident Tracking
* Knowledge Base
* Service Requests
* Ticket Escalation

---

# Security Architecture

The enterprise security model includes:

* Current Security Controls
  * Microsoft Defender
  * Windows Firewall
  * NTFS Permissions
  * Group Policy
  * Security Groups
  * Password Policy
  * Account Lockout
* Future Security Controls
  * Wazuh SIEM
  * Sysmon
  * SOC Monitoring
  * Incident Response
  * Threat Detection

---

# Automation Architecture

PowerShell is the primary automation platform.

Current automation objectives include:

* User Management
* Group Administration
* Shared Folder Management
* Reporting
* System Administration

Future automation will expand to Microsoft 365 administration and enterprise reporting.

---

# Documentation Architecture

All enterprise documentation follows the Northwind Technologies Documentation Standard.

Documentation categories include:

* Documentation Standards
  ↓
* Project Management
  ↓
* Enterprise Documentation
  ↓
* Engineering Guides
  ↓
* SOP Library
  ↓
* Incident Reports
  ↓
* Knowledge Base
  ↓
* Ticket Walkthroughs

---

# Enterprise Technology Roadmap

Future enterprise initiatives include:

* Microsoft Entra ID
* Microsoft 365
* Exchange Online
* SharePoint Online
* OneDrive
* Intune
* Endpoint Management
* Enterprise Monitoring
* Disaster Recovery
* Security Operations Center (SOC)

---

# Related Documentation

* NWT-ENT-001 Company Profile
* NWT-ENT-003 Enterprise Network Diagram
* NWT-ENT-004 Server Inventory
* NWT-ENT-005 IP Address Plan
* NWT-ENT-006 Enterprise Naming Standards
* NWT-ENT-007 Organization Chart
* NWT-PM-001 Project Charter

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

| Version | Date      | Author            | Description     |
| ------- | --------- | ----------------- | --------------- |
| 1.0     | June 2026 | Brandon J. Cooper | Initial release |

---

**Northwind Technologies**

**Information Technology Services (ITS)**

*Innovate • Secure • Support*

© 2026 Northwind Technologies
