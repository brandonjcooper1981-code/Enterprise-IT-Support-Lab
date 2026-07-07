# Enterprise Network Diagram

Version: 1.0

---

# Overview

This document describes the logical architecture of the Enterprise IT Support Lab.

The environment simulates a small-to-medium business infrastructure using Windows Server, Active Directory, enterprise file services, DHCP, DNS, Windows 11 clients, Ubuntu Linux, and osTicket.

---

# Enterprise Architecture

```
                               Internet
                                   │
                           Home Router / ISP
                                   │
                        ┌────────────────────┐
                        │   VirtualBox Host  │
                        │ Windows 11 Desktop │
                        └────────────────────┘
                                   │
                 VirtualBox Host-Only Network (192.168.56.0/24)
                                   │
        ┌──────────────────────────┼──────────────────────────┐
        │                          │                          │
        │                          │                          │
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│      DC01       │      │    CLIENT01     │      │   osTicket01    │
│ Windows Server  │      │ Windows 11 Pro  │      │ Ubuntu Server   │
│                 │      │                 │      │                 │
│ Active Directory│      │ Domain Joined   │      │ Apache          │
│ DNS             │      │ Help Desk User  │      │ PHP             │
│ DHCP            │      │ Test Workstation│      │ MariaDB         │
│ SMB Shares      │      │                 │      │ osTicket        │
└─────────────────┘      └─────────────────┘      └─────────────────┘
```

---

## Network Design Principles

Northwind Technologies follows a centralized network architecture designed to simplify administration, improve security, and support future enterprise expansion.

Design principles include:

- Centralized identity management
- DNS-integrated Active Directory
- Static addressing for infrastructure servers
- DHCP for enterprise workstations
- Segmented departmental resources
- Least-privilege access through security groups
- Standardized network configurations

---

# Server Roles

## Server Roles

| Server | Operating System | Primary Role | Services |
|---------|-----------------|--------------|--------------------------------|
| DC01 | Windows Server 2025 | Domain Controller | AD DS, DNS, DHCP, SMB |
| CLIENT01 | Windows 11 Enterprise | Enterprise Workstation | Authentication, GPO Testing |
| osTicket01 | Ubuntu Server | Linux Application Server | Apache, PHP, MariaDB, osTicket |

---

## Network Information

| Property | Value |
|----------|--------------------------------|
| Network Name | VirtualBox Host-Only |
| IPv4 Network | 192.168.56.0/24 |
| Gateway | Host Adapter |
| DNS Server | DC01 |
| DHCP Server | DC01 |
| Domain | NORTHWIND.LOCAL |
| Addressing | Static Servers / DHCP Clients |
| Internet Access | NAT Adapter |

---

## Enterprise Services

| Service | Server | Purpose |
|----------|---------|------------------------------|
| Active Directory | DC01 | Identity Management |
| DNS | DC01 | Name Resolution |
| DHCP | DC01 | IP Address Assignment |
| SMB | DC01 | File Services |
| Group Policy | DC01 | Enterprise Configuration |
| Authentication | DC01 | Domain Logons |
| Help Desk | osTicket01 | Ticket Management |

---

## Authentication Flow

```
User
↓
CLIENT01
↓
DNS Resolution
↓
DC01
↓
Active Directory
↓
Authentication
↓
Group Policy
↓
Security Groups
↓
Mapped Drives
↓
Department Resources
```
---

## Enterprise Communication Matrix

| Source | Destination | Protocol | Purpose |
|----------|-------------|----------|--------------------|
| CLIENT01 | DC01 | DNS | Name Resolution |
| CLIENT01 | DC01 | Kerberos | Authentication |
| CLIENT01 | DC01 | SMB | File Shares |
| CLIENT01 | DC01 | LDAP | Active Directory |
| CLIENT01 | osTicket01 | HTTP/HTTPS | Help Desk |
| osTicket01 | Internet | HTTPS | Package Updates |

---

## Network Ports

| Service | Protocol | Port | Used By |
|----------|----------|------|------------------|
| DNS | TCP/UDP | 53 | CLIENT01 → DC01 |
| DHCP | UDP | 67/68 | CLIENT01 → DC01 |
| Kerberos | TCP/UDP | 88 | CLIENT01 → DC01 |
| LDAP | TCP | 389 | CLIENT01 → DC01 |
| SMB | TCP | 445 | CLIENT01 → DC01 |
| HTTPS | TCP | 443 | CLIENT01 → osTicket01 |
| HTTP | TCP | 80 | CLIENT01 → osTicket01 |

---

# File Services

Enterprise department shares

- HR
- Finance
- Executive
- Engineering
- Marketing
- Operations
- Sales
- IT
- Public
- Software

Permissions are managed using:

- Active Directory Security Groups
- SMB Share Permissions
- NTFS Permissions

---

# Future Expansion

The following systems will be integrated later.

Sprint 2
---------
PowerShell

Sprint 3
---------
osTicket Expansion

Sprint 4
---------
Sysmon
Wazuh
Windows Event Forwarding

Sprint 5
---------
Microsoft 365
Entra ID
Intune

Sprint 6
---------
WSUS
Windows Deployment Services

Future
---------
Azure
Hybrid Identity

---

# Revision History

| Version | Date | Changes |
|----------|------|----------|
| 1.0 | June 2026 | Initial network architecture |
