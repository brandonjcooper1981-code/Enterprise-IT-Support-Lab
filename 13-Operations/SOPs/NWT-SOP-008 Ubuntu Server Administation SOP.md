# NWT-SOP-008 Ubuntu Server Administration SOP

| Property | Value |
|----------|----------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-008 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain Ubuntu Server systems throughout the Northwind Technologies environment.

The Ubuntu server environment supports security monitoring, ticketing systems, centralized logging, future automation services, and enterprise applications.

---

## Purpose

This SOP defines standards and procedures for:
- Ubuntu server administration
- User and group management
- Package management
- Service administration
- Network configuration
- SSH administration
- Storage management
- Log management
- System monitoring
- Troubleshooting
- Backup and recovery
- Security controls

---

## Scope

Applies to:
- Ubuntu Server 24.04
- Virtual machines
- Wazuh server
- osTicket server
- SSH access
- Network services
- System services
- Package repositories
- Future cloud integrations

---

## Supported Systems

- UBUNTU01
- WAZUH01
- OsTicket01
- Ubuntu Server 24.04
- OpenSSH
- Apache
- MariaDB
- Wazuh
- osTicket
- Northwind.local

---

## Administrative Tools

Authorized tools include:
- Terminal
- SSH
- Nano
- Vim
- systemctl
- journalctl
- apt
- netplan
- htop
- PowerShell (remote)
- Wazuh (future)

---

## Role & Responsibilities

| Role                 | Responsibility           |
| -------------------- | ------------------------ |
| CIO                  | Approves Linux standards |
| Infrastructure Lead  | Server administration    |
| System Administrator | Ubuntu maintenance       |
| Security Team        | Log review               |
| Help Desk            | Tier 1 troubleshooting   |
| Documentation Owner  | SOP maintenance          |

---

## Ubuntu Architecture

Northwind Technologies

├── Ubuntu Servers
│
├── WAZUH01
│   ├── Manager
│   ├── Dashboard
│   └── Agents
│
├── OSTICKET01
│   ├── Apache
│   ├── PHP
│   └── MariaDB
│
├── Services
│   ├── SSH
│   ├── Networking
│   ├── Logging
│   └── Updates
│
└── Future Services
    ├── Docker
    ├── Automation
    └── Cloud

---

## User Administration Standards

Requirements:
- Disable root SSH login.
- Use sudo for administrative access.
- Remove inactive accounts.
- Enforce least privilege.
- Review users quarterly.

---

## Service Management

| Service         | Purpose               |
| --------------- | --------------------- |
| ssh             | Remote administration |
| apache2         | Web services          |
| mariadb         | Database              |
| wazuh-manager   | SIEM management       |
| wazuh-dashboard | Web dashboard         |

---

## Package Management Standards

Requirements:
- Install updates monthly.
- Test major updates before deployment.
- Remove unsupported packages.
- Review repositories quarterly.
- Document package changes.

---

## Administrative Tasks

| Task                 | Frequency |
| -------------------- | --------- |
| Review logs          | Daily     |
| Verify services      | Daily     |
| Check disk space     | Weekly    |
| Review user accounts | Monthly   |
| Install updates      | Monthly   |
| Validate backups     | Quarterly |

---

## Troubleshooting Playbooks

### SSH Connection Failure

Severity: High
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify network connectivity.
2. Ping the server.
3. Verify SSH service status.
4. Review firewall rules.
5. Restart SSH.
6. Review logs.
7. Document ticket.

### Service Will Not Start

Severity: High
1. Verify service status.
2. Review journal logs.
3. Check disk space.
4. Validate configuration files.
5. Restart service.
6. Escalate if unresolved.

### Package Update Failure

Severity: Medium
1. Verify Internet connectivity.
2. Run update commands.
3. Review repository configuration.
4. Check package locks.
5. Retry installation.
6. Document ticket.

### Disk Space Full

Severity: High
1. Review storage utilization.
2. Locate large files.
3. Clear logs.
4. Remove temporary files.
5. Extend storage if approved.
6. Document ticket.

### High CPU / Memory Usage

Severity: Medium
1. Review active processes.
2. Check running services.
3. Review logs.
4. Restart affected service.
5. Escalate if unresolved.

---

## Linux Administration Commands

```bash
sudo systemctl status ssh

sudo systemctl restart ssh

sudo apt update

sudo apt upgrade

sudo apt autoremove

sudo journalctl -xe

sudo tail -f /var/log/syslog

sudo ss -tulnp

sudo ufw status

df -h

free -h

top

htop

sudo reboot
```

---

## Monitoring & Health Checks

Verify:
- SSH service status
- Disk utilization
- CPU usage
- Memory usage
- Package updates
- Failed logins
- Service availability
- Network connectivity
- Log health

---

## Backup Requirements

Before major changes:
- Verify VM snapshot exists.
- Export configurations.
- Verify rollback plan.
- Update documentation.
- Test restoration quarterly.
- Follow NWT-STD-006.

---

## Security Requirements

Requirements include:
- Least privilege
- SSH key authentication (future)
- Firewall enabled
- Audit logging
- Patch management
- Change approval
- Account review

---

## Validation Checklist

| Validation            | Status   |
| --------------------- | -------- |
| SSH Configured        | Verified |
| Services Running      | Verified |
| Updates Installed     | Verified |
| Firewall Reviewed     | Verified |
| Logs Reviewed         | Verified |
| Documentation Updated | Complete |


---

## Future Improvements

- Docker
- Kubernetes
- Ansible
- Azure integration
- Microsoft Sentinel
- Wazuh monitoring
- SSH key enforcement
- Patch automation

---

## Related Documentation

- NWT-SOP-007 osTicket Administration SOP
- NWT-SOP-009 Wazuh SIEM Administration SOP
- NWT-SOP-002 Help Desk Operations SOP
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
