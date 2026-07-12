# NWT-RUN-009 Printer Offline

| Property             | Value                                 |
| -------------------- | ------------------------------------- |
| Company              | Northwind Technologies                |
| Department           | Information Technology Services (ITS) |
| Runbook ID           | NWT-RUN-009                           |
| Severity             | Medium                                |
| Estimated Resolution | 15–30 minutes                         |
| Escalation Team      | Infrastructure                        |

---

## Purpose

This runbook provides the procedures required to diagnose and resolve printer connectivity failures within the Northwind Technologies environment.

This runbook applies to both currently deployed printers and future print infrastructure planned within the Northwind Technologies environment.

---

## Symptoms

- Printer shows Offline.
- User cannot print documents.
- Print jobs remain queued.
- User receives:
    - "Printer is offline."
    - "Unable to connect to printer."
    - "Access denied."
    - "Printer not responding."
    - "Windows cannot connect to the printer."
- Department printer disappears from Devices and Printers.
- Multiple users report printing issues.

---

## Systems Affected

- DC01
- Print Server (Planned)
- Windows 11 workstations
- Active Directory
- Group Policy
- DNS Server
- DHCP Server
- northwind.local

---

## Standard Printers (Planned)

| Printer        | Department             | Purpose                  |
| -------------- | ---------------------- | ------------------------ |
| HR-Printer     | Human Resources        | HR document printing     |
| FIN-Printer    | Finance                | Financial documents      |
| IT-Printer     | Information Technology | Administrative printing  |
| Public-Printer | Shared printing        | General office printing |

> Note:
>
> The Northwind Technologies print infrastructure is planned for a future deployment phase. Printer names and mappings are subject to change as enterprise services expand.
>
---

## Investigation

1. Verify user identity.
2. Confirm workstation network connectivity.
3. Verify the printer appears in: Settings -> Bluetooth & devices -> Printers & scanners.
4. Test connectivity to the print server: ```ping DC01```
5. Review installed printers: ```Get-Printer```
6. Verify the printer queue: ``` Get-PrinterJob```
7. Verify printer port configuration: ``` Get-PrinterPort```
8. Restart the Print Spooler servicce if necessary: ```Get-Service Spooler```
9. Review Event Viewer:
    Applications and Services Logs
        └── Microsoft
            └── Windows
                └── PrintService
                    └── Operational
10. Verify Group Policy printer deployment settings.

---

## Reolution

1. Confirm the printer is powered on.
2. Verify network connectivity.
3. Clear stuck print jobs: ```Get-PrintJob```
4. Restart the Print Spooler: ```Restart-Service Spooler```
5. Remove and re-add the printer: ```Remove-Printer -Name "IT-Printer"``` ```Add-Printer -ConnectionName "\\DC01\IT-Printer"```
6. Force Group Policy refresh: ```gpupdate /force```
7. Restart the workstation if required.
8. Print a test page.

---

## Validation

- Printer displays Online.
- Test page prints successfully.
- Print queue clears.
- User can print documents.
- Group Policy reapplies successfully.
- Other users can access the printer.

---

## Escalation Criteria

Escalate if:
- Multiple printers are offline.
- Print Spooler repeatedly crashes.
- Print server is unavailable.
- Printer drivers fail to install.
- Group Policy printer deployment fails.
- Hardware failure is suspected.

---

## Key Event IDs

| Event ID | Description                     |
| -------- | ------------------------------- |
| 307      | Document printed successfully   |
| 808      | Printer installation failed     |
| 372      | Print job failed                |
| 808      | Driver installation issue       |
| 1000     | Print Spooler crash             |
| 1058     | Group Policy processing failure |

---

## Common Commands

Get-Printer

Get-PrintJob

Get-PrinterPort

Get-Service Spooler

Restart-Service Spooler

Remove-Printer -Name "IT-Printer"

Add-Printer -ConnectionName "\\DC01\IT-Printer"

gpupdate /force

ping DC01

---

## Related Documentation

- NWT-SOP-001 Active Directory Administration SOP
- NWT-SOP-005 Group Policy Administration SOP
- NWT-RUN-005 Group Policy Failure
- NWT-RUN-006 Shared Drive Access Failure
- NWT-RUN-007 DNS Resolution Failure
- NWT-RUN-008 DHCP Lease Failure

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
