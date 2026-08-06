# DHCP Commands

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Administrative Command Reference |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides a centralized reference for administering, validating, and troubleshooting Microsoft DHCP services within the Northwind Technologies Active Directory environment.
The commands support DHCP server administration, scope management, lease management, reservations, DHCP options, client troubleshooting, server validation, auditing, and ongoing enterprise DHCP maintenance.

---

## Environment Note

Note:
The implementation environment uses the lab.local Active Directory domain.
References to northwind.local throughout Northwind Technologies documentation represent the planned enterprise naming standard and future production environment.

---

## Prerequisites

Before using these commands:

- Open PowerShell as Administrator.
- Verify the DHCP Server role is installed.
- Confirm the DHCP Server is authorized in Active Directory.
- Verify network connectivity to DC01.
- Test commands in the lab before production deployment.
- Back up the DHCP database before major changes.

---

## Verify DHCP Server

```powershell
Get-Service DHCPServer
```

Purpose:
Displays the DHCP Server service status.

```powershell
Get-WindowsFeature DHCP
```

Purpose:
Verifies the DHCP Server role is installed.

```powershell
Get-DhcpServerInDC
```

Purpose:
Displays authorized DHCP servers in Active Directory.

---

## DHCP Scope Administration

```powershell
Get-DhcpServerv4Scope
```

Purpose:
Displays all IPv4 scopes.

```powershell
Get-DhcpServerv4ScopeStatistics
```

Purpose:
Displays utilization statistics for all scopes.

```powershell
Get-DhcpServerv4ScopeStatistics -ScopeId 192.168.56.0
```

Purpose:
Displays statistics for a specific scope.

```powershell
Get-DhcpServerv4ExclusionRange
```

Purpose:
Displays excluded IP ranges.

---

## DHCP Lease Administration

```powershell
Get-DhcpServerv4Lease
```

Purpose:
Displays all DHCP leases.

```powershell
Get-DhcpServerv4Lease -ScopeId 192.168.56.0
```

Purpose:
Displays leases for a specific scope.

```powershell
Remove-DhcpServerv4Lease
```

Purpose:
Removes a DHCP lease.

---

## Reservations

```powershell
Get-DhcpServerv4Reservation
```

Purpose:
Displays DHCP reservations.

```powershell
Add-DhcpServerv4Reservation
```

Purpose:
Creates a DHCP reservation.

```powershell
Remove-DhcpServerv4Reservation
```

Purpose:
Deletes a reservation.

---

## DHCP Options

```powershell
Get-DhcpServerv4OptionValue
```

Purpose:
Displays configured DHCP options.

```powershell
Set-DhcpServerv4OptionValue
```

Purpose:
Configures DHCP option values.

---

## Server Administration

```powershell
Restart-Service DHCPServer
```

Purpose:
Restarts the DHCP Server service.

```powershell
Get-DhcpServerDatabase
```

Purpose:
Displays DHCP database iformation.

```powershell
Backup-DhcpServer
```

Purpose:
Creates a backup of the DHCP database.


```powershell
Restore-DhcpServer
```
Purpose:
Restores a DHCP database backup.

---

## Enterprise Administration

```powershell
Get-DhcpServerInDC
```

```powershell
Get-DhcpServerSetting
```

```powershell
Get-DhcpServerBinding
```

```powershell
Get-DhcpServerAuditLog
```

---

## Client Troubleshooting

```powershell
ipconfig /release
```

Purpose:
Releases the current DHCP lease.

```powershell
ipconfig /renew
```

Purpose:
Requests a new DHCP lease.

```powershell
ipconfig /all
```

Purpose:
Displays current TCP/IP configuration.

```powershell
Get-NetIPConfiguration
```

Purpose:
Displays detailed PowerShell network configuration.

```powershell
Test-NetConnection dc01
```

Purpose:
Verifies network connectivity.

---

## Validation

```powershell
Get-DhcpServerv4Statistics
```

Purpose:
Displays DHCP server statistics.

```powershell
Get-DhcpServerAuditLog
```

Purpose:
Displays DHCP audit log configuration.

```powershell
Get-DhcpServerv4ScopeStatistics
```

```powershell
Get-DhcpServerv4Binding
```

Purpose:
Displays network apdapters bound to the DHCP service.

---

## Event Logs

```powershell
Get-WinEvent `
-LogName "Microsoft-Windows-DHCP Server Events/Operational" `
-MaxEvents 25
```

Purpose:
Displays the 25 most recent DHCP operational events

---

## Export Information

```powershell
Get-DhcpServerv4Lease |
Export-Csv C:\Reports\DHCP-Leases.csv -NoTypeInformation
```

```powershell
Get-DhcpServerv4Reservation |
Export-Csv C:\Reports\DHCP-Reservations.csv -NoTypeInformation
```

```powershell
Get-DhcpServerv4Scope |
Export-Csv C:\Reports\DHCP-Scopes.csv -NoTypeInformation
```

```powershell
Get-DhcpServerv4Statistics |
Export-Csv C:\Reports\DHCP-Statistics.csv -NoTypeInformation
```

---

## Troubleshooting Reference

| Issue | Recommended Command |
|--------|---------------------|
| Scope missing | `Get-DhcpServerv4Scope` |
| No lease issued | `Get-DhcpServerv4Lease` |
| Reservation missing | `Get-DhcpServerv4Reservation` |
| Wrong DHCP options | `Get-DhcpServerv4OptionValue` |
| Service stopped | `Get-Service DHCPServer` |
| Restart DHCP | `Restart-Service DHCPServer` |
| Client won't obtain IP | `ipconfig /renew` |
| Verify authorization | `Get-DhcpServerInDC` |
| Scope utilization high | `Get-DhcpServerv4ScopeStatistics` |

---

## Best Practices

- Authorize DHCP servers in Active Directory.
- Use exclusions for infrastructure devices.
- Create reservations for servers, printers, and network appliances.
- Configure DNS (Option 006) and Default Gateway (Option 003).
- Keep lease durations appropriate for the environment.
- Back up the DHCP database regularly.
- Monitor scope utilization to prevent address exhaustion.
- Document reservations and exclusions.
- Validate DHCP changes before deployment.
- Use PowerShell for repeatable administrative tasks.
- Regularly review scope utilization to avoid address exhaustion.

---

## Related Documentation

- PowerShell-Commands.md
- AD-Commands.md
- DNS-Commands.md
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
