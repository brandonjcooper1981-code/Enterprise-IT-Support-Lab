# NWT-RUN-007 DNS Resolution Failure

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-007                           |
| Severity             | High                                  |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose
This runbook provides the procedures required to diagnose and resolve Domain Name System (DNS) failures within the Northwind Technologies environment.

---

## Symptoms

- Users cannot log in to the domain.
- Group Policy does not apply.
- Network drives disappear.
- Printers are unavailable.
- Domain join fails.
- Wazuh agents lose connectivity.
- Users receive:
    - "DNS server isn't responding."
    - "The specified domain either does not exist."
    - "Server not found."
    - "An Active Directory Domain Controller could not be contacted."

---

## Systems Affected

- DC01
- DNS Server
- Active Directory
- DHCP Server
- CLIENT01
- Windows 11 workstations
- WAZUH01
- osTicket01
- northwind.local

---

## Common DNS Records

| Record | Purpose                     |
| ------ | --------------------------- |
| A      | Host name resolution        |
| PTR    | Reverse lookup              |
| CNAME  | Alias                       |
| MX     | Mail routing                |
| SRV    | Domain controller discovery |

---

## Investigation

1. Verify user identity.
2. Verify workstation network connectivity.
3. Review IP configuration: ```ipconfig /all```
4. Verify DNS server assignment.
5. Verify DHCP settings: ``` Get-DhcpServer40ptionValve```
6. Test domain connectivity: ```ping DC01```
7. Test DNS resolution: ```nslookup northwind.local```
8. Verify DNS records: ```nslookup DC01```
9. Flush the local DNS cache: ```ipconfig /flushdns```
10. Verify secure channel: ```nltest /sc_verify:northwind.local```
11. Review Event Viewer logs:
        Applications and Services Logs
            └── Microsoft
                └── Windows
                    └── DNS Client Events

---

## Resolution

1. Verify the workstation uses DC01 as its preferred DNS server.
    - Notes:
      - Domain clients must use the internal DNS server.
      - Public DNS servers (8.8.8.8, 1.1.1.1) should not be configured directly on domain-joined systems.
2. Renew the IP address: ```ipconfig /release``` ```ipconfig /renew```
3. Flush and re-register DNS: ```ipconfig /flushdns``` ```ipconfig /registerdns```
4. Force Group Policy refresh: ```gpupdate /force```
5. Restart the DNS Client service if necessary.
6. Verify DNS zones on DC01.
7. Confirm SRV records exist: ```nslookup``` ```set type=SRV``` ```_ldap._tcp.dc._msdcs.northwind.local```
8. Reboot the workstation if required.

---

## Validation

- Domain names resolve correctly.
- User can authenticate.
- Group Policy applies successfully.
- Network drives reconnect.
- Shared folders are accessible.
- Domain controllers can be discovered.
- Waxuh agents reconnect.

---

## Escalation Criteria

Escalate if:
- Multiple systems are affected.
- DNS service is offline.
- SRV records are missing.
- Active Directory replication fails.
- DHCP distributes incoorect DNS settings.
- Problems persist after cache refresh.

---

## Key Event IDs

| Event ID | Description                     |
| -------- | ------------------------------- |
| 1014     | DNS name resolution failure     |
| 4013     | DNS service startup delay       |
| 4015     | Critical DNS error              |
| 5501     | DNS zone transfer failure       |
| 1058     | Group Policy processing failure |
| 1129     | Domain controller unavailable   |

---

## Common Commands

ipconfig /all

ipconfig /flushdns

ipconfig /registerdns

ipconfig /release

ipconfig /renew

nslookup northwind.local

nslookup DC01

ping DC01

nltest /sc_verify:northwind.local

Get-DnsClientServerAddress

Resolve-DnsName northwind.local

Get-Service DNS

Test-NetConnection DC01 -Port 53

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-003 DNS Administration SOP
- NWT-SOP-004 DHCP Administration SOP
- NWT-RUN-003 Domain Join Failure
- NWT-RUN-004 Network Drive Missing
- NWT-RUN-005 Group Policy Failure
- NWT-RUN-006 Shared Drive Access Failure

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
