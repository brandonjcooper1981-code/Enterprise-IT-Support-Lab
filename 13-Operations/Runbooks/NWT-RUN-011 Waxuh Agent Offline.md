# NWT-RUN-011 Wazuh Agent Offline

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-011                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Security Operations                   |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve Wazuh agent connectivity failures within the Northwind Technologies environment.

This runbook applies to both current endpoint monitoring systems and future security infrastructure planned within Northwind Technologies.

---

## Symptoms

- Wazuh dashboard shows the agent as Disconnected.
- Security events stop appearing.
- Endpoint logs are missing.
- The agent status changes to Never connected or Pending.
- Users receive:
    - "Agent disconnected."
    - "Agent not reporting."
    - "No recent events found."
    - "Unable to connect to manager."
- Alerts stop generating.
- Endpoint monitoring fails.

---

## Systems Affected

- WAZUH01
- CLIENT01
- DC01
- Windows 11 workstations
- Active Directory
- DNS Server
- DHCP Server
- northwind.local

---

## Core Components

| Component                  | Purpose                     |
| -------------------------- | --------------------------- |
| Wazuh Manager              | Receives agent events       |
| Wazuh Agent                | Collects endpoint telemetry |
| Filebeat                   | Forwards logs               |
| Elasticsearch / OpenSearch | Stores events               |
| Wazuh Dashboard            | Security monitoring         |
| Sysmon                     | Endpoint logging            |

---

## Investigation

1. Verify user identity.
2. Confirm workstation network connectivity.
3. Verify WAZUH01 is reachable: ```ping WAZUH01```
4. Verify DNS resolution: ```nslookup WAZUH01```
5. Verify Wazuh Agent service status on CLIENT01: ```Get-Service WazuhSvc | Select-Object Name, Status, StartType```
6. Verify the Wazuh Manager service on WAZUH01: ```sudo systemctl status wazuh-manager```
7. Verify Filebeat status: ```sudo systemctl status filebeat```
8. Verify agent connectivity: ```sudo /var/ossec/bin/agent_control -l```
9. Review Wazuh logs: ```/var/ossec/logs/ossec.log``` ```C:\Program Files (x86)\ossec-agent\ossec.log```
10. Review dashboard agent status.

---

## Resolution

1. Restart the Wazuh Agent on CLIENT01: ```Restart-Service WazuhSvc```
2. Verify the service starts: ```Get-Service WazuhSvc```
3. Restart the Wazuh Manager: ```sudo systemctl restart wazuh-manager```
4. Restart Filebeat: ```sudo systemctl restart filebeat```
5. Verify firewall connectivity.
6. Confirm the agent key is valid.
   - Note:
        -If the agent key is invalid or missing, remove and re-register the endpoint using manage_agents.
7. Re-register the agent if necessary: ```sudo /var/ossec/bin/manage_agents```
8. Force policy refresh: ```gpupdate /force```
9.  Reboot the endpoint if required.

---

## Validation

- Agent status changes to Active.
- Security events appear in the dashboard.
- Sysmon logs are received.
- Alerts generate successfully.
- Wazuh Manager remains online.
- Filebeat remains operational.

---

## Escalation Criteria

Escalate if:
- Multiple agents are offline.
- Wazuh Manager is unavailable.
- Filebeat repeatedly crashes.
- Agent registration fails.
- Security alerts stop globally.
- Problems persist after agent re-registration.

---

## Key Logs/Event IDs

| Log / Event                        | Description               |
| ---------------------------------- | ------------------------- |
| `/var/ossec/logs/ossec.log`        | Wazuh Manager logs        |
| `ossec.log`                        | Wazuh Agent logs          |
| Sysmon Event ID 1                  | Process creation          |
| Sysmon Event ID 3                  | Network connection        |
| Sysmon Event ID 11                 | File creation             |
| Sysmon Event ID 22                 | DNS query                 |
| /var/ossec/logs/alerts/alerts.json | Generated security alerts |

---

## Common Commands

Get-Service WazuhSvc

Restart-Service WazuhSvc

gpupdate /force

ping WAZUH01

nslookup WAZUH01

sudo systemctl status wazuh-manager

sudo systemctl restart wazuh-manager

sudo systemctl status filebeat

sudo systemctl restart filebeat

sudo /var/ossec/bin/agent_control -l

sudo /var/ossec/bin/manage_agents

tail -f /var/ossec/logs/ossec.log

---

## Related Documentation

- NWT-RUN-007 DNS Resolution Failure
- NWT-RUN-008 DHCP Lease Failure
- NWT-RUN-010 osTicket Service Outage
- NWT-RUN-012 Ubuntu Service Failure
- NWT-RUN-013 Security Alert Investigation
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
