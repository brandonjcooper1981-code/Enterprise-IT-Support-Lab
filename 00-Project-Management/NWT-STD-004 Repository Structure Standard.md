# NWT-STD-004 Repository Structure Standard

| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-STD-004 |
| **Document Type** | Enterprise Repository Standard |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

The Repository Structure Standard establishes the organizational framework used throughout the Northwind Technologies Enterprise IT Modernization Project. This standard defines the directory layout, file organization, naming conventions, documentation hierarchy, and evidence management practices used across every sprint, milestone, and engineering project.

A standardized repository structure improves consistency, simplifies navigation, accelerates onboarding, and ensures that engineering documentation remains scalable as the enterprise environment expands.

---

## Purpose

This standard defines how all project repositories are organized to ensure predictable storage of documentation, engineering artifacts, PowerShell automation, validation evidence, and project deliverables.

Objectives include:

Standardized project organization
Faster navigation
Easier maintenance
Consistent documentation
Improved collaboration
Repeatable engineering process
Scalable repository growth

---

## Repository Scope

This standard applies to:

- Enterprise repositories
- Sprint repositories
- Milestone repositories
- PowerShell repositories
- Documentation repositories
- Knowledge Base repositories

---

## Repository Design Principles

The repository follows these core principles:

Documentation First
Consistent Folder Structure
Separation of Design and Implementation
Evidence-Based Validation
Automation Ready
Version Controlled
Enterprise Scalability

---

## Standard Repository Layout

Repository
│
├── README.md
├── 00-Documentation
├── 01-Commands
├── 02-Design
├── 03-Implementation
├── 04-Configuration
├── 05-Validation
├── 06-PowerShell
├── 07-Evidence
├── 08-Screenshots
└── 09-Notes

---

## Standard Folder Definitions

| Folder            | Purpose                                            |
| ----------------- | -------------------------------------------------- |
| README.md         | Project overview                                   |
| 00-Documentation  | Design documents, standards, validation checklists |
| 01-Commands       | Frequently used commands                           |
| 02-Design         | Architecture, diagrams, planning                   |
| 03-Implementation | Build procedures                                   |
| 04-Configuration  | Configuration files and exports                    |
| 05-Validation     | Verification procedures                            |
| 06-PowerShell     | Modules, scripts, reports                          |
| 07-Evidence       | Logs, exports, configuration backups               |
| 08-Screenshots    | Screenshots organized by task                      |
| 09-Notes          | Lessons learned and troubleshooting                |

---

## Sprint Repository Layout

Each sprint follows the same standardized layout.

Sprint
│
├── 00-Documentation
├── 01-Commands
├── 02-Planning
├── 03-Implementation
├── 04-Configuration
├── 05-Validation
├── 06-PowerShell
├── 07-Evidence
├── 08-Screenshots
├── 09-Notes
└── README.md

---

## Screenshot Organization

Screenshots should be grouped by implementation stage.

08-Screenshots
│
├── Infrastructure
├── Installation
├── Configuration
├── Validation
├── Troubleshooting
└── Final

---

## Evidence Organization

Evidence should contain supporting artifacts used during implementation.

Examples include:
- Event Viewer exports
- PowerShell output
- GPResult reports
- Network captures
- Configuration exports
- Inventory reports
- CSV files
- Log files

---

## PowerShell Organization

06-PowerShell
│
├── Modules
├── Scripts
├── Reports
└── Exports

---

## Documentation Standards

Every repository should include:
- README
- Executive Summary
- Design Documentation
- Validation Documentation
- Lessons Learned
- Troubleshooting Notes
- References

---

## README Requirements

Each repository README should include:
- Project Overview
- Objectives
- Prerequisites
- Architecture Diagram
- Technologies Used
- Implementation
- Validation
- Lessons Learned
- Related Documentation
- License

---

## File Naming Standard

Examples:
- 0Create-Users.ps1
- Export-GPO.ps1
- DHCP-Configuration.md
- Server-Inventory.md
- Validation-Checklist.md

---

## Screenshot Naming Standard

Examples:
- 01-Domain-Install.png
- 02-DNS-Configuration.png
- 03-DHCP-Scope.png
- 04-Group-Policy.png
- 05-Validation.png

---

## Evidence Naming Standard

Examples:
- GPResult.txt
- DHCP-Export.xml
- AD-Users.csv
- DNS-Zones.csv
- PowerShell-Output.txt

---

## Repository Lifecycle

Planning
    ↓
Documentation
    ↓
Implementation
    ↓
Validation
    ↓
Evidence Collection
    ↓
Automation
    ↓
Maintenance

---

## Repository Growth Strategy

Repositories should evolve according to the enterprise roadmap.

Current focus:
- Active Directory
- DNS
- DHCP
- File Services
- Help Desk
- Documentation

Future additions:
- Microsoft 365
- Entra ID
- Intune
- WDS
- WSUS
- SQL
- Wazuh
- Sysmon
- PKI
- MECM
- Azure

---

## Repository Maturity Model

Level 1  Documentation
        ↓
Level 2  Configuration
        ↓
Level 3  Validation
        ↓
Level 4  Automation
        ↓
Level 5  Enterprise Ready

Definitions:

| Level   | Meaning                       |
| ------- | ----------------------------- |
| Level 1 | Documentation Complete        |
| Level 2 | Infrastructure Implemented    |
| Level 3 | Validation Complete           |
| Level 4 | PowerShell Automation Added   |
| Level 5 | Enterprise Production Quality |

---

## Repository Navigation

Project
│
├── Standards
│
├── Enterprise
│
├── Project Management
│
├── Sprint 1
│
├── Sprint 2
│
├── Sprint 3
│
└── Archive

## Validation Checklist

| Validation                    | Status   |
| ----------------------------- | -------- |
| Folder Structure Standardized | Verified |
| README Present                | Verified |
| Documentation Organized       | Verified |
| PowerShell Organized          | Verified |
| Evidence Organized            | Verified |
| Screenshots Organized         | Verified |
| Naming Standard Applied       | Complete |

---

## Related Documentation
- NWT-STD-001 Enterprise Documentation Standard
- NWT-STD-002 Markdown & Document Style Guide
- NWT-STD-003 Engineering Documentation Standard
- NWT-ENT-001 Company Profile
- NWT-PM-003 Milestones

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

**Northwind Technologies**

**Information Technology Services (ITS)**

*Innovate • Secure •Support*

© 2026 Northwind Technologies
