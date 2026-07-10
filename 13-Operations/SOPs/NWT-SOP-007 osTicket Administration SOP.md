# NWT-SOP-007 osTicket Administration SOP

| Property | Value |
|----------|----------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-007 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This Standard Operating Procedure establishes the processes used by Information Technology Services (ITS) to administer, monitor, troubleshoot, secure, and maintain the Northwind Technologies osTicket environment.

The ticketing system supports incident management, service requests, user communication, workflow automation, knowledge management, and operational reporting.

---

## Purpose

This SOP defines standards and procedures for:
- osTicket administration
- Ticket lifecycle management
- User and agent management
- Department management
- SLA administration
- Queue management
- Knowledge base management
- Email configuration
- Ticket troubleshooting
- Monitoring and health checks
- Backup and recovery
- Security controls

---

## Scope

Applies to:
- osTicket Server
- Ubuntu Server 24.04
- Apache / Nginx
- MariaDB / MySQL
- PHP
- Help Desk agents
- Departments
- Ticket queues
- Email pipelines
- Knowledge Base
- Future SSO integrations

---

## Supported Systems
- osTicket01
- Ubuntu Server
- osTicket
- Apache Web Server
- MariaDB
- PHP
- Northwind.local
- Help Desk workstations
- Email services

---

## Administrative Tools

Authorized tools include:
- osTicket Admin Panel
- osTicket Agent Panel
- Ubuntu Terminal
- SSH
- Apache
- MariaDB
- PowerShell
- Web Browser
- Wazuh (Future)

---

## Roles & Responsibilities

| Role                 | Responsibility               |
| -------------------- | ---------------------------- |
| CIO                  | Approves ticketing standards |
| Infrastructure Lead  | Server administration        |
| Help Desk Manager    | Queue administration         |
| Help Desk Agent      | Ticket processing            |
| System Administrator | osTicket maintenance         |
| Documentation Owner  | SOP maintenance              |

---

## osTicket Architecture

Northwind Technologies

├── osTicket Server
│
├── Web Server
│   └── Apache
│
├── Database
│   └── MariaDB
│
├── Departments
│   ├── Help Desk
│   ├── Infrastructure
│   ├── Security
│   └── Management
│
├── Ticket Queues
│   ├── Open
│   ├── Assigned
│   ├── Overdue
│   └── Closed
│
└── Knowledge Base

---

## Ticket Lifecycle

Ticket Created
        ↓
Auto Assignment
        ↓
Agent Review
        ↓
Troubleshooting
        ↓
Escalation (if needed)
        ↓
Resolution
        ↓
User Confirmation
        ↓
Ticket Closed

---

## Ticket Priorities

| Priority |   Response Goal |
| -------- | --------------: |
| Critical |          1 hour |
| High     |         4 hours |
| Medium   |  1 business day |
| Low      | 3 business days |

---

## Department Structure

- Help Desk
- Infrastructure
- Security
- Systems Administration
- Management

---

## Depaartment/Queue Ownership

| Queue          | Owner               |
| -------------- | ------------------- |
| Help Desk      | Help Desk Team      |
| Infrastructure | Infrastructure Team |
| Security       | Security Team       |
| Management     | Management          |

---

## Administratice Tasks

| Task                     | Frequency |
| ------------------------ | --------- |
| Review open tickets      | Daily     |
| Review overdue tickets   | Daily     |
| Verify email delivery    | Daily     |
| Review agent assignments | Weekly    |
| Review SLA compliance    | Weekly    |
| Review system logs       | Monthly   |
| Backup database          | Monthly   |

---

## Configuration Standards

Requirements:
- All tickets must have an owner.
- Departments must be documented.
- SLAs must be assigned.
- Ticket priorities must follow company standards.
- Administrative access requires approval.
- Audit logs must remain enabled.

---

## Troubleshooting Playbooks

### Users Cannot Create Tickets

Severity: High
1. Verify web server availability.
2. Verify DNS resolution.
3. Confirm email configuration.
4. Verify database connectivity.
5. Review Apache logs.
6. Test portal access.
7. Document ticket.

### Agent Cannot Log In

Severity: High
1. Verify account status.
2. Reset password.
3. Verify group membership.
4. Review authentication logs.
5. Test browser session.
6. Document ticket.

### Email Not Importing

Severity: High
1. Verify mailbox credentials.
2. Review IMAP/SMTP settings.
3. Test mail connectivity.
4. Restart mail fetch service.
5. Review logs.
6. Verify ticket creation.

### Database Connection Failure

Severity: Critical
1. Verify MariaDB service status.
2. Verify database credentials.
3. Check disk utilization.
4. Review logs.
5. Restart services.
6. Escalate if unresolved.

---

## Administrative Commands

```cmd
sudo systemctl status apache2

sudo systemctl restart apache2

sudo systemctl status mariadb

sudo systemctl restart mariadb

sudo systemctl status ssh

sudo tail -f /var/log/apache2/error.log

sudo mysql -u root -p

df -h

free -h
```

---

## Monitoring & Health Checks

Verify:
- Web server status
-  Database status
- Ticket queue health
- Email delivery
- Agent access
- Disk space
- Memory usage
- System logs

---

## Backup Requirements

Before major changes:
- Verify VM snapshot exists.
- Export database backup.
- Verify rollback plan.
- Update documentation.
- Follow NWT-STD-006.
- Test restoration procedure quarterly.

---

## Future Improvements
- Active Directory authentication
- SSO integration
- LDAP synchronization
- Microsoft Teams integration
- Wazuh monitoring
- Automated ticket routing
- Asset management integration

---

## Related Documentation
- NWT-SOP-002 Help Desk Operations SOP
- NWT-SOP-008 Ubuntu Server Administration SOP
- NWT-SOP-009 Wazuh SIEM Administration SOP
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard

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
