# NWT-ENT-004 Server Inventory

| Property | Value |
|----------|----------------------------|
| Company | Northwind Technologies |
| Department | Information Technology Services |
| Document ID | NWT-ENT-004 |
| Document Type | Enterprise Governance Standard |
| Classification | Internal Use |
| Version | 1.0 |
| Status | Approved |
| Author | Brandon J. Cooper |
| Owner | ITS |
| Last Updated | June 2026 |

## Executive Summary

The Server Inventory provides a centralized record of all enterprise servers deployed within the Northwind Technologies Enterprise IT Modernization Project. This inventory documents server roles, operating systems, hardware allocations, network configurations, installed services, and lifecycle status to support administration, maintenance, troubleshooting, and future expansion.

---

## Inventory Summary

| Metric              | Value             |
| ------------------- | ----------------- |
| Total Servers       | 2                 |
| Windows Servers     | 1                 |
| Linux Servers       | 1                 |
| Domain Controllers  | 1                 |
| Application Servers | 1                 |
| Virtual Machines    | 3                 |
| Hypervisor          | Oracle VirtualBox |

---

## Operational Status

| Server   | Status      | Last Verified |
|----------|-------------|-------------- |
| DC01     | Operational | Sprint 1      |
| UBUNTU01 | Operational | Sprint 1      |

---

## Server Inventory Table

| Hostname   | Operating System        | Role                     | Status      |
| ---------- | ----------------------- | ------------------------ | ----------- |
| DC01       | Windows Server 2025     | Domain Controller        | Operational |
| UBUNTU01   | Ubuntu Server 24.04 LTS | Linux Application Server | Operational |

---

## Enterprise Server Assets

---

## Virtual Machine Standards

| Resource  | Domain Controller | Linux Server    |
|-----------|-------------------|-----------------|
| CPU       | 2 vCPU            | 2 vCPU          |
| Memory    | 4 GB              | 4 GB            |
| Disk      | 80 GB             | 80 GB           |
| Network   | NAT + Host Only   | NAT + Host Only |

## DC01

### Asset Classification

| Classification          | Value             |
| ----------------------- | ----------------- |
| Criticality             | Tier 1 (Critical) |
| Business Impact         | High              |
| Authentication Required | Yes               |
| Domain Joined           | Yes               |
| Internet Facing         | No                |
| Data Classification     | Internal          |
| Asset ID                | SRV-001           |
| Hostname                | DC01              |

### General Information

| Property         | Value                   |
| ---------------- | ----------------------- |
| Hostname         | DC01                    |
| Operating System | Windows Server 2025     |
| Server Role      | Domain Controller       |
| Platform         | Oracle VirtualBox 7.x   |
| Status           | Operational             |
| Environment      | Production Lab          |

### Hardware

| Resource | Allocation                              |
| -------- | --------------------------------------- |
| CPU      | 2 vCPU                                  |
| Memory   | 4 GB                                    |
| Disk     | 80 GB                                   |
| Network  | Adapter 1 (NAT) + Adpater 2 (Host-Only) |

### Network

| Property   | Value           |
| ---------- | --------------- |
| IP Address | 192.168.56.10   |
| DNS        | Self            |
| DHCP       | Local           |
| Domain     | NORTHWIND.LOCAL |

### Installed Roles

- Active Directory Domain Services
- DNS Server
- DHCP Server
- File Services
- Group Policy

### Enterprise Responsibilities

- Authentication
- Authorization
- Centralized Administration
- DNS
- DHCP
- File Shares
- Group Policy

### Validation Status

| Validation           | Status   |
|----------------------|----------|
| Operating System     | Verified |
| Network Connectivity | Verified |
| DNS Resolution       | Verified |
| Authentication       | Verified |
| Installed Services   | Verified |
| Documentation        | Complete |

### Dependencies

Depends On
- Oracle VirtualBox
- Host Network
Supports
- CLIENT01
- UBUNTU01

---

## UBUNTU01

### Asset Classification

| Classification          | Value                         |
| ----------------------- | ----------------------------- |
| Criticality             | Tier 2 (Business Application) |
| Business Impact         | Medium                        |
| Authentication Required | Yes                           |
| Domain Joined           | No *(currently)*              |
| Internet Facing         | No                            |
| Data Classification     | Internal                      |
| Asset ID                | SRV-002                       |
| Hostname                | UBUNTU01                      |


### General Information

| Property         | Value                         |
| ---------------- | ----------------------------- |
| Hostname         | UBUNTU01                      |
| Operating System | Ubuntu Server 24.04 LTS       |
| Server Role      | Enterprise Application Server |
| Platform         | Oracle VirtualBox 7.x         |
| Status           | Operational                   |
| Environment      | Production Lab                |

### Hardware

| Resource | Allocation                              |
| -------- | --------------------------------------- |
| CPU      | 2 vCPU                                  |
| Memory   | 4 GB                                    |
| Disk     | 80 GB                                   |
| Network  | Adapter 1 (NAT) + Adpater 2 (Host-Only) |

### Installed Services

- Apache 2.4
- PHP 8.5
- MariaDB 11
- osTicket 1.18
- SSH

### Enterprise Responsibilities

- Help Desk
- Ticket Management
- Linux Services
- Future Wazuh

### Validation Status

| Validation           | Status   |
|----------------------|----------|
| Operating System     | Verified |
| Network Connectivity | Verified |
| DNS Resolution       | Verified |
| Authentication       | Verified |
| Installed Services   | Verified |
| Documentation        | Complete |

### Dependencies
Depends On
- DC01 (DNS)
- Enterprise Network
Supports
- Help Desk Users

---

## Lifecycle Status

| Server     | Current State | Next Planned Upgrade  |
| ---------- | ------------- | --------------------- |
| DC01       | Production    | PowerShell Automation |
| UBUNTU01   | Production    | Wazuh Integration     |

---

## Backup Strategy

| Component        | Method                           |
| ---------------- | -------------------------------- |
| Virtual Machines | VirtualBox Snapshots             |
| Windows Server   | Windows Server Backup *(Future)* |
| Ubuntu Server    | Configuration Export *(Future)*  |
| Database         | MariaDB Backup *(Future)*        |
| Documentation    | GitHub Repository                |

---

## Monitoring

| Status  | Technology               |
| ------- | ------------------------ |
| Current | Windows Event Viewer     |
| Planned | Sysmon                   |
| Planned | Wazuh                    |
| Planned | Windows Event Forwarding |
| Planned | Health Monitoring        |

---

## Maintenance Schedule

| Task                 | Frequency      |
| -------------------- | -------------- |
| Windows Updates      | Monthly        |
| Ubuntu Updates       | Monthly        |
| Snapshot             | Before Changes |
| Documentation Review | Quarterly      |

---

## Furture Servers

| Hostname | Planned Role        | Sprint |
| -------- | ------------------- | ------ |
| WDS01    | Deployment Services | 6      |
| WSUS01   | Update Services     | 6      |
| SQL01    | Database            | Future |
| FILE01   | Enterprise Storage  | Future |
| PRINT01  | Print Services      | Future |

---

## Related Documentation

- ENT-001 Company Profile
- ENT-002 Enterprise Architecture
- ENT-003 Enterprise Network Diagram
- ENT-005 IP Address Plan
- ENT-006 Enterprise Naming Standards

---






