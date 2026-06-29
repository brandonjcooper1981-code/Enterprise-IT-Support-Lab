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

# Server Roles

## DC01

Primary Domain Controller

Services

- Active Directory Domain Services
- DNS
- DHCP
- Enterprise File Server
- Authentication
- Group Policy

---

## CLIENT01

Enterprise Windows Workstation

Purpose

- Domain user logins
- Help Desk testing
- File share testing
- Policy testing
- Software deployment testing

---

## osTicket01

Ubuntu Linux Server

Purpose

- Enterprise Help Desk
- Ticket Management
- Technician Portal
- Customer Portal

Software

- Ubuntu Server 24.04
- Apache
- MariaDB
- PHP 8.5
- osTicket 1.18

---

# Network Information

| Network | Value |
|----------|-------|
| Network | 192.168.56.0/24 |
| Domain | lab.local |
| DNS | Active Directory Integrated |
| DHCP | Windows Server 2025 |
| Client Addressing | DHCP |

---

# Enterprise Services

| Service | Server |
|----------|--------|
| Active Directory | DC01 |
| DNS | DC01 |
| DHCP | DC01 |
| SMB Shares | DC01 |
| Authentication | DC01 |
| Group Policy | DC01 |
| Help Desk | osTicket01 |

---

# Authentication Flow

```
User

↓

CLIENT01

↓

Active Directory

↓

Domain Authentication

↓

Group Policy

↓

Mapped Resources

↓

Department Shares
```

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

- Microsoft 365
- Microsoft Entra ID
- Intune
- Defender for Endpoint
- PowerShell Automation
- Wazuh SIEM
- Sysmon
- Windows Event Forwarding
- WSUS
- Windows Deployment Services

---

# Revision History

| Version | Date | Changes |
|----------|------|----------|
| 1.0 | June 2026 | Initial network architecture |
