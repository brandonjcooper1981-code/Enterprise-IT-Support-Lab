# NWT-RUN-010 osTicket Service Outage

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-010                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve osTicket service outages within the Northwind Technologies environment.

This runbook applies to both the current osTicket deployment and future service desk infrastructure planned within Northwind Technologies.

---

## Symptoms

- Users cannot access the help desk portal.
- Ticket submission fails.
- Agents cannot log in.
- Pages fail to load.
- Users receive:
    - "Unable to connect."
    - "This site can't be reached."
    - "500 Internal Server Error."
    - "503 Service Unavailable."
    - "Connection timed out."
- Email-to-ticket processing stops.
- Ticket notifications fail.

---

## Systems Affected

- osTicket01
- Apache Web Server
- MariaDB/MySQL Database
- PHP Services
- DNS Server
- CLIENT01
- Windows 11 workstations
- northwind.local

---

## Core Services

| Service | Purpose                                   |
| ------- | ----------------------------------------- |
| Apache2 | Hosts the osTicket web application        |
| MariaDB | Stores ticket data                        |
| PHP     | Processes application requests            |
| SSH     | Remote administration and troubleshooting |
| DNS     | Name resolution                           |
| SMTP    | Email-to-ticket processing (Future)       |

---

## Investigation

1. Verify user identity.
2. Confirm workstation network connectivity.
3. Verify that osTicket01 is reachable: ```ping osTicket01```
4. Verify DNS resolution: ```nslookup osTicket01```
5. Connect to osTicket01 via SSH: ```ssh administrator@osTicket01```
6. Verify Apache status: ```sudo systemctl status apache2```
7. Verify database status: ```sudo systemctl status mariadb```
8. Verify disk utilization: ```df -h```
9. Verify listening services: ```sudo ss -tulnp```
10. Review system logs:
    - ```/var/log/apache2/error.log```
    - ```/var/log/syslog```
    - ```/var/log/auth.log```
    Commands:
    ```sudo journalctl -xe```

---

## Resolution

1. Restart Apache: ```sudo systemctl restart apache2```
2. Restart MariaDB: ```sudo systemctl restart mariadb```
3. Verify both services are running: ```sudo systemctl status apache2``` ```sudo systemctl status mariadb```
4. Verify network connectivity.
5. Verify available disk space.
6. Verify PHP modules: ```php -m```
7. Verify firewall configuration: ```sudo ufw status```
8. Test the osTicket web portal.
9. Reboot osTicket01 if required: ```sudo reboot```

---

## Validation

- Users can access the osTicket portal.
- Agents can log in.
- New tickets can be created.
- Existing tickets open correctly.
- Email notifications function normally.
- Apache and MariaDB remain online.
- Existing tickets remain accessible.

---

## Escalation Criteria

Escalate if:
- Multiple services fail simultaneously.
- Apache repeatedly crashes.
- Database corruption is suspected.
- Email integration fails.
- Disk space is exhausted.
- Problems persist after service restart.

---

## Key Event IDs/Logs

| Log                          | Description           |
| ---------------------------- | --------------------- |
| `/var/log/apache2/error.log` | Apache errors         |
| `/var/log/syslog`            | System events         |
| `/var/log/auth.log`          | Authentication events |
| `journalctl -u apache2`      | Apache service logs   |
| `journalctl -u mariadb`      | Database service logs |

---

## Common Commands

ping osTicket01

nslookup osTicket01

sudo systemctl status apache2

sudo systemctl restart apache2

sudo systemctl status mariadb

sudo systemctl restart mariadb

sudo ss -tulnp

df -h

php -m

sudo ufw status

journalctl -u apache2

journalctl -u mariadb

---

## Related Documentation

- NWT-RUN-007 DNS Resolution Failure
- NWT-RUN-008 DHCP Lease Failure
- NWT-RUN-009 Printer Offline
- NWT-RUN-011 Wazuh Agent Offline
- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-001 Active Directory Administration SOP

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
