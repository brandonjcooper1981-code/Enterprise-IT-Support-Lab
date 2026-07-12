# NWT-RUN-008 DHCP Lease Failure

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-008                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve Dynamic Host Configuration Protocol (DHCP) lease failures within the Northwind Technologies environment.

---

## Symptoms

- Workstations receive an APIPA address (169.254.x.x).
- Users cannot access network resources.
- Internet connectivity fails.
- Domain login fails.
- Group Policy does not apply.
- Network drives disappear.
- Printers become unavailable.
- Users receive:
    - "Limited connectivity."
    - "No Internet access."
    - "Unable to contact domain controller."
    - "Network path not found."

---

## Systems Affected

- DC01
- DHCP Server
- DNS Server
- Active Directory
- CLIENT01
- Windows 11 workstations
- WAZUH01
- osTicket01
- northwind.local

---

## DHCP Components

| Component       | Purpose                         |
| --------------- | ------------------------------- |
| Scope           | IP address pool                 |
| Lease           | Temporary IP assignment         |
| Reservation     | Static assignment               |
| Exclusion Range | Prevent allocation              |
| Options         | DNS, gateway, domain            |
| DHCP Service    | Lease management                |
| Scope Options   | DNS, gateway,domain suffix      |
| Faiover         | Redundancy between DHCP servers |

---

## Investigation

1. Verify user identity.
2. Verify workstation network connectivity.
3. Review IP configuration: ```ipconfig /all```
4. Check for an APIPA address (169.254.x.x).
5. Verify the DHCP server is reachable: ```ping DC01```
6. Verify DHCP lease information: ```ipconfig /all```
7. Review current lease: ```Get-NetIPConfiguration```
8. Verify DHCP service status on DC01: ```Get-Service DHCPServer```
9. Verify DHCP scope availability: ```Get-DhcpServerv4Scope``` ```Get-DhcpServerv4Lease```
10. Review Event Viewer:
        Applications and Services Logs
            └── Microsoft
                └── Windows
                    └── DHCP-Client

---

## Resolution

1. Renew the DHCP lease: ```ipconfig /release``` ```ipconfig /renew```
2. Restart the network adapter if neccessary.
3. Verify DHCP scope has available addresses.
4. Verify DHCP options: ```Get-DhcpServerv4OptionValue```
5. Verify the correct DNS server is distributed.
6. Verify the default gateway is configured.
7. Restart the DHCP Server service if necessary: ```Restart-Service DHCPServer```
8. Force Group Policy refresh: ```gpudate /force```
9. Reboot the workstation if required.

---

## Validation

- Workstation receives a valid IP address.
- DNS server information is correct.
- Default gateway is configured.
- User can authenticate to the domain.
- Network drives reconnect.
- Group Policy applies successfully.
- Internet access is restored.
- Workstation recieves an IP from teh correct subnet.
- Lease expiration time is present.
- User can browse internal resources.

---

## Escalation Criteria

Escalate if:
- Multiple systems are affected.
- DHCP scope is exhausted.
- DHCP service is offline.
- Reservations are misconfigured.
- Incorrect DHCP options are distributed.
- Problems persist after lease renewal.

---

## Key Event IDs

| Event ID | Description                     |
| -------- | ------------------------------- |
| 1001     | DHCP lease obtained             |
| 1002     | DHCP lease renewed              |
| 1003     | DHCP lease released             |
| 1007     | DHCP lease failure              |
| 1058     | Group Policy processing failure |
| 1129     | Domain controller unavailable   |

---

## Common Commands

ipconfig /all

ipconfig /release

ipconfig /renew

Get-NetIPConfiguration

Get-Service DHCPServer

Restart-Service DHCPServer

Get-DhcpServerv4Scope

Get-DhcpServerv4Lease

Get-DhcpServerv4OptionValue

ping DC01

nslookup northwind.local

gpupdate /force

---

## Related Documentation

- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-004 DHCP Administration SOP
- NWT-SOP-001 Active Directory Administration SOP
- NWT-RUN-003 Domain Join Failure
- NWT-RUN-005 Group Policy Failure
- NWT-RUN-007 DNS Resolution Failure

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
