# NWT-ENT-009 Enterprise Backup & Recovery Plan

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-009 |
| Document Type | Enterprise Business Continuity Documentation |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | July 2026 |

---

## Executive Summary

The Enterprise Backup & Recovery Plan establishes the backup, restoration, and disaster recovery procedures used throughout the Northwind Technologies Enterprise IT Modernization Project. This document defines standardized backup strategies, recovery objectives, validation procedures, and restoration priorities for enterprise infrastructure, Active Directory services, Linux application servers, documentation, and future enterprise services.

The plan is designed to minimize downtime, protect business-critical data, support operational continuity, and provide a scalable recovery framework as additional infrastructure is introduced throughout future project sprints.

---

## Purpose

This document defines the enterprise backup and recovery standards required to ensure business continuity and rapid restoration of services following hardware failure, software corruption, administrative error, or security incidents.

Objectives include:
- Protect enterprise infrastructure
- Minimize downtime
- Standardize backup procedures
- Simplify disaster recovery
- Protect configuration data
- Validate recoverability
- Support future enterprise expansion

---

## Business Continuity Principles

Northwind Technologies follows these recovery principles:

- Backup Before Change
- Recovery First
- Multiple Recovery Methods
- Documented Recovery Procedures
- Least Downtime Possible
- Validate Every Backup
- Test Recovery Regularly
- Continuous Improvement

---

## Enterprise Backup Architecture

                   Enterprise Infrastructure

                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
        DC01             UBUNTU01          Documentation
          │                  │                  │
 Active Directory      osTicket          Git Repository
 DNS                  MariaDB            Markdown Docs
 DHCP                 Apache             PowerShell
 SMB Shares           PHP                Diagrams
          │                  │                  │
          └──────────────┬──────────────────────┘
                         │
                  Backup Repository
                         │
         ┌───────────────┴─────────────────┐
         │                                 │
 VirtualBox Snapshots              Future Backups
                                   Windows Server Backup
                                   MariaDB Dumps
                                   Configuration Exports
                                   Offsite Storage

---

## Recovery Objectives (RPO/RTO)

| Service          | Recovery Priority | RPO      | RTO     |
| ---------------- | ----------------- | -------- | ------- |
| Active Directory | Critical          | 24 Hours | 2 Hours |
| DNS              | Critical          | 24 Hours | 2 Hours |
| DHCP             | High              | 24 Hours | 2 Hours |
| File Services    | High              | 24 Hours | 4 Hours |
| osTicket         | High              | 24 Hours | 4 Hours |
| Documentation    | Medium            | 24 Hours | 1 Hour  |

---

## Backup Classification

| Asset            | Classification | Backup Priority |
| ---------------- | -------------- | --------------- |
| DC01             | Tier 1         | Critical        |
| Active Directory | Tier 1         | Critical        |
| DNS              | Tier 1         | Critical        |
| DHCP             | Tier 1         | Critical        |
| UBUNTU01         | Tier 2         | High            |
| MariaDB          | Tier 2         | High            |
| osTicket         | Tier 2         | High            |
| Documentation    | Tier 3         | Standard        |

---

## Current Backup Strategy

| Component          | Method               | Status      |
| ------------------ | -------------------- | ----------- |
| Virtual Machines   | VirtualBox Snapshots | Operational |
| Documentation      | GitHub Repository    | Operational |
| Configuration      | Manual Export        | Operational |
| PowerShell Scripts | Git Repository       | Operational |

---

## Backup Frequency Matrix

| Asset                 | Frequency      |
| --------------------- | -------------- |
| DC01                  | Before Changes |
| UBUNTU01              | Before Changes |
| Documentation         | Every Commit   |
| PowerShell            | Every Commit   |
| Configuration Exports | Monthly        |

---

## Recovery Priority Levels

| Priority | Description             |
| -------- | ----------------------- |
| P1       | Active Directory        |
| P2       | Infrastructure Services |
| P3       | Applications            |
| P4       | Documentation           |

---

## Recovery Testing Schedule

| Test                  | Frequency   |
| --------------------- | ----------- |
| Snapshot Restore      | Quarterly   |
| AD Validation         | Quarterly   |
| Documentation Restore | Monthly     |
| osTicket Recovery     | Semi-Annual |

---

## Future Backup Strategy

| Technology                   | Planned Sprint |
| ---------------------------- | -------------- |
| Windows Server Backup        | Sprint 6       |
| MariaDB Scheduled Backup     | Sprint 6       |
| PowerShell Backup Automation | Sprint 7       |
| Offsite Repository           | Future         |
| Incremental Backups          | Future         |
| Enterprise Backup Server     | Future         |

---

## Server Backup Matrix

| Server   | Backup Method | Frequency      | Priority |
| -------- | ------------- | -------------- | -------- |
| DC01     | Snapshot      | Before Changes | Critical |
| UBUNTU01 | Snapshot      | Before Changes | High     |

---

## Active Directory Recovery

Recovery includes:

Active Directory
- DNS
- DHCP
- Group Policy
- Organizational Units
- Security Groups
- User Accounts
- SMB Shares

Recovery priority:
1. Restore DC01
2. Verify DNS
3. Verify DHCP
4. Validate AD Replication (Future)
5. Validate Authentication
6. Validate Group Policy
7. Validate File Shares

## Ubuntu Server Recovery

Recovery includes:
- Ubuntu Server
- Apache
- PHP
- MariaDB
- osTicket
- SSH Configuration

Recovery priority:
1. Restore Virtual Machine
2. Verify Network
3. Verify Apache
4. Verify Database
5. Verify osTicket
6. Verify Help Desk Access

---

## Configuration Backup

Current configuration exports include:
- DHCP Configuration
- DNS Zones
- PowerShell Scripts
- Group Policy Backups (Future)
- Network Documentation
- Server Inventory
- Security Documentation

---

## Documentation Backup

Enterprise documentation is stored within:
- GitHub Repository
- Markdown Documentation
- Version Control
- Local Repository Clone

Documentation includes:
- Enterprise Standards
- Architecture
- Network Documentation
- Security Baselines
- Project Documentation
- Sprint Documentation

---

## Recovery Validation Checklist

| Validation                 | Status   |
| -------------------------- | -------- |
| VM Restored Successfully   | Verified |
| Active Directory Available | Verified |
| DNS Functional             | Verified |
| DHCP Operational           | Verified |
| Authentication Successful  | Verified |
| osTicket Available         | Verified |
| Documentation Accessible   | Verified |

---

## Recovery Workflow

Failure Detected
       │
       ▼
Assess Impact
       │
       ▼
Determine Recovery Priority
       │
       ▼
Restore Snapshot
       │
       ▼
Validate Services
       │
       ▼
Restore User Access
       │
       ▼
Document Recovery
       │
       ▼
Close Incident

---

## Disaster Recovery Roadmap

| Phase    | Objective                        |
| -------- | -------------------------------- |
| Current  | VirtualBox Snapshots             |
| Sprint 6 | Windows Server Backup            |
| Sprint 7 | Automated Backup Scripts         |
| Sprint 8 | Recovery Validation Automation   |
| Future   | Enterprise Backup Infrastructure |
| Future   | Cloud Backup Integration         |

---

## Related Documentation
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-003 Enterprise Network Diagram
- NWT-ENT-004 Server Inventory
- NWT-ENT-005 Enterprise IP Address Plan
- NWT-ENT-008 Enterprise Security Baseline
- NWT-STD-001 Enterprise Documentation Standard

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


