# NWT-SOP-002 Help Desk Operations SOP

| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SOP-002 |
| **Document Type** | Standard Operating Procedure (SOP) |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

This document establishes the standardized framework for the Help Desk Team to receive, track, troubleshoot, and resolve technical incidents and service requests. It applies to all IT support staff and outlines procedures for minimizing system downtime and ensuring optimal end-user satisfaction.  The SOP mandates tracking of key performance indicators, including First Contact Resolution rates, average response times, and customer satisfaction scores to ensure continuous operational improvement.

---

## Scope

  - Tier 1 Support
  - End Users
  - Workstations
  - Active Directory
  - Password Resets
  - Account Unlocks
  - Software Requests
  - Printer Support
  - File Shares
  - Escalations

---

## Supported Systems

  - Windows 11
  - Windows Server 2025
  - Active Directory
  - DNS
  - DHCP
  - File Shares
  - PowerShell
  - osTicket
  - Ubuntu Server (limited)
  - VirtualBox Lab

---

## Help Desk Responsibilities

  - Ticket Creation
  - Ticket Prioritization
  - Password Resets
  - User Creation
  - Unlock Accounts
  - Printer Support
  - Software Installation
  - Basic Network Troubleshooting
  - Escalation

---

## Ticket Categories

| Category | Examples |
|-----------|-----------|
| Account Management | Password Reset, Unlock Account |
| Hardware | Laptop, Desktop, Monitor |
| Software | Installation, Licensing |
| Network | Internet, Wi-Fi, VPN |
| Email | Outlook, Exchange |
| File Services | Shared Folders |
| Printing | Printer Mapping |
| Security | Malware, Suspicious Activity |
| Infrastructure | DNS, DHCP, Server Issues |

---

## Ticket Status

  - New
  - Assigned
  - In Progress
  - Pending User
  - Pending Vendor
  - Resolved
  - Closed
  - Cancelled

---

## Severity Definitions

Critical
- Enterprise outage
- Security incident
- Multiple business services unavailable

High
- Department-wide outage
- Core infrastructure affected

Medium
- Multiple users affected
- Non-critical business impact

Low
- Single user issue
- Minimal operational impact

---

## SLA Definitions

  - Response Time
  - Time before technician responds.
  - Resolution Time
  - Time before issue is resolved.
  - First Contact Resolution
  - Resolved during first interaction.
  - Escalation
  - Transferred to another support tier.

---

## Ticket Priority Matrix

| Priority | Response          | Resolution |
| -------- | ----------------- | ---------- |
| Critical | 15 min            | 4 hr       |
| High     | 30 min            | 8 hr       |
| Medium   | 4 hr              | 2 Days     |
| Low      | Next Business Day | 5 Days     |

---

## Incident Workflow

User Request
↓
Ticket Created
↓
Categorize
↓
Prioritize
↓
Investigate
↓
Resolve
↓
Verify
↓
Document
↓
Close

---

## Password Reset Procedure

1. Verify user identity using approved verification methods.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Reset the password.
5. Enable "User must change password at next logon."
6. Unlock the account if required.
7. Verify successful login with the user.
8. Document the ticket.
9. Close the request.

---

## Unlock Account Procedure

1. Verify user identity using approved verification methods.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Unlock the account.
5. Verify successful login with the user.
6. Document the ticket.
7. Close the request.

---

## User Creation Procedure

1. Verif management authorization or approved request.
2. Open Active Directory Users and Computers.
3. Create the new user account.
4. Assign the user to the correct Organizational Unit (OU).
5. Add required security groups.
6. Configure the initial password.
7. Enable "User must change password at next logon."
8. Verify successful login with the user.
9. Document the Ticket
10. Close the request.

---

## Ticket Documentation Standards

Every ticket shall contain:
  - User Name
  - Department
  - Device Name
  - Asset Tag
  - Date and Time
  - Issue Description
  - Troubleshooting Performed
  - Resolution
  - Technician
  - Follow-up Required

---

## Escalation Matrix

| Issue             | Escalate To    |
| ----------------- | -------------- |
| Password Reset    | Help Desk      |
| User Creation     | Help Desk      |
| Group Membership  | Infrastructure |
| DNS               | Infrastructure |
| DHCP              | Infrastructure |
| Domain Controller | Infrastructure |
| Backup Failure    | Infrastructure |
| Security Incident | CIO            |

---

## Troubleshooting Playbooks

### Cannot Login

Severity: Low
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify username.
2. Verify password.
3. Check account lockout.
4. Verify AD account enabled.
5. Reset password if required.
6. Unlock account.
7. Verify login.
8. Document resolution the ticket.
9. Close the request.

### Account Locked

Severity: Low
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Unlock the account.
5. Verify successful login with the user.
6. Document the ticket.
7. Close the request.

### Password Reset

Severity: Low
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Open Active Directory Users and Computers.
3. Locate the user account.
4. Reset the password.
5. Enable "User must change password at next logon."
6. Unlock the account if required.
7. Verify successful login with the user.
8. Document the ticket.
9. Close the request.

### No Internet Connection

