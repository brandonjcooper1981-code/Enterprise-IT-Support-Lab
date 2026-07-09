# NWT-SOP-003 DNS Administration SOP

| Property | Value |
|----------|--------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-003 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain the Northwind Technologies Domain Name System (DNS) infrastructure.

The DNS environment supports Active Directory services, workstation authentication, Group Policy processing, file shares, server communications, and future enterprise services.

---

## Purpose

This SOP defines the standards and procedures for:

- DNS administration
- DNS troubleshooting
- Zone management
- Record management
- Forwarder configuration
- DNS monitoring
- Backup and recovery
- Security controls

---

## Scope

Applies to:

- Windows Server 2025 DNS
- Active Directory-integrated zones
- Forward lookup zones
- Reverse lookup zones
- Domain controllers
- Client workstations
- DHCP integration
- Future cloud DNS services

---

## Supported Systems

- DC01
- Northwind.local
- Windows DNS Server
- DHCP Server
- Windows 11 clients
- Active Directory
- Group Policy
- File Services

---

## Administrative Tools

Authorized tools include:

- DNS Manager
- Windows Admin Center (Future)
- PowerShell
- Event Viewer
- RSAT DNS Tools
- Command Prompt
- Wazuh (Future)

---

## Roles & Responsibilities

| Role | Responsibility |
|--------|--------|
| CIO | Approves DNS standards |
| Infrastructure Lead | DNS administration |
| System Administrator | DNS maintenance |
| Help Desk | Tier 1 troubleshooting |
| Documentation Owner | SOP maintenance |

---

## DNS Architecture

Enterprise DNS hierarchy:

Northwind.local

├── Forward Lookup Zones

│   └── northwind.local

├── Reverse Lookup Zones

│   └── 192.168.56.x

├── Domain Controllers

│   └── DC01

└── Clients

    └── Windows 11 Workstations

---

## DNS Record Types

| Record Type | Purpose |
|--------------|-------------|
| A | Host record |
| AAAA | IPv6 host |
| PTR | Reverse lookup |
| CNAME | Alias |
| MX | Mail routing |
| NS | Name server |
| SRV | Active Directory services |
| TXT | Verification records |

---

## Zone Management

### Forward Lookup Zone

- northwind.local
- Secure dynamic updates
- Active Directory integrated

### Reverse Lookup Zone

- 192.168.56.x
- PTR records enabled

---

## DNS Administration Tasks

| Task | Frequency |
|--------|--------|
| Verify DNS service | Daily |
| Review DNS logs | Daily |
| Validate forwarders | Weekly |
| Review stale records | Monthly |
| Verify zone replication | Monthly |
| Test name resolution | Monthly |

---

## DNS Configuration Standards

Requirements:

- Active Directory-integrated zones
- Secure dynamic updates only
- DNS installed on domain controllers
- Internal DNS used by domain clients
- Public DNS through forwarders

---

## DNS Troubleshooting Playbooks

### Cannot Resolve Hostname

Severity: Medium

Estimated Resolution: 15–30 minutes

Escalation: Infrastructure Team

1. Verify network connectivity.
2. Run:

    ```cmd
    ping DC01
    ```

3. Run:

    ```cmd
    ipconfig /all
    ```

4. Verify DNS server settings.
5. Run:

    ```cmd
    nslookup hostname
    ```

6. Run:

    ```cmd
    ipconfig /flushdns
    ```

7. Restart DNS Client service.
8. Verify resolution.
9. Document ticket.
10. Close request.

---

### DNS Server Unreachable

Severity: High

Estimated Resolution: 30–60 minutes

Escalation: Infrastructure Team

1. Verify DC01 is online.
2. Confirm DNS service status.
3. Test connectivity.
4. Restart DNS service.
5. Review Event Viewer.
6. Validate zones.
7. Verify client resolution.
8. Document ticket.
9. Escalate if unresolved.

---

### Missing DNS Record

Severity: Medium

Estimated Resolution: 15–30 minutes

Escalation: Infrastructure Team

1. Open DNS Manager.
2. Verify record existence.
3. Check replication status.
4. Recreate record if authorized.
5. Run:

    ```powershell
    ipconfig /registerdns
    ```

6. Verify resolution.
7. Document ticket.

---

## PowerShell Administration

Common commands:

```powershell
Get-DnsServerZone

Get-DnsServerResourceRecord

Resolve-DnsName DC01

Clear-DnsClientCache

ipconfig /flushdns

ipconfig /registerdns
```

---

## Monitoring & Health Checks

Verify:

- DNS Server service
- Zone health
- Event logs
- Forwarders
- Replication
- Name resolution
- Client connectivity

---

## Backup Requirements

Before major DNS changes:

- Verify snapshot exists
- Export DNS configuration
- Confirm rollback plan
- Update documentation
- Follow NWT-STD-005

---

## Security Requirements

Requirements include:

- Least privilege
- RBAC
- Secure dynamic updates
- Administrative separation
- Audit logging
- Change approval

---

## Validation Checklist

| Validation | Status |
|------------|------------|
| DNS Installed | Verified |
| Forward Zone Configured | Verified |
| Reverse Zone Configured | Verified |
| Name Resolution Tested | Verified |
| Event Logs Reviewed | Verified |
| Documentation Updated | Complete |

---

## DNS Administration Workflow

Request Received
↓
Review Request
↓
Validate Change
↓
Implement Change
↓
Test Resolution
↓
Document
↓
Close Request

---

## Future Improvements

- Secondary DNS server
- DNS replication
- Azure DNS
- DNS analytics
- Microsoft Sentinel integration
- Wazuh monitoring
- Conditional forwarders
- Split DNS

---

## Related Documentation

- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-004 Server Inventory
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Backup & Recovery Plan
- NWT-ENT-010 Disaster Recovery Plan
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard
- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-002 Help Desk Operations SOP

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
