# NWT-RUN-012 Ubuntu Service Failure

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-012                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure / Security Operations  |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve Ubuntu service failures within the Northwind Technologies environment.

This runbook applies to infrastructure services hosted on Ubuntu systems, including Wazuh, osTicket, Apache, MariaDB, Filebeat, and future Linux-based enterprise services.

---

## Symptoms

- Service fails to start.
- Users cannot access hosted applications.
- SSH sessions disconnect unexpectedly.
- Web applications return errors.
- Security monitoring stops reporting.
- Scheduled tasks fail.
- Users receive:
    - "Service unavailable."
    - "Connection refused."
    - "Failed to start service."
    - "Host unreachable."
    - "Internal Server Error."

---

## Systems Affected

- WAZUH01
- osTicket01
- Ubuntu Server
- Apache Web Server
- MariaDB Database
- Wazuh Manager
- Filebeat
- SSH
- northwind.local

---

## Core Services

| Service       | Purpose                   |
| ------------- | ------------------------- |
| Apache2       | Web hosting               |
| MariaDB       | Database engine           |
| Wazuh Manager | Security event collection |
| Filebeat      | Log forwarding            |
| SSH           | Remote administration     |
| Cron          | Scheduled jobs            |
| UFW           | Firewall management       |
| Systemd       | Service management        |

---

## Investigation

1. Verify user identity.
2. Confirm network connectivity.
3. Verify server reachability: ```bash ping WAZUH01```
4. Verify DNS resolution: ```bash nslookup WAZUH01```
5. Review service status:
```bash
sudo systemctl status apache2
sudo systemctl status mariadb
sudo systemctl status wazuh-manager
sudo systemctl status filebeat
```
6. Review failed services: ```bash sudo systemctl --failed```
7. Review disk utilization: ```bash df -h```
8. Review memory utilization: ```bash free -h```
9. Review active processes: ```bash top```
10. 10. Review system logs:
```bash
sudo journalctl -xe
sudo journalctl -p err
```

---

## Resolution

1. Restart affected services: ```bash sudo systemctl restart <service>```
2. Verify service startup: ```bash sudo systemctl status <service>```
3. Restart the server if required: ```bash sudo reboot```
4. Verify disk space availability.
5. Verify firewall configuration: ```bash sudo ufw status```
6. Verify port availability: ```bash sudo ss -tulpn```
7. Verify service dependencies: ```bash sudo systemctl list-dependencies <service>```
8. Review application logs.
9. Escalate if service failures persist.

---

## Validation

- Service status shows Active (running).
- Hosted applications respond normally.
- Users can connect successfully.
- Monitoring resumes.
- No new errors appear in logs.
- Dashboard services load correctly.

---

## Escalation Criteria

Escalate if:
- Multiple services fail simultaneously.
- Disk utilization exceeds 90%.
- Memory exhaustion occurs.
- Service repeatedly crashes.
- Server becomes unreachable.
- Data corruption is suspected.

---

## Key Logs/Event IDs

| Log                          | Description      |
| ---------------------------- | ---------------- |
| `/var/log/syslog`            | System events    |
| `/var/log/auth.log`          | Authentication   |
| `journalctl -xe`             | Service failures |
| `journalctl -p err`          | Errors only      |
| `/var/log/apache2/error.log` | Apache errors    |
| `/var/ossec/logs/ossec.log`  | Wazuh logs       |

---

## Common Commands

sudo systemctl --failed

sudo systemctl status apache2

sudo systemctl status mariadb

sudo systemctl status wazuh-manager

sudo systemctl status filebeat

sudo journalctl -xe

sudo journalctl -p err

df -h

free -h

top

sudo ss -tulpn

sudo ufw status

sudo reboot

---

## Related Documentation

- NWT-RUN-010 osTicket Service Outage
- NWT-RUN-011 Wazuh Agent Offline
- NWT-RUN-013 Security Alert Investigation
- NWT-SOP-003 DNS Administration SOP

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
