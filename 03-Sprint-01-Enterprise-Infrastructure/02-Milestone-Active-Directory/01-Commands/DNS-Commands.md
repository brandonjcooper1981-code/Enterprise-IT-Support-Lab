# DNS Commands

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Administrative Command Reference |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides a centralized reference for administering, validating, and troubleshooting Microsoft DNS services within the Northwind Technologies Active Directory environment.
The commands support DNS server administration, forward and reverse lookup zones, resource record management, client troubleshooting, name resolution validation, and Active Directory-integrated DNS maintenance.

---

## Environment Note

Note:
The implementation environment uses the lab.local Active Directory domain.
References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Table of Contents

- Verify DNS Server
- DNS Records
- DNS Server Administration
- Client Troubleshooting
- DNS Server Cache
- Active Directory DNS Validation
- DNS Event Logs
- Export DNS Information
- Troubleshooting Reference
- Best Practices

---

## Prerequisites

Before using these commands:
- Open PowerShell as Administrator.
- Verify DNS Server tools are installed.
- Confirm the DNS Server role is operational.
- Verify network connectivity to DC01.
- Test commands in the lab before production.
- Backup DNS zones before major changes.

---

## Verify DNS Server

### Verify DNS Service

```powershell
Get-Service DNS
```

Purpose:
Displays the DNS Server service status.

### Display DNS Server Information

```powershell
Get-DnsServer
```

Pupose:
Display information about the local DNS server.

### Display DNS Zones

```powershell
Get-DnsServerZone
```

Purpose:
Lists all configured DNS zones.

### Display Forward Lookup Zone

```powershell
Get-DnsServerZone -Name "lab.local"
```

Purpose:
Displays the Active Directory forward lookup zone.

### Display Reverse Lookup Zones

```powershell
Get-DnsServerZone |
Where-Object ZoneName -like "*.in-addr.arpa"
```

Purpose:
Displays configured reverse lookup zones.

---

## DNS Records

### Display All A Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-RRType "A"
```

Purpose:
Lists all host (A) records.

### Display CNAME Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-RRType "CNAME"
```

### Display MX Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-RRType "MX"
```

### Display SRV Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-RRType "SRV"
```

Purpose:
Displays Active Directory service records.

### Lookup Specific Record

```powershell
Resolve-DnsName dc01.lab.local
```

Purpose:
Resolves a specfic DNS record.

---

## DNS Server Administration

### Restart DNS Service

```powershell
Restart-Service DNS
```

Purpose:
Restarts the DNS Server service.

### View DNS Forwarders

```powershell
Get-DnsServerForwarder
```

Purpose:
Displays configured DNS forwarders.

### View Conditional Forwarders

```powershell
Get-DnsServerConditionalForwarderZone
```

### View Root Hints

```powershell
Get-DnsServerRootHint
```

### Test a DNS Server

```powershell
Resolve-DnsName microsoft.com -Server DC01
```

### Clear Client Cache

```powershell
Clear-DnsClientCache
```

Newer:

```powershell
ipconfig /flushdns
```

### View Scavenging Settings

```powershell
Get-DnsServerScavenging
```

### View Zone Aging

```powershell
Get-DnsServerZoneAging lab.local
```

---

## Client Troubleshooting

### Resolve a Hostname

```powershell
Resolve-DnsName dc01
```

### Nslookup

```powershell
nslookup dc01
```

Purpose:
Performs a DNS lookup using the legacy name resolution tool.

### Reverse Lookup

```powershell
nslookup 192.168.56.10
```

### Ping by Name

```powershell
ping dc01
```

### Flush DNS Cache

```powershell
ipconfig /flushdns
```

### Register DNS

```powershell
ipconfig /registerdns
```

### Display DNS Cache

```powershell
ipconfig /displaydns
```

### Display IP Configuration

```powershell
ipconfig /all
```

---

## DNS Server Cache

### View Server Cache

```powershell
Get-DnsServerCache
```

Purpose:
Displays the contents of the DNS server cache.

### Clear DNS Server Cache

```powershell
Clear-DnsServerCache -Force
```

Purpose:
Clears cached DNS entries on the DNS server.

---

## Active Directory DNS Validation

### Verify Domain Controller Discovery

```powershell
nltest /dsgetdc:lab.local
```

### Verify Secure Channel

```powershell
Test-ComputerSecureChannel
```

### Domain Diagnostics

```powershell
dcdiag /test:dns
```

Purpose:
Run DNS-specific domain controller diagnostics.

### Full Domain Diagnostics

```powershell
dcdiag /v
```

---

## DNS Event Logs

### View DNS Events

```powershell
Get-WinEvent `
-LogName "DNS Server"
```

### Recent DNS Errors

```powershell
Get-WinEvent `
-LogName "DNS Server" `
-MaxEvents 20
```

---

## Export DNS Information

### Export DNS Zones

```powershell
Get-DnsServerZone |
Export-Csv C:\Reports\DNS-Zones.csv -NoTypeInformation
```

### Export DNS Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" |
Export-Csv C:\Reports\DNS-Records.csv -NoTypeInformation
```

---

## Troubleshooting Reference

| Issue | Recommended Command |
|---------|--------------------|
| DNS won't resolve | Resolve-DnsName |
| Verify DNS Server | Get-Service DNS |
| Display Zones | Get-DnsServerZone |
| Lookup Record | Resolve-DnsName |
| Flush Cache | ipconfig /flushdns |
| Register DNS | ipconfig /registerdns |
| DNS Diagnostics | dcdiag /test:dns |
| Reverse Lookup | nslookup IP |

---

## Best Practices

Northwind Technologies recommends:
- Use Active Directory-integrated DNS.
- Configure both forward and reverse lookup zones.
- Point clients only to internal DNS servers.
- Never configure clients to use public DNS directly.
- Verify SRV records after promoting a domain controller.
- Regularly back up DNS zones.
- Flush DNS cache only during troubleshooting.
- Validate name resolution after infrastructure changes.
- Monitor DNS event logs for replication or registration issues.
- Document all manual DNS changes.

---

## Related Documentation

- PowerShell-Commands.md
- AD-Commands.md
- DHCP-Commands.md
- Implementation-Steps.md
- Validation-Checklist.md
- Troubleshooting.md
- Active-Directory-Design.md

---

## Approval

**Approved By**

Michael Wilson

Chief Information Officer (CIO)

**Prepared By**

Brandon J. Cooper

**Department**

Information Technology Services (ITS)

---

## Revision History

| Version | Date | Author | Description |
|----------|----------|----------|----------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial release |

---

**Questions or Updates?**

Please submit documentation corrections through the Northwind Technologies Information Technology Services documentation review process.

---

____________________________________

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Innovate • Secure • Support

© 2026 Northwind Technologies

---
