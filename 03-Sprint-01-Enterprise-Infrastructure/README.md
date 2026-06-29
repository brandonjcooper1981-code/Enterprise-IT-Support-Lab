Company: Northwind Technologies

Department: Information Technology Services (ITS)

Section: Sprint 01 – Enterprise Infrastructure

Document Type: Navigation

Classification: Internal Use

Repository: Enterprise IT Support Lab

Status: Active

Version: 1.0

Last Updated: June 2026

# Sprint 1 – Enterprise Infrastructure

## Objective

Deploy the foundational infrastructure required for a production-inspired enterprise environment.

---

# Completed

- Installed Windows Server 2025
- Promoted Domain Controller
- Configured Active Directory
- Configured DNS
- Configured DHCP
- Joined Windows 11 workstation
- Installed Ubuntu Server
- Installed osTicket
- Created Enterprise Organizational Units
- Created Department Security Groups
- Created Enterprise User Accounts
- Configured Enterprise File Shares
- Configured NTFS Permissions
- Configured Share Permissions

---

# Enterprise Organizational Units

- Executive
- Finance
- HR
- IT
- Engineering
- Marketing
- Operations
- Sales
- Servers
- Workstations
- HelpDesk-Lab

---

# Department Shares

- Executive
- Finance
- HR
- IT
- Engineering
- Marketing
- Operations
- Sales
- Public
- Software

---

# Enterprise Applications

- Active Directory
- DNS
- DHCP
- Windows File Services
- osTicket
- Apache
- MariaDB
- PHP

---

# Skills Demonstrated

- Active Directory Administration
- DNS
- DHCP
- Windows Server Administration
- Enterprise File Services
- NTFS Permissions
- Share Permissions
- Windows 11 Administration
- Linux Administration
- Apache
- MariaDB
- PHP
- osTicket
- Troubleshooting

---

# Troubleshooting

## VirtualBox Guest Additions

Problem

Shared folders would not mount.

Resolution

Installed Guest Additions, loaded VBoxSF modules, and mounted shared folders manually.

---

## osTicket Installation

Problem

GitHub download returned HTTP 404.

Resolution

Downloaded manually and transferred using VirtualBox Shared Folders.

---

## PHP Extensions

Problem

Installer failed prerequisite checks.

Resolution

Installed missing PHP extensions and restarted Apache.

---

## File Permissions

Problem

Apache could not create osTicket configuration files.

Resolution

Corrected Linux ownership and permissions.

---

## NTFS Permissions

Problem

Inherited permissions granted unnecessary access.

Resolution

Disabled inheritance and assigned department security groups.

---

## DHCP

Configured DHCP scope

Reserved CLIENT01

Verified DNS registration

Validated lease assignments

---

# Lessons Learned

- Enterprise Active Directory design
- DHCP deployment
- DNS integration
- Windows File Server
- NTFS permissions
- Share permissions
- Ubuntu administration
- Apache administration
- osTicket deployment
- Linux troubleshooting
- VirtualBox administration
