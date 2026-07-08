# NWT-ENT-008 Enterprise Security Baseline

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-008 |
| Document Type | Enterprise Security Standard |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | July 2026 |

---

## Executive Summary

The Enterprise Security Baseline establishes the minimum security standards implemented throughout the Northwind Technologies Enterprise IT Modernization Project. This document defines the administrative, technical, and operational security controls used to protect enterprise infrastructure, Active Directory services, Windows workstations, Linux servers, enterprise data, and future cloud services.

The security baseline provides a standardized framework that supports confidentiality, integrity, and availability while ensuring consistency across all enterprise systems and future technology deployments.

---

## Purpose

This document defines the enterprise security controls required for all infrastructure deployed within Northwind Technologies.

Objectives include:
- Standardized security configuration
- Least privilege administration
- Centralized identity management
- Secure authentication
- Consistent auditing
- Enterprise monitoring
- Future cloud readiness

---

## Enterprise Security Architecture

                    Users
                      │
          Active Directory
                      │
        Authentication (Kerberos)
                      │
          Security Groups (RBAC)
                      │
             Group Policy
                      │
      ┌───────────────┼───────────────┐
      │               │               │
 Windows 11        DC01         UBUNTU01
 Defender      NTFS/DNS/DHCP    SSH/Apache
      │               │               │
      └───────────────┼───────────────┘
                      │
             Windows Firewall
                      │
            Event Viewer Logs
                      │
         Future: Sysmon → Wazuh → SIEM

---

## Security Principles

Northwind Technologies follows these enterprise security principles:
- Least Privilege
- Defense in Depth
- Zero Trust (Future Direction)
- Secure by Default
- Centralized Administration
- Role-Based Access Control (RBAC)
- Group-Based Authorization
- Documentation First
- Continuous Improvement

---

## Security Domains

| Domain              | Technology                    |
| ------------------- | ----------------------------- |
| Identity            | Active Directory              |
| Authentication      | Kerberos                      |
| Authorization       | Security Groups               |
| Endpoint Protection | Microsoft Defender            |
| Firewall            | Windows Firewall              |
| File Security       | NTFS Permissions              |
| Network Security    | Windows Firewall Rules        |
| Monitoring          | Event Viewer                  |
| Future Monitoring   | Sysmon, Wazuh                 |
| Cloud Security      | Microsoft Entra ID *(Future)* |

---

## Security Baseline Matrix

| Control            | Current | Planned  |
| ------------------ | ------- | -------- |
| Active Directory   | ✓       |          |
| Kerberos           | ✓       |          |
| Defender           | ✓       |          |
| Windows Firewall   | ✓       |          |
| BitLocker          |         | Sprint 5 |
| Sysmon             |         | Sprint 5 |
| Wazuh              |         | Sprint 6 |
| Entra ID           |         | Future   |
| MFA                |         | Future   |
| Conditional Access |         | Future   |

---

## Security Classification Levels

| Asset             | Classification |
| ----------------- | -------------- |
| Domain Controller | Tier 1         |
| DNS               | Tier 1         |
| DHCP              | Tier 1         |
| File Shares       | Tier 2         |
| Help Desk         | Tier 2         |
| Workstations      | Tier 3         |

---

## Security Compliance Mapping

| Framework                   | Status    |
| --------------------------- | --------- |
| CIS Controls                | Partial   |
| NIST CSF                    | Planned   |
| Microsoft Security Baseline | Planned   |
| Security+ Objectives        | Supported |

---

## Identity & Access Management

Authentication is centralized through Active Directory.
- Identity Controls
- Domain Authentication
- Organizational Units
- Security Groups
- Group Policy
- Password Policies
- Account Lockout Policies
- Administrative Separation

---

## Administrative Security

Administrative accounts should be separated from standard user accounts.

Examples:
BCooper
ADMIN-BCOOPER

JSmith
ADMIN-JSMITH

Administrative activities include:
- Server Administration
- Active Directory
- DNS
- DHCP
- File Services
- Group Policy
- PowerShell Administration

---

## Passsword Standards

