# NWT-ENT-005 Enterprise IP Address Plan

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-005 |
| Document Type | Enterprise Governance Standard |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | June 2026 |

---

## Executive Summary

The Enterprise IP Address Plan defines the IPv4 addressing scheme for the Northwind Technologies Enterprise IT Modernization Project. This document establishes standardized address assignments, DHCP scopes, reserved addresses, and network allocation policies to ensure consistent deployment, simplified administration, and future scalability.

The addressing plan supports centralized management of Windows Server infrastructure, Active Directory Domain Services, enterprise networking, Help Desk operations, and future infrastructure expansion.

---

## Addressing Standards

| Standard           | Value                            |
| ------------------ | -------------------------------- |
| IP Version         | IPv4                             |
| Primary Network    | 192.168.56.0/24                  |
| Addressing Model   | Static Servers / Dynamic Clients |
| DHCP Authority     | DC01                             |
| DNS Authority      | DC01                             |
| Domain             | NORTHWIND.LOCAL                  |
| Address Management | Enterprise Controlled            |

---

## Network Summary

| Network         | Purpose                   | Gateway                      |
| --------------- | ------------------------- | ---------------------------- |
| 192.168.56.0/24 | Enterprise Infrastructure | VirtualBox Host-Only Adapter |

---

## Enterprise Address Allocation

| Range     | Purpose                     |
| --------- | --------------------------- |
| .1-.9     | Infrastructure Reserved     |
| .10-.19   | Enterprise Servers          |
| .20-.49   | Future Infrastructure       |
| .50-.99   | Network Devices             |
| .100-.199 | DHCP Client Pool            |
| .200-.239 | Testing / Temporary Systems |
| .240-.254 | Future Expansion            |

---

## Current Static Assignments

| Hostname | IP Address    | Assignment | Purpose              |
| -------- | ------------- | ---------- | -------------------- |
| DC01     | 192.168.56.10 | Static     | Active Directory     |
| UBUNTU01 | 192.168.56.20 | Static     | Enterprise Help Desk |

---

## DHCP Configuration

| Setting     | Value                         |
| ----------- | ----------------------------- |
| DHCP Server | DC01                          |
| Scope       | 192.168.56.100-192.168.56.199 |
| Lease Time  | 8 Days                        |
| DNS Server  | 192.168.56.10                 |
| Domain Name | NORTHWIND.LOCAL               |

---

## Reserved Ifrastructure Address

| Address | Reserved For           |
| ------- | ---------------------- |
| .1      | Gateway (Host Network) |
| .10     | DC01                   |
| .20     | UBUNTU01               |
| .30     | Future WDS Server      |
| .40     | Future WSUS            |
| .50     | Future SQL             |
| .60     | Future File Server     |

---

## Client Addressing

| Device                             | Addressing |
| ---------------------------------- | ---------- |
| Windows 11 Enterprise              | DHCP       |
| Future Workstations                | DHCP       |
| Test Systems                       | DHCP       |
| Server Administration Workstations | DHCP       |

---

## DNS Configuration

| Setting             | Value                       |
| ------------------- | --------------------------- |
| Primary DNS         | DC01                        |
| DNS Type            | Active Directory Integrated |
| Dynamic Updates     | Secure Only                 |
| Forward Lookup Zone | NORTHWIND.LOCAL             |
| Reverse Lookup Zone | Enabled                     |

---

## Address Assignment Standards

| Assignment | Device Type            |
| ---------- | ---------------------- |
| Static     | Domain Controllers     |
| Static     | Infrastructure Servers |
| Static     | Linux Servers          |
| Static     | Network Services       |
| DHCP       | Enterprise Clients     |
| DHCP       | Test Systems           |
| DHCP       | Temporary VMs          |

---

## IP Assignment Workflow

New Device
      │
      ▼
Server?
      │
 ┌────┴────┐
 │         │
Yes        No
 │          │
Static     DHCP
 │          │
Reserved   Client Pool
 │          │
Document   Automatic
 │          │
Inventory  DNS Registration

---

## Future Address Reservations

| Address | Planned System | Sprint |
| ------- | -------------- | ------ |
| .30     | WDS01          | 6      |
| .40     | WSUS01         | 6      |
| .50     | SQL01          | Future |
| .60     | FILE01         | Future |
| .70     | PRINT01        | Future |

---

## Validation Checklist

| Validation                | Status   |
| ------------------------- | -------- |
| Static Server Addresses   | Verified |
| DHCP Scope                | Verified |
| DNS Resolution            | Verified |
| Client Address Assignment | Verified |
| Reserved Address Ranges   | Verified |
| Documentation Updated     | Complete |

---

## IP Address Management Policy

The following standards apply to all enterprise IP assignments.

| Policy | Standard |
|---------|----------|
| Server Addressing | Static |
| Client Addressing | DHCP |
| Address Documentation | Mandatory |
| Reserved Ranges | Enterprise Controlled |
| DNS Registration | Automatic |
| Address Changes | Change Management Required |

---

## Related Documents

- ENT-001 Company Profile
- ENT-002 Enterprise Architecture
- ENT-003 Enterprise Network Diagram
- ENT-004 Server Inventory
- ENT-006 Enterprise Naming Standards
