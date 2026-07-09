# NWT-SOP-004 DHCP Administration SOP

| Property | Value |
|-----------|--------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-004 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain the Northwind Technologies Dynamic Host Configuration Protocol (DHCP) infrastructure.

The DHCP environment supports workstation connectivity, automatic IP address assignment, DNS integration, domain communications, and future enterprise services.

---

## Purpose

This SOP defines standards and procedures for:
- DHCP administration
- Scope management
- Reservation management
- Lease management
- DNS integration
- DHCP troubleshooting
- Monitoring and health checks
- Backup and recovery
- Security controls

---

## Scope

Applies to:
- Windows Server 2025 DHCP
- Active Directory-integrated environment
- DHCP scopes
- Reservations
- DHCP options
- Domain controllers
- Client workstations
- DNS integration
- Future cloud DHCP services

---

## Supported Systems

- DC01
- Northwind.local
- Windows DHCP Server
- Windows 11 clients
- Active Directory
- DNS Server
- Group Policy
- File Services

---

## Administrative Tools

Authorized tools include:
- DHCP Manager
- Windows Admin Center (Future)
- PowerShell
- Event Viewer
- RSAT DHCP Tools
- Command Prompt
- Wazuh (Future)

---

## Roles & Responsibilities

| Role | Responsibility |
|--------|--------|
| CIO | Approves DHCP standards |
| Infrastructure Lead | DHCP administration |
| System Administrator | DHCP maintenance |
| Help Desk | Tier 1 troubleshooting |
| Documentation Owner | SOP maintenance |

---

## DHCP Architecture

Enterprise DHCP hierarchy:

Northwind.local

├── DHCP Server

│   └── DC01

├── Scope

│   └── 192.168.56.0/24

├── Reservations

├── Exclusions

└── Clients

    └── Windows 11 Workstations

---

## DHCP Scope Configuration

### Primary Scope

- Network: 192.168.56.0/24
- Scope Name: Internal Network
- Start Range: 192.168.56.100
- End Range: 192.168.56.200
- Subnet Mask: 255.255.255.0
- Lease Duration: 8 Days

### Exclusions

Reserved Infrastructure Range:
- 192.168.56.1 – 192.168.56.99

### Reservations

Reserved addresses may be assigned for:

- Domain Controllers
- DNS servers
- DHCP servers
- Printers
- Network appliances
- Future infrastructure systems

Requirements:

- MAC address documented.
- Reservation approved by Infrastructure Team.
- Reservation recorded in inventory.

---

## DHCP Options

| Option | Description | Value |
|----------|----------|----------|
| 003 | Router (Gateway) | 192.168.56.1 |
| 006 | DNS Servers | 192.168.56.10 |
| 015 | DNS Domain Name | northwind.local |

---

## DHCP Administration Tasks

| Task | Frequency |
|--------|--------|
| Verify DHCP service | Daily |
| Review DHCP logs | Daily |
| Review active leases | Weekly |
| Validate reservations | Weekly |
| Review scope utilization | Monthly |
| Verify DNS registration | Monthly |
| Test lease renewal | Monthly |

---

## DHCP Utilization Thresholds

| Utilization | Status | Action |
|-------------|----------|----------|
| 0–70% | Normal | Monitor |
| 71–85% | Warning | Review leases |
| 86–95% | Critical | Expand scope |
| >95% | Emergency | Immediate escalation |

---

## DHCP Configuration Standards

Requirements:

- DHCP servers must be authorized in Active Directory.
- DHCP scopes must use documented IP ranges.
- Reservations must be approved and documented.
- Domain clients must receive DNS settings automatically.
- Exclusions must protect infrastructure devices.
- DHCP changes require change approval.

---

## DHCP Troubleshooting Playbooks

### Cannot Obtain IP Address

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team

1. Verify network cable or Wi-Fi.
2. Run: ipconfig /all
3. Check for a 169.254.x.x address.
4. Run: ipconfig /release then ipconfig /renew.
5. Verify DHCP service is running on DC01.
6. Review the DHCP lease list.
7. Document the ticket.
8. Close the request.

### APIPA Address (169.254.x.x)

Severity: High
Estimated Resolution: 30–60 minutes
Escalation: Infrastructure Team

1. Verify client connectivity.
2. Confirm DHCP scope has available addresses.
3. Verify DHCP server authorization.
4. Restart the DHCP Client service.
5. Renew the lease.
6. Verify DNS assignment.
7. Document the ticket.

### DHCP Server Unreachable

Severity: High
Estimated Resolution: 30–60 minutes
Escalation: Infrastructure Team

1. Verify DC01 is online.
2. Open DHCP Manager.
3. Verify the DHCP service status.
4. Review Event Viewer.
5. Validate the scope configuration.
6. Test network connectivity.
7. Escalate if unresolved.

### Reservation Not Working

1. Verify MAC address.
2. Verify reservation exists.
3. Release and renew the lease.
4. Remove stale leases.
5. Confirm the client received the reserved address.

### Scope Exhausted

1. Open DHCP Manager.
2. Review address utilization.
3. Remove stale leases.
4. Expand the scope if approved.
5. Document the change.

### Lease Renewal Failure

1. Run: ipconfig /renew.
2. Verify DHCP service.
3. Verify scope availability.
4. Review Event Viewer.
5. Test connectivity.

### PowerShell Administration

Get-DhcpServerv4Scope

Get-DhcpServerv4Lease

Get-DhcpServerv4Reservation

Get-DhcpServerv4OptionValue

ipconfig /release

ipconfig /renew

### Monitoring & Health Checks

Verify:
- DHCP Server service
- Scope utilization
- Active leases
- Reservations
- DHCP logs
- Event Viewer
- DNS registration
- Client connectivity

---

## DHCP Administration Workflow

Request Received
↓
Review Request
↓
Validate Scope
↓
Implement Change
↓
Renew Lease
↓
Test Connectivity
↓
Document
↓
Close Request

---

## Backup Requirements

Before major DHCP changes:

- Verify VM snapshot exists.
- Export DHCP configuration.
- Confirm rollback procedure.
- Update documentation.
- Follow NWT-STD-005.

---

## Validation Checklist

| Validation              | Status   |
| ----------------------- | -------- |
| DHCP Installed          | Verified |
| Scope Configured        | Verified |
| Reservations Tested     | Verified |
| Lease Assignment Tested | Verified |
| DNS Integration Tested  | Verified |
| Event Logs Reviewed     | Verified |
| Documentation Updated   | Complete |

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