| Setting           | Standard      |
| ----------------- | ------------- |
| Minimum Length    | 14 Characters |
| Complexity        | Enabled       |
| Password History  | 24 Passwords  |
| Maximum Age       | 90 Days       |
| Minimum Age       | 1 Day         |
| Lockout Threshold | 5 Attempts    |
| Lockout Duration  | 15 Minutes    |
| Reset Counter     | 15 Minutes    |

---

## Group Policy Security Baseline

Security policies include:
- Password Policy
- Account Lockout Policy
- Windows Firewall
- Microsoft Defender
- Windows Updates
- Desktop Security
- Audit Policies
- Drive Mapping
- Software Restrictions (Future)

---

## Endpoint Security

Current endpoint protection includes:
- Microsoft Defender
- Windows Firewall
- Windows Updates
- BitLocker (Future)
- Device Control (Future)

Supported systems:
- Windows Server 2025
- Windows 11 Enterprise
- Ubuntu Server 24.04 LTS

---

## Server Security
DC01

Security responsibilities:
- Active Directory
- DNS
- DHCP
- File Services
- Authentication
- Authorization

UBUNTU01

Security responsibilities:
- SSH
- Apache
- PHP
- MariaDB
- osTicket
- Linux Updates

---

## File Security

Enterprise file security utilizes:
- NTFS Permissions
- SMB Permissions
- Security Groups
- Department Access
- Least Privilege

Protected resources include:
- HR
- Finance
- Executive
- Engineering
- Operations
- Sales
- Marketing
- IT
- Public
- Software Repository

---

## Logging & Auditing

Current logging:
- Windows Event Viewer
- Active Directory Logs
- DNS Logs
- DHCP Logs
- Security Logs

Future logging:
- Sysmon
- Windows Event Forwarding
- Wazuh SIEM
- Centralized Audit Repository

---

## Network Security

Security controls include:
- Static Server Addressing
- DHCP Client Assignment
- DNS Integration
- Windows Firewall
- Host-Only Virtual Network
- Administrative Network Segmentation (Future)

---

## Help Desk Security

Security controls include:
- Role-Based Technician Accounts
- Ticket Permissions
- Password Reset Procedures
- User Verification
- Audit Logging
- Knowledge Base Access

---

## PowerShell Security

PowerShell standards include:
- Script Signing (Future)
- Module Standardization
- Administrative Execution
- Version Control
- GitHub Repository
- Documentation Required

---

## Backup Security

Current:
- VirtualBox Snapshots
- GitHub Documentation

Future:
- Windows Server Backup
- MariaDB Backup
- Offsite Repository
- Configuration Export
- Disaster Recovery

---

## Security Monitoring Roadmap

| Phase    | Technology                      |
| -------- | ------------------------------- |
| Current  | Windows Event Viewer            |
| Sprint 5 | Sysmon                          |
| Sprint 6 | Wazuh                           |
| Sprint 7 | Windows Event Forwarding        |
| Future   | Microsoft Defender for Endpoint |
| Future   | Microsoft Sentinel              |

---

## Future Enterprise Security

Planned technologies include:
- Microsoft Entra ID
- Microsoft 365 Security
- Intune
- Defender for Endpoint
- Wazuh
- Sysmon
- PKI
- MFA
- Conditional Access
- Microsoft Sentinel
- Azure Security Center

---

## Security Compliance Checklist

| Validation                | Status   |
| ------------------------- | -------- |
| Active Directory Security | Verified |
| Password Policies         | Verified |
| NTFS Permissions          | Verified |
| Windows Firewall          | Verified |
| Microsoft Defender        | Verified |
| Administrative Separation | Verified |
| Documentation Complete    | Complete |

---

## Related Security Procedures
- Account Lockout
- Password Reset
- Malware Response (Future)
- Unauthorized Access (Future)
- Incident Escalation (Future)

---

## Related Documentation
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-003 Enterprise Network Diagram
- NWT-ENT-004 Server Inventory
- NWT-ENT-005 Enterprise IP Address Plan
- NWT-ENT-006 Enterprise Naming Standards
- NWT-ENT-007 Organization Chart
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


