# NWT-SOP-009 Wazuh SIEM Administaation SOP

| Property | Value |
|----------|----------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-009 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain the Northwind Technologies Wazuh Security Information and Event Management (SIEM) platform.

The Wazuh platform provides centralized log collection, endpoint monitoring, security event detection, compliance reporting, and incident visibility across the Northwind Technologies infrastructure.

---

## Purpose

This SOP defines standards and procedures for:
- Wazuh administration
- Agent management
- Log collection
- Security monitoring
- Rule management
- Alert triage
- Dashboard administration
- User management
- System health monitoring
- Incident investigation
- Backup and recovery
- Security controls

---

## Scope

Applies to:
- Ubuntu Server 24.04
- Wazuh Server
- Wazuh Dashboard
- Wazuh Indexer
- Windows Server 2025
- Windows 11 workstations
- Active Directory
- Sysmon
- osTicket integration
- Security Operations
- Future cloud workloads

---

## Supported Systems

- WAZUH01
- DC01
- CLIENT01
- Ubuntu Server 24.04
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer
- Sysmon
- Windows Event Logs
- northwind.local

---

## Administrative Tools

Authorized tools include:
- Wazuh Dashboard
- Ubuntu Terminal
- SSH
- PowerShell
- Event Viewer
- Sysmon
- journalctl
- systemctl
- curl
- nano
- Wazuh API (future)

---

## Roles & Responsibilities

| Role                 | Responsibility              |
| -------------------- | --------------------------- |
| CIO                  | Approves security standards |
| Security Team        | SIEM monitoring             |
| Infrastructure Lead  | Platform administration     |
| System Administrator | Agent maintenance           |
| Help Desk            | Tier 1 troubleshooting      |
| Documentation Owner  | SOP maintenance             |

---

## Wazuh Architesture

Northwind Technologies

├── WAZUH01
│
├── Wazuh Manager
│
├── Wazuh Dashboard
│
├── Wazuh Indexer
│
├── Agents
│   ├── DC01
│   ├── CLIENT01
│   └── Future Servers
│
├── Log Sources
│   ├── Windows Event Logs
│   ├── Sysmon
│   ├── Security Logs
│   └── Application Logs
│
└── Integrations
    ├── osTicket (Future)
    ├── Active Directory
    └── Microsoft Sentinel (Future)

---

## Agent Management Standards

Requirements:
- All production systems require Wazuh agents.
- Agents must report every 10 minutes or less.
- Agent names must match hostnames.
- Unauthorized agents must be removed.
- Agent health must be reviewed weekly.

---

## Alert Severity Levels

| Severity | Description         |
| -------- | ------------------- |
| Critical | Active compromise   |
| High     | Security incident   |
| Medium   | Suspicious activity |
| Low      | Informational event |
| Info     | System status       |

---

## Administrative Tasks

| Task                    | Frequency |
| ----------------------- | --------- |
| Review alerts           | Daily     |
| Verify agent status     | Daily     |
| Review failed logins    | Daily     |
| Review dashboard health | Weekly    |
| Update rules            | Monthly   |
| Validate backups        | Quarterly |

---

## Monitoring Categories

Monitor:
- Failed logons
- Account lockouts
- Group membership changes
- PowerShell execution
- Sysmon events
- New services
- Software installation
- Firewall events
- Privilege escalation
- Endpoint health

---

## Incident Workflow

Alert Generated
      ↓
Initial Triage
      ↓
Severity Classification
      ↓
Investigation
      ↓
Containment (if required)
      ↓
Escalation
      ↓
Resolution
      ↓
Documentation
      ↓
Ticket Closure

---

## Troubleshooting Playbooks
### Agent Offline

Severity: High
1. Verify server connectivity.
2. Ping WAZUH01.
3. Verify Wazuh service status.
4. Restart Wazuh agent.
5. Review logs.
6. Re-register the agent if necessary.
7. Document ticket.

### Dashboard Unavailable

Severity: High
1. Verify Ubuntu connectivity.
2. Check Wazuh Dashboard service.
3. Review disk space.
4. Review logs.
5. Restart dashboard services.
6. Escalate if unresolved.

### No Logs Received

Severity: Critical
1. Verify agent status.
2. Check Windows Event Viewer.
3. Verify Sysmon service.
4. Restart Wazuh agent.
5. Review Wazuh Manager logs.
6. Confirm firewall rules.
7. Document ticket.

### High CPU / Memory Usage

Severity: Medium
1. Review running processes.
2. Check active alerts.
3. Review indexer health.
4. Restart affected service.
5. Escalate if unresolved.

---

## Linux Commands

```bash
sudo journalctl -u wazuh-dashboard

sudo journalctl -u wazuh-indexer

sudo systemctl status wazuh-manager

sudo systemctl restart wazuh-manager

sudo systemctl status wazuh-dashboard

sudo systemctl restart wazuh-dashboard

sudo systemctl status wazuh-indexer

sudo systemctl restart wazuh-indexer

sudo systemctl status wazuh-agent

sudo journalctl -u wazuh-manager

sudo tail -f /var/ossec/logs/ossec.log

sudo ss -tulnp

df -h

free -h

top

htop
```

---

## Monitoring & Health Checks

Verify:
- Wazuh Manager status
- Dashboard availability
- Indexer status
- Agent connectivity
- Disk utilization
- Memory usage
- Alert processing
- Sysmon ingestion
- Windows log collection
- SSL certificate health

---

## Backup Requirements

Before major changes:
- Verify VM snapshot exists.
- Export configuration files.
- Backup rules and decoders.
- Verify rollback plan.
- Update documentation.
- Test restoration quarterly.
- Follow NWT-STD-006.

---

## Security Requirements

Requirements include:
- Least privilege
- Role-based access control
- MFA (future)
- Audit logging
- Patch management
- Rule approval
- Agent verification
- Quarterly access review

---

## Validation Checklist

| Validation            | Status   |
| --------------------- | -------- |
| Manager Running       | Verified |
| Dashboard Accessible  | Verified |
| Indexer Healthy       | Verified |
| Agents Connected      | Verified |
| Sysmon Logs Received  | Verified |
| Alerts Generated      | Verified |
| Documentation Updated | Complete |

---

## Future Improvements

- Active Directory authentication
- Microsoft Sentinel integration
- osTicket automation
- Threat intelligence feeds
- Email alerting
- Docker deployment
- Cloud monitoring
- Automated incident response

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
