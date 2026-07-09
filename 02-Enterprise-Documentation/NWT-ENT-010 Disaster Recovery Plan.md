# NWT-ENT-010 Enterprise Disaster Recovery Plan

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-010 |
| Document Type | Enterprise Business Continuity Document |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | July 2026 |

---

## Executive Summary

The Enterprise Disaster Recovery Plan establishes the procedures required to restore critical business services following a major infrastructure failure, security incident, natural disaster, or other event that significantly disrupts Northwind Technologies operations. This plan defines recovery priorities, emergency response procedures, service restoration workflows, validation requirements, and future disaster recovery capabilities supporting the Enterprise IT Modernization Project.

The objective of this plan is to minimize downtime, protect business-critical infrastructure, restore enterprise services in a controlled manner, and ensure operational continuity through documented recovery procedures.

---

## Disaster Recovery Decision

System Failure
      │
      ▼
Single Server?
 ┌──────┴──────┐
 │             │
Yes           No
 │             │
Restore VM   Declare Disaster
 │             │
Validate     Notify CIO
 │             │
Operational  Full DR Plan

---

## Purpose

This document defines the disaster recovery procedures used to restore enterprise infrastructure following events that cannot be resolved through normal operational recovery.

Objectives include:
- Restore critical business services
- Minimize operational downtime
- Protect enterprise data
- Define recovery priorities
- Standardize recovery procedures
- Validate restored services
- Support business continuity

---

# Disaster Recovery Principles

Northwind Technologies follows these recovery principles:
- Safety First
- Critical Systems First
- Document Every Action
- Validate Every Recovery
- Least Downtime Possible
- Preserve Evidence
- Controlled Restoration
- Continuous Improvement

---

## Enterprise Recovery Architecture

Enterprise Infrastructure
        │
        ├───────────────┐
        │               │
     DC01          UBUNTU01
        │               │
        │               │
 Active Directory   osTicket
 DNS                MariaDB
 DHCP               Apache
 SMB Shares         PHP
        │               │
        └──────┬────────┘
               │
      Documentation Repository
               │
      Git Repository
      Configuration Exports
      Snapshots

---

## Disaster Classification

| Disaster                  | Severity |
| ------------------------- | -------- |
| Single Service Failure    | Low      |
| Server Failure            | Medium   |
| Domain Controller Failure | High     |
| Multiple Server Failure   | Critical |
| Ransomware                | Critical |
| Complete Site Loss        | Critical |

---

## Recovery Priority Matrix

| Disaster                  | Severity |
| ------------------------- | -------- |
| Single Service Failure    | Low      |
| Server Failure            | Medium   |
| Domain Controller Failure | High     |
| Multiple Server Failure   | Critical |
| Ransomware                | Critical |
| Complete Site Loss        | Critical |

---

## Recovery Priority Matrix

| Priority | Service          |
| -------- | ---------------- |
| Tier 1   | Active Directory |
| Tier 1   | DNS              |
| Tier 1   | DHCP             |
| Tier 2   | File Services    |
| Tier 2   | Ubuntu Server    |
| Tier 2   | MariaDB          |
| Tier 2   | osTicket         |
| Tier 3   | Documentation    |

---

## Recovery Procedures

Separate sections for:

### Active Directory Recovery

Restore:
- Domain Controller
- DNS
- DHCP
- Authentication
- Group Policy
- Users
- Security Groups

### Ubuntu Server Recovery

Restore:
- Ubuntu Server
- Apache
- PHP
- MariaDB
- osTicket
- SSH

### File Services Recovery

Restore:
- SMB Shares
- NTFS Permissions
- Department Folders
- Public Share
- Software Repository

### Documentation Recovery

Restore:
- Git Repository
- Markdown Files
- Diagrams
- Standards
- Sprint Documentation

---

## Disaster Recovery Timeline

| Phase                   | Target     |
| ----------------------- | ---------- |
| Incident Assessment     | 15 Minutes |
| Disaster Declaration    | 30 Minutes |
| Infrastructure Recovery | 2 Hours    |
| Application Recovery    | 4 Hours    |
| Validation              | 1 Hour     |
| Return to Operations    | <8 Hours   |

---

## Communication Plan

| Role                  | Responsibility          |
| --------------------- | ----------------------- |
| CIO                   | Executive Coordination  |
| Infrastructure Lead   | Infrastructure Recovery |
| IT Operations Manager | System Validation       |
| Help Desk Manager     | User Communication      |
| Documentation Owner   | Recovery Documentation  |

---

## Current Recovery Technologies
- VirtualBox Snapshots
- Git Repository
- Configuration Exports
- Windows Event Viewer
- Manual Recovery Documentation

---

## Future Recovery Technologies
- Windows Server Backup
- Automated Restore Scripts
- PowerShell Recovery Automation
- Azure Site Recovery
- Wazuh Incident Detection
- Microsoft Sentinel
- Automated Health Validation

## Recovery Validation Checklist

Verify:
- Domain Authentication
- DNS Resolution
- DHCP Services
- Group Policy
- File Shares
- osTicket
- MariaDB
- Documentation
- Event Logs
- Security Controls

---

## Disaster Recovery Matrix

| Metric                      | Target        |
| --------------------------- | ------------- |
| Infrastructure Availability | >99%          |
| Recovery Success            | >95%          |
| Validation Completion       | 100%          |
| Documentation Updated       | 100%          |
| Recovery Time Objective     | Within Target |
| Recovery Point Objective    | Within Target |

---

## Future Disaster Recovery Roadmap
- Automated DR Testing
- Wazuh Incident Response
- Microsoft Sentinel Integration
- Azure Site Recovery
- High Availability Services
- Secondary Backup Site
- Infrastructure as Code Recovery
- Cloud Failover

---

## Disaster Recovery Testing Schedule

| Test                            | Frequency | Owner               |
| ------------------------------- | --------- | ------------------- |
| Snapshot Restore                | Monthly   | Infrastructure Lead |
| Active Directory Recovery       | Quarterly | Infrastructure Lead |
| Ubuntu Recovery                 | Quarterly | Infrastructure Lead |
| Documentation Restore           | Monthly   | Documentation Owner |
| Full Disaster Recovery Exercise | Annually  | CIO / ITS           |

---

## Assumptions

- DC01 remains the authoritative Domain Controller.
- Recovery media is available.
- VirtualBox snapshots are intact.
- Git repository remains accessible.
- Documentation repository has been cloned locally.
- Administrative credentials are available.
- Backup integrity has been previously validated.

---

## Related Documentation
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Enterprise Backup & Recovery Plan
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard
- NWT-STD-008 Security Configuration Standard

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