Severity: Low
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify there is no internet connection.
2. Confirm wheter the issues is localized to a single workstation or a wider outage.
3. Ensure the Ethernet cable is connected securely or the Wi-Fi is enabled.
4. Try connecting with another device on the same network.
5. Reboot the workstation.
6. Disconnected the Wi-Fi and then re-connect it.
7. Unplug the modem and router, wait 30 seconds, replug in starting with the modem then router.
8. Open Command Prompt.
9. Run ```cmd ipconfig /release```.
10. run ```cmd ipconfig /renew```.
11. Ping the default gateway.
12. Ping 8.8.8.8.
13. Verify internet access.
14. Document the ticket.
15. Close the request.

### Cannot Access Shared Folder

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify network connectivity.
2. Verify user has autherization for folders.
3. Open Active Directory Users and Computers.
4. Verify user is in the correct OU.
5. Verify group policy is active.
6. Verify user is added to the correct security groups.
7. Re-check acces to shared folder.
8. Verify user can access shared folders.
9. Document the ticket.
10. Close the request.

### Mapped Drive Missing

Severity: Medium
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify mapped drive is not present.
2. Verify network connection.
3. Press Win+R, then type the UNC path directly.
4. Restart workstation.
5. Verify user has access to mapped drive.
6. Document the ticket.
7. Close the request.

### Printer Offline

Severity: Low
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify printer is offline.
2. Turn the printer off and unpluig it for 60 seconds.
3. Ensure all connections are present and secure.
4. Check the printer display for errors.
5. Confirm the print and the user's workstatoin are connected to the exact same Wi-Fi network.
6. Print a configuration page from the printer to verify it has an active IP address.
7. Cancel all pending print jobs.
8. Verify user can access printer.
9. Document the ticket.
10. Close the request.

### Slow Computer

Severity: Single user: Low,  Mutliple Users: High
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify if the entire system runs slow or just an application.
2. Restart the workstation.
3. Open Task Manager.
4. Sort by CPU, MEmory and Disk to identify runaway process.
5. Disable unnecessary background application apps launching at boot.
6. Open Disk Cleanup to remove temp files.
7. Identify and remove heavy or malicious browser extenstions.
8. Run scan using organization's approved endpoint protection software.
9. Verify the OS and critical applicaitons are fully updated.
10. Verify user's workstations is running correctly.
11. Document the ticket.
12. Close the request.

### Group Policy Not Applying

Severity: High
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify user identity using approved verification methods.
2. Verify network connectivity.
3. Open Applications and Services Logs -> Microsoft -> Windows -> Group Policy -> Operational.
4. Run ```cmd gpresults /h gpresults.html```.
5. Review Wazuh alerts (if configured).
6. Verify workstation and user's target resides in the Organizational Unit (OU).
7. Verify the target object is not denied read/apply permissions are not disabled or unlinked.
8. Verify successful acces to the user's target.
9. Document the ticket.
10. Close the request.

### DNS Resolution Failure

Severity: High
Estimated Resolution: 15–30 minutes
Escalation: Infrastructure Team
1. Verify basic connectivity.
2. Verify if single device or multiple devices affected.
3. Verify if user can reach some sites but not others.
4. Open PowerShell.
5. Ping 8.8.8.8.
6. Run ```cdm ipconfig /flushdns```.
7. Run ```cmd nslookup example.com``` for local.
8. Run ```cmd nslookup example.com 8.8.8.8``` for public.
9. Run ```cmd ipconfig /all```.
10. Run ```cmd ipconfig /release```.
11. Run ```cmd ipconfig /renew```.
12. Restart network deviecs as well as the workstation.
13. Update drivers.
14. Verify DNS resolution is successful.
15. Document the ticket.
16. Close the request.

---

## Daily Checklist

Morning:
  - Check ticket queue
  - Review alerts
  - Verify backups
  - Review overnight issues

Afternoon:
  - Follow up on open tickets
  - Update documentation
  - Escalate blockers

End of Day:
  - Close completed tickets
  - Update sprint board
  - Verify documentation
  - Future Improvements
  - Microsoft Intune
  - Remote Support
  - Quick Assist
  - Microsoft Entra ID
  - MFA
  - Wazuh Alerts
  - Microsoft Sentinel

---

## Help Desk Performance Metrics

| Metric | Target |
|----------|--------|
| First Contact Resolution | >80% |
| Ticket Closure | >95% |
| SLA Compliance | >95% |
| Customer Satisfaction | >90% |
| Documentation Accuracy | 100% |

---

## Security Incidents

Immediately escalate:

- Malware
- Phishing
- Ransomware
- Privileged Account Compromise
- Data Loss
- Unauthorized Access

Reference:

NWT-STD-008 Security Configuration Standard

NWT-ENT-010 Disaster Recovery Plan

---

## Document Maintenance

This SOP is a living document.

New troubleshooting playbooks, procedures, and support workflows shall be added as new technologies and operational requirements are introduced into the Northwind Technologies environment.

Review Frequency: Quarterly
Document Owner: Information Technology Services (ITS)

---

## Related Documentation

- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-004 Server Inventory
- NWT-ENT-006 Enterprise Naming Standards
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Backup & Recovery Plan
- NWT-ENT-010 Disaster Recovery Plan
- NWT-STD-005 Enterprise Change Management Standard
- NWT-STD-006 Enterprise Backup Standard
- NWT-STD-008 Security Configuration Standard
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


