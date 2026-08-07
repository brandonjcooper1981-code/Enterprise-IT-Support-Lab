# Northwind Technologies Enterprise Operations Runbook

Northwind Technologies

Enterprise IT Troubleshooting Runbook

Information Technology Services (ITS)

Version 1.0

Prepared By
Brandon J. Cooper

Enterprise IT Modernization Project

---

| Property | Value |
|----------|-------|
| Company | Northwind Technologies |
| Department | Information Technology Services (ITS) |
| Document Type | Enterprise Troubleshooting Runbook |
| Status | Active |
| Version | 1.0 |

---

## Purpose

This document provides standardized troubleshooting procedures for diagnosing, isolating, resolving, and validating common enterprise IT issues within the Northwind Technologies Active Directory environment.
The procedures are intended to promote a consistent troubleshooting methodology across the Information Technology Services (ITS) department while minimizing downtime and ensuring repeatable, documented resolutions.
This guide complements the administrative command references by focusing on real-world troubleshooting scenarios rather than individual commands.

---

## Scope

This runbook supports the Northwind Technologies Enterprise IT Support Lab and provides standardized procedures for diagnosing and resolving common incidents affecting Windows Server, Active Directory, DNS, DHCP, Group Policy, SMB file services, and enterprise workstation management.

---

## Environment Note

**Note:**
The current implementation environment uses the **lab.local** Active Directory domain.
References to **northwind.local** throughout Northwind Technologies documentation represent the planned production naming standard and future enterprise environment.

---

## Prerequisites

Before performing troubleshooting procedures:
- Verify you are using an authorized administrative account.
- Confirm PowerShell is running with administrative privileges when required.
- Verify network connectivity to the Domain Controller (DC01).
- Review existing monitoring alerts or ticket information.
- Record the initial symptoms before making configuration changes.
- Whenever possible, validate fixes in the lab environment before implementing them in production.
- Document all changes made during troubleshooting.

---

# Table of Contents

## Front Matter

- [Purpose](#purpose)
- [Environment Note](#environment-note)
- [Prerequisites](#prerequisites)

---

## Enterprise Troubleshooting Framework

- [Enterprise Troubleshooting Methodology](#enterprise-troubleshooting-methodology)
- [Enterprise Troubleshooting Workflow](#enterprise-troubleshooting-workflow)
- [Incident Severity](#incident-severity)
- [Escalation Criteria](#escalation-criteria)
- [Initial Health Checks](#initial-health-checks)

---

## Part I – Authentication & Directory Services

- [Scenario 1 – User Cannot Log In](#scenario-1--user-cannot-log-in)
- [Scenario 2 – Computer Cannot Join the Domain](#scenario-2--computer-cannot-join-the-domain)
- [Scenario 3 – Secure Channel Failure](#scenario-3--secure-channel-failure)
- [Scenario 4 – Group Policy Not Applying](#scenario-4--group-policy-not-applying)

---

## Part II – Network Infrastructure

- [Scenario 5 – DNS Resolution Failure](#scenario-5--dns-resolution-failure)
- [Scenario 6 – DNS Registration Failure](#scenario-6--dns-registration-failure)
- [Scenario 7 – DHCP Lease Failure](#scenario-7--dhcp-lease-failure)
- [Scenario 8 – DHCP Scope Exhaustion](#scenario-8--dhcp-scope-exhaustion-address-pool-full)

---

## Part III – Enterprise Resource Access

- [Scenario 9 – Shared Folder Access Denied](#scenario-9--shared-folder-access-denied-file-services)
- [Scenario 10 – Network Drive Not Mapping](#scenario-10--network-drive-not-mapping)

---

## Part IV – Infrastructure Services

- [Scenario 11 – Domain Controller Unavailable](#scenario-11--domain-controller-unavailable)
- [Scenario 12 – Time Synchronization Failure](#scenario-12--time-synchronization-failure)

---

## Appendices

- [Appendix A – Incident Severity Matrix](#appendix-a--incident-severity-matrix)
- [Appendix B – Estimated Resolution Times](#appendix-b--estimated-resolution-times)
- [Appendix C – Escalation Matrix](#appendix-c--escalation-matrix)
- [Appendix D – Common Network Ports](#appendix-d--common-network-ports)
- [Appendix E – Critical Windows Services](#appendix-e--critical-windows-services)
- [Appendix F – Important Event IDs](#appendix-f--important-event-ids)
- [Appendix G – Administrative Command References](#appendix-g--administrative-command-references)
- [Appendix H – Troubleshooting Decision Tree](#appendix-h--troubleshooting-decision-tree)
- [Appendix I – Technician Checklist](#appendix-i--technician-checklist)
- [Appendix J – Acronyms](#appendix-j--acronyms)

---

## Quick Navigation

| Need Help With? | Go To |
|-----------------|--------|
| User Login Problems | Scenario 1 |
| Domain Join Issues | Scenario 2 |
| Secure Channel Errors | Scenario 3 |
| Group Policy Problems | Scenario 4 |
| DNS Issues | Scenarios 5–6 |
| DHCP Issues | Scenarios 7–8 |
| File Share Issues | Scenarios 9–10 |
| Domain Controller Problems | Scenario 11 |
| Time Synchronization | Scenario 12 |

---

## Enterprise Troubleshooting Methodology

Northwind Technologies follows a structured troubleshooting methodology to ensure issues are resolved efficiently, consistently, and with minimal impact to business operations.

Following a standardized process helps reduce unnecessary configuration changes, improves documentation quality, and accelerates future incident resolution.

The troubleshooting lifecycle consists of the following phases:
1. Gather Information
2. Identify Scope
3. Verify Symptoms
4. Collect Evidence
5. Analyze the Evidence
6. Form a Hypothesis
7. Test the Hypothesis
8. Implement the Resolution
9. Validate the Resolution
10. Document the Resolution
11. Close the Incident

The following workflow illustrates how technicians should progress through the troubleshooting lifecycle while avoiding unnecessary configuration changes and ensuring every resolution is properly validated and documented.

---

## Northwind Technologies Enterprise Troubleshooting Workflow

```text
                  INCIDENT REPORTED
                          │
                          ▼
               Gather Information
                          │
                          ▼
                 Identify Scope
                          │
                          ▼
                 Verify Symptoms
                          │
                          ▼
                 Collect Evidence
                          │
                          ▼
                Analyze the Evidence
                          │
                          ▼
                Form a Hypothesis
                          │
                          ▼
                Test the Hypothesis
                          │
                          ▼
             Root Cause Confirmed?
                 │            │
                No            Yes
                 │             │
                 ▼             ▼
         Gather More     Implement Resolution
         Information             │
                                 ▼
                        Validate Resolution
                                 │
                                 ▼
                       Document Resolution
                                 │
                                 ▼
                         Close the Incident
```

---

## Guide Contents

### Methodology
- Troubleshooting Lifecycle
- Incident Severity
- Escalation Criteria

### Common Incident Playbooks
- User Authentication
- Active Directory
- DNS
- DHCP
- Group Policy
- File Services
- Network Connectivity

### Validation
- Initial Health Checks
- Post-Repair Validation
- Documentation Standards

---

### 1. Gather Information

Before making any changes, collect as much information as possible.

Examples include:
- Error messages
- Screenshots
- Ticket description
- User impact
- Time the issue began
- Recent system changes
- Number of affected users
- Affected devices
- Recent software installations

### 2. Identify Scope

Determine the extent of the issue.

Questions to ask:
- Is only one user affected?
- Is an entire department affected?
- Is the issue limited to one workstation?
- Is one server affected?
- Is the entire domain impacted?

#### Incident Severity

| Severity | Description | Example |
|----------|-------------|----------|
| Critical | Business-wide outage | Domain Controller unavailable |
| High | Multiple departments affected | DNS server failure |
| Medium | Single department affected | File share unavailable |
| Low | Single user issue | Password reset |

### 3. Verify Symptoms

Reproduce or confirm the reported issue whenever possible.

Examples:
- Attempt to log in.
- Access the shared folder.
- Resolve the hostname.
- Renew the DHCP lease.
- Launch the affected application.

### 4. Collect Evidence

Collect diagnostic information before making changes.

Common evidence includes:
- Event Logs
- PowerShell output
- Command Prompt output
- Screenshots
- Service status
- Network configuration
- IP addressing
- DNS results
- DHCP leases

### 5. Analyze the Evidence

Review the collected information to identify patterns and possible root causes.

Consider the following:
- Do all affected systems share a common issue?
- Were recent configuration changes made?
- Are Event Logs reporting consistent errors?
- Are multiple services failing together?
- Is the issue isolated to one technology (DNS, DHCP, Active Directory)?
- Can the issue be reproduced consistently?

Avoid making configuration changes until sufficient evidence has been collected.

### 6. Form a Hypothesis

Based on the collected evidence, develop a likely explanation for the issue.

Examples:
- DNS records are missing.
- DHCP scope has exhausted available addresses.
- The workstation has lost its secure channel with the domain.
- Group Policy failed to apply.
- Required services are stopped.

A clear hypothesis reduces unnecessary troubleshooting and minimizes changes to production systems.

### 7. Test the Hypothesis

Perform controlled tests to confirm or reject the hypothesis.

Examples:
- Resolve a hostname.
- Renew a DHCP lease.
- Restart a service.
- Query Active Directory.
- Review Event Viewer.
- Test network connectivity.

If the hypothesis is incorrect, collect additional evidence and repeat the analysis process.

### 8. Implement the Resolution

After confirming the root cause, implement the appropriate corrective action.

Examples include:
- Reset a user password.
- Repair the secure channel.
- Correct DNS records.
- Restart required services.
- Expand a DHCP scope.
- Restore missing permissions.
- Follow the organization's change management procedures when implementing production changes.

Whenever possible, use documented procedures and approved change management practices.

### 9. Validate the Resolution

Confirm that the issue has been resolved and that normal operation has been restored.

Validation should include:
- User confirmation
- Successful authentication
- Network connectivity
- Event Log review
- Service verification
- Application testing

### 10. Document the Resolution

Record the completed work for future reference.

Documentation should include:
- Root cause
- Corrective actions
- Commands executed
- Configuration changes
- Validation results
- Lessons learned

Whenever practical, identify the underlying root cause rather than only resolving the immediate symptoms. Correcting root causes reduces repeat incidents and improves long-term system stability.

Documentation should be:
- Accurate
- Complete
- Repeatable
- Time-stamped
- Written clearly enough that another technician can reproduce the resolution.

### 11. Close the Incident

After successful validation and documentation:
- Update the ticket.
- Notify affected users.
- Close the incident.
- Identify any long-term improvements to prevent recurrence.

---

## Escalation Criteria

Escalate incidents when:
- Business-critical services are unavailable.
- Multiple departments are affected.
- Data integrity may be compromised.
- Security incidents are suspected.
- Administrative permissions are required.
- Troubleshooting exceeds documented procedures.

---

## Initial Health Checks

Before troubleshooting a specific service, perform these initial validation steps to quickly identify widespread infrastructure issues that may affect multiple systems.

Completing these checks can prevent unnecessary troubleshooting and help determine whether the issue is isolated or part of a larger outage.

---

### 1. Verify Netowrk Connectivity

```powershell
Test-NetConnection dc01
```
or
```cmd
ping dc01
```

Verify:
- Domain Controller reachable.
- DNS resolution succeeds.
- Network latency appears normal.

### 2. Verify IP Configuration

```powershell
ipconfig /all
```

Verify:
- Correct IPv4 Address.
- Default Gateway.
- Preferred DNS Server.
- DHCP Enabled (if applicable).

### 3. Verify DNS Resolution

```powershell
Resolve-DnsName dc01.lab.local
```
or
```cmd
nslookup dc01
```

Verify:
- Correct hostname.
- Correct IP address.
- No timeout.

### 4. Verify Domain Authentication

```cmd
whoami
```
or
```powershell
Test-ComputerSecureChannel
```

Verify:
- User authenticated.
- Secure channel healthy.

### 5. Verify Active Directory

```powershell
Get-ADDomainController -Discover
```

Verify:
- Domain reachable.
- DC responding.
- AD module functioning.

### 6. Verify Critical Services

```powershell
Get-Service NTDS,DNS,DHCPServer,Netlogon,KDC
```

Confirm:
- Running.
- Automatic startup.
- No failures.

### 7. Review Event Logs

```powershell
Get-WinEvent -LogName System -MaxEvents 20
```

Review:
- Critical.
- Error.
- Warning.

### 8. Determine Scope

Ask:
- One user?
- One computer?
- Entire Department?
- Entire site?
- Entire domain?

### Health Check Summary

| Check | Status |
|---------|--------|
| Network Connectivity | Pass/Fail |
| IP Configuration | Pass/Fail |
| DNS Resolution | Pass/Fail |
| Domain Authentication | Pass/Fail |
| Active Directory | Pass/Fail |
| Critical Services | Pass/Fail |
| Event Logs | Pass/Fail |
| Scope Identified | Pass/Fail |

---

If the initial health checks identify a widespread infrastructure problem, resolve that issue before proceeding with scenario-specific troubleshooting.

If no infrastructure issues are identified, continue to the appropriate troubleshooting scenario below.

---

# Part I – Authentication & Directory Services

## Overview

Authentication and directory services form the foundation of the Northwind Technologies enterprise environment. These services provide centralized identity management, user authentication, computer management, Group Policy processing, and secure communication between domain-joined systems.

The following incident runbooks address common authentication and Active Directory issues encountered by the Information Technology Services (ITS) department.

---

# Scenario 1 – User Cannot Log In

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain-Joined Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Users may be unable to authenticate to the domain for several reasons, including incorrect passwords, account lockouts, disabled accounts, expired passwords, DNS issues, workstation trust problems, or Active Directory replication failures.

This runbook provides a standardized process for diagnosing and resolving user authentication issues while minimizing unnecessary account changes.

---

## Business Impact

Potential impacts include:
- User unable to perform daily job functions.
- Lost productivity.
- Increased Help Desk workload.
- Delayed business operations.
- Potential security concern if authentication failures are widespread.

---

## Symptoms

The user reports one or more of the following:
- Unable to log into Windows.
- "The username or password is incorrect."
- "The referenced account is currently locked out."
- "The trust relationship between this workstation and the primary domain failed."
- Password accepted yesterday but fails today.
- User can log into one computer but not another.
- Mapped drives unavailable after logon.

---

## Initial Questions

Gather the following information before making changes.
- Username
- Computer name
- Department
- Location
- Exact error message
- When did the issue begin?
- Has the password recently changed?
- Is anyone else experiencing the issue?
- Is VPN required?
- Has the workstation recently been replaced or rebuilt?

---

## Possible Causes

Common causes include:
- Incorrect password
- Account locked
- Disabled account
- Expired password
- Password expired
- Workstation secure channel failure
- DNS resolution failure
- Domain Controller unavailable
- Network connectivity issue
- Group Policy authentication problem
- Active Directory replication delay

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.
>
---

## Diagnostic Workflow

```

            User Cannot Log In
                     │
                     ▼
        Verify Network Connectivity
                     │
                     ▼
            Verify DNS Resolution
                     │
                     ▼
       Verify Active Directory Access
                     │
                     ▼
      Check Account Status in AD
                     │
          ┌──────────┴──────────┐
          ▼                     ▼
     Account OK?             Account Issue
          │                     │
          ▼                     ▼
 Check Workstation        Unlock / Enable /
 Secure Channel           Reset Password
          │                     │
          └──────────┬──────────┘
                     ▼
          Validate Successful Login

```

---

## Diagnostic Commands

### Verify User Account

```powershell
Get-ADUser username -Properties *
```

Purpose:
Display the user's Active Directory account properties.

---

### Check if Account is Locked

```powershell
Search-ADAccount -LockedOut
```

---

### Verify Account is Enabled

```powershell
Get-ADUser username -Properties Enabled
```

---

### Verify Password Expiration

```powershell
Get-ADUser username -Properties PasswordExpired
```

---

### Verify Group Membership

```powershell
Get-ADPrincipalGroupMembership username
```

---

### Verify DNS

```powershell
Resolve-DnsName dc01.lab.local
```

---

### Verify Domain Connectivity

```powershell
Test-ComputerSecureChannel
```

---

### Verify Current User

```cmd
whoami
```

---

### Verify Domain Controller

```powershell
Get-ADDomainController -Discover
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.
>
## Resolution Procedures

Depending on the findings:

### Incorrect Password

- Verify Caps Lock.
- Confirm username.
- Reset password if required.
- Require password change at next logon.

---

### Account Locked

Unlock account.

```powershell
Unlock-ADAccount username
```

Investigate repeated failed login attempts before closing the ticket.

---

### Disabled Account

```powershell
Enable-ADAccount username
```

Confirm authorization before enabling.

---

### Password Reset

```powershell
Set-ADAccountPassword
```

Require password change at next login.

---

### Secure Channel Failure

```powershell
Test-ComputerSecureChannel -Repair
```

---

### DNS Issue

Verify:
- Preferred DNS Server
- DC reachable
- DNS records exist

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Successful logon
- User profile loads
- Group Policy applies
- Network drives reconnect
- Shared folders accessible
- Outlook/Microsoft 365 signs in
- Event Viewer contains no authentication errors

---

## Escalate When

Escalate if:
- Multiple users affected.
- Domain Controller unavailable.
- Replication failures detected.
- Authentication failures continue after password reset.
- Secure Channel cannot be repaired.
- Administrative approval required.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- Group-Policy.md
- PowerShell-Commands.md
- Validation-Checklist.md

Scenario 1 End.

---

# Scenario 2 – Computer Cannot Join the Domain

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain-Joined Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

A workstation may fail to join the Active Directory domain because of DNS misconfiguration, network connectivity problems, insufficient permissions, duplicate computer accounts, time synchronization issues, or Active Directory service failures.

This runbook provides a standardized process for diagnosing and resolving domain join failures.

---

## Business Impact

Potential impacts include:
- User unable to authenticate using domain credentials.
- Group Policy cannot be applied.
- Shared resources become unavailable.
- Centralized management is unavailable.
- Increased Help Desk workload.
- Delayed workstation deployment.

---

## Symptoms

Users or technicians may experience:
- "An Active Directory Domain Controller could not be contacted."
- "The specified domain either does not exist or could not be contacted."
- "Access is denied."
- "The network path was not found."
- "DNS name does not exist."
- Domain join wizard fails.
- Computer remains in a workgroup.
- Group Policy never applies after reboot.

---

## Initial Questions

Before making changes, determine:
- Computer name
- Domain being joined
- Static or DHCP address?
- Has this computer previously joined the domain?
- Was Windows recently reinstalled?
- Has the computer account already been created?
- Can the computer reach the Domain Controller?
- Has anyone else reported the same issue?

---

## Possible Causes

Common causes include:
- Incorrect DNS server
- Network connectivity failure
- Domain Controller unavailable
- Active Directory unavailable
- Duplicate computer account
- Time synchronization issue
- Secure channel problem
- Firewall blocking required ports
- Insufficient permissions
- Computer object exists in the wrong OU

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

          Domain Join Failed
                   │
                   ▼
       Verify Network Connectivity
                   │
                   ▼
          Verify DNS Settings
                   │
                   ▼
      Resolve Domain Controller
                   │
                   ▼
      Verify Active Directory
                   │
                   ▼
       Check Computer Account
                   │
         ┌─────────┴─────────┐
         ▼                   ▼
     Account Exists?      Doesn't Exist
         │                   │
         ▼                   ▼
 Verify Account       Create Computer
 Status               Account
         │                   │
         └─────────┬─────────┘
                   ▼
          Retry Domain Join
                   │
                   ▼
         Validate Successful Join

```

---

## Diagnostic Commands

### Verify IP Configuration

```cmd
ipconfig /all
```

Verify:
- Correct IPv4 address
- Correct subnet
- Correct default gateway
- Preferred DNS server points to DC01

---

### Verify Network Connectivity

```powershell
Test-NetConnection dc01
```

or

```cmd
ping dc01
```

---

### Verify DNS Resolution

```powershell
Resolve-DnsName dc01.lab.local
```

---

### Verify Domain Controller Discovery

```cmd
nltest /dsgetdc:lab.local
```

---

### Verify Active Directory

```powershell
Get-ADDomain
```

---

### Check Computer Account

```powershell
Get-ADComputer CLIENT01
```

---

### Search for Duplicate Computer Accounts

```powershell
Get-ADComputer -Filter "Name -like 'CLIENT01'"
```

---

### Verify Secure Channel

```powershell
Test-ComputerSecureChannel
```

---

### Check Time Synchronization

```cmd
w32tm /query /status
```

---

### Verify Firewall Connectivity

```powershell
Test-NetConnection dc01 -Port 389
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### DNS Incorrect

Update Preferred DNS Server to the Domain Controller.

Flush DNS cache.

```cmd
ipconfig /flushdns
```

Register DNS.

```cmd
ipconfig /registerdns
```

---

### Computer Account Exists

Reset the account.

```powershell
Reset-ADComputer CLIENT01
```

Retry the domain join.

---

### Duplicate Account

Remove or rename the duplicate object after approval.

---

### Active Directory Unavailable

Verify:
- NTDS Service
- DNS Service
- Netlogon
- Replication health

---

### Time Synchronization

Synchronize time.

```cmd
w32tm /resync
```

---

### Firewall

Verify required ports:
- 53
- 88
- 135
- 389
- 445
- 636
- 3268

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Computer successfully joins the domain.
- Restart completes successfully.
- Domain credentials authenticate.
- Group Policy applies.
- Computer appears in Active Directory.
- DNS record is created.
- Event Viewer contains no join errors.

---

## Escalate When

Escalate if:
- Multiple computers cannot join.
- Domain Controller unavailable.
- DNS infrastructure failure.
- Active Directory replication failures.
- Computer account corruption suspected.
- Administrative approval required.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- DHCP-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md

Scenario 2 End

---

# Scenario 3 – Secure Channel Failure

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain-Joined Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

A secure channel failure occurs when the trust relationship between a domain-joined computer and the Active Directory domain is broken. This typically happens when the computer account password stored locally no longer matches the password stored in Active Directory.

This runbook provides a standardized process for diagnosing and repairing workstation trust relationship failures while minimizing downtime.

---

## Business Impact

Potential impacts include:
- Users unable to log in using domain credentials.
- Group Policy fails to apply.
- Shared drives become inaccessible.
- Domain authentication fails.
- Centralized management is unavailable.
- Business operations are interrupted until trust is restored.

---

## Symptoms

Users or technicians may experience:
- "The trust relationship between this workstation and the primary domain failed."
- Domain users cannot log in.
- Local administrator login succeeds.
- Group Policy updates fail.
- Computer authentication errors appear in Event Viewer.
- Network resources are unavailable.

---

## Initial Questions

Before making changes, determine:
- Computer name
- Username affected
- Has the VM been restored from a snapshot?
- Has Windows recently been reinstalled?
- Has the computer account been reset?
- Is the issue affecting multiple computers?
- Can the workstation communicate with the Domain Controller?

---

## Possible Causes

Common causes include:
- Computer account password mismatch
- Virtual machine snapshot rollback
- Active Directory replication delay
- Computer account deleted
- Secure channel corruption
- DNS issues
- Domain Controller unavailable
- Network connectivity failure
- Time synchronization problems

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

        Trust Relationship Failed
                  │
                  ▼
      Verify Network Connectivity
                  │
                  ▼
         Verify DNS Resolution
                  │
                  ▼
      Verify Domain Controller
                  │
                  ▼
      Test Secure Channel
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
   Secure Channel OK?    Broken
        │                   │
        ▼                   ▼
 Investigate Other      Repair Secure
 Authentication Issues  Channel
        │                   │
        └─────────┬─────────┘
                  ▼
          Validate Logon

```

---

## Diagnostic Commands

### Verify Current User

```cmd
whoami
```

---

### Verify Computer Name

```cmd
hostname
```

---

### Verify Network Connectivity

```powershell
Test-NetConnection dc01
```

---

### Verify DNS Resolution

```powershell
Resolve-DnsName dc01.lab.local
```

---

### Test Secure Channel

```powershell
Test-ComputerSecureChannel -Verbose
```

Expected Result:

```text
True
```

If the result is **False**, the trust relationship is broken.

---

### Verify Domain Controller

```cmd
nltest /dsgetdc:lab.local
```

---

### Check Computer Account

```powershell
Get-ADComputer CLIENT01 -Properties Enabled
```

---

### Verify Time Synchronization

```cmd
w32tm /query /status
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Repair Secure Channel

```powershell
Test-ComputerSecureChannel `
    -Repair `
    -Credential (Get-Credential)
```

---

### Reset Computer Machine Password

```powershell
Reset-ComputerMachinePassword -Server DC01
```

---

### Reset Computer Account in Active Directory

```powershell
Reset-ADComputer CLIENT01
```

Retry the secure channel test.

---

### Rejoin the Domain

If repair fails:
1. Remove the computer from the domain.
2. Restart.
3. Join a workgroup.
4. Restart.
5. Rejoin the domain.
6. Restart again.

---

### Verify DNS

Ensure:
- Preferred DNS points to DC01.
- Domain Controller resolves correctly.
- No stale DNS records exist.

---

### Verify Time Synchronization

```cmd
w32tm /resync
```

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Secure channel returns **True**.
- User successfully logs into the domain.
- Group Policy applies successfully.
- Shared folders are accessible.
- Network drives reconnect.
- Event Viewer shows no authentication errors.

---

## Escalate When

Escalate if:
- Multiple computers experience trust failures.
- Domain Controller is unavailable.
- Active Directory replication problems exist.
- Secure channel cannot be repaired.
- Rejoining the domain fails.
- Administrative approval is required.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 1 – User Cannot Log In
- Scenario 2 – Computer Cannot Join the Domain

Scenario 3 End

---

# Scenario 4 – Group Policy Not Applying

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain-Joined Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Group Policy is used to centrally manage user and computer configurations throughout the enterprise. When Group Policy fails to apply, users may experience missing mapped drives, incorrect desktop settings, software deployment failures, login script failures, or missing security policies.

This runbook provides a standardized process for diagnosing and resolving Group Policy processing failures.

---

## Business Impact

Potential impacts include:
- Security policies not enforced.
- Login scripts fail.
- Drive mappings unavailable.
- Desktop configurations inconsistent.
- Software deployments fail.
- Compliance requirements not met.
- Increased Help Desk workload.

---

## Symptoms

Users or technicians may report:
- Desktop settings missing.
- Mapped network drives unavailable.
- Login scripts do not execute.
- Security settings not applied.
- Printer mappings missing.
- Folder Redirection not working.
- Software deployment failed.
- GPUpdate returns errors.
- RSOP shows missing policies.

---

## Initial Questions

Before troubleshooting:
- Is the issue affecting one user or multiple users?
- Is the issue affecting one computer?
- Has the computer recently joined the domain?
- Has the Group Policy recently changed?
- Is the user logging into the correct computer?
- Are other domain services functioning normally?
- Has the workstation recently been restored or rebuilt?

---

## Possible Causes

Common causes include:
- DNS resolution failure
- Domain Controller unavailable
- Secure channel failure
- SYSVOL unavailable
- Network connectivity issues
- Incorrect OU placement
- Security filtering
- WMI filtering
- Replication delay
- Permissions issues
- Corrupted Group Policy cache

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

        Group Policy Failure
                 │
                 ▼
      Verify Network Connectivity
                 │
                 ▼
         Verify DNS Resolution
                 │
                 ▼
      Verify Domain Authentication
                 │
                 ▼
      Force Group Policy Update
                 │
                 ▼
      Review GPResult / RSOP
                 │
         ┌───────┴────────┐
         ▼                ▼
   Policy Found?      Policy Missing
         │                │
         ▼                ▼
 Investigate Client   Verify AD / OU /
 Configuration        SYSVOL / Replication
         │                │
         └───────┬────────┘
                 ▼
          Validate Policy Applied

```

---

## Diagnostic Commands

### Verify Network Connectivity

```powershell
Test-NetConnection dc01
```

---

### Verify DNS

```powershell
Resolve-DnsName dc01.lab.local
```

---

### Verify Secure Channel

```powershell
Test-ComputerSecureChannel
```

---

### Force Group Policy Update

```cmd
gpupdate /force
```

---

### Generate GPResult Report

```cmd
gpresult /h C:\Reports\GPReport.html
```

---

### Display Applied Policies

```cmd
gpresult /r
```

---

### Open Resultant Set of Policy

```cmd
rsop.msc
```

---

### Verify SYSVOL Access

```cmd
dir \\dc01\SYSVOL
```

---

### Verify Domain Controller

```cmd
nltest /dsgetdc:lab.local
```

---

### Verify Replication Health

```cmd
repadmin /replsummary
```

---

### Review Event Logs

```powershell
Get-WinEvent `
-LogName Microsoft-Windows-GroupPolicy/Operational `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### DNS Issues

Verify:
- Preferred DNS server points to DC01.
- Domain Controller resolves correctly.
- Flush DNS cache.

```cmd
ipconfig /flushdns
```

---

### Secure Channel Failure

Repair the secure channel.

```powershell
Test-ComputerSecureChannel -Repair
```

---

### Incorrect OU

Move the computer or user into the correct Organizational Unit.

Verify the correct GPO is linked.

---

### Group Policy Replication

Force replication.

```cmd
repadmin /syncall
```

---

### Group Policy Cache

Delete the local Group Policy cache if corruption is suspected.

```text
C:\Windows\System32\GroupPolicy
```

Restart the workstation.

---

### Force Policy Refresh

```cmd
gpupdate /force
```

Restart if prompted.

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- GPUpdate completes successfully.
- GPResult lists expected policies.
- RSOP reflects correct settings.
- Login scripts execute.
- Network drives map correctly.
- Desktop settings apply.
- Security policies are enforced.
- Event Viewer contains no Group Policy processing errors.

---

## Escalate When

Escalate if:
- Multiple departments are affected.
- SYSVOL is unavailable.
- Active Directory replication is failing.
- Domain Controllers disagree on policy versions.
- GPO corruption is suspected.
- Administrative approval is required.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Active-Directory-Design.md
- Scenario 1 – User Cannot Log In
- Scenario 2 – Computer Cannot Join the Domain
- Scenario 3 – Secure Channel Failure

Scenario 4 End

---

### Next Section

Continue to **Part II – Network Infrastructure** to troubleshoot DNS, DHCP, and enterprise network service issues.

⬆️ **Back to [Table of Contents](#table-of-contents)**

---

# Part II – Network Infrastructure

## Overview

Reliable network infrastructure services are essential to enterprise operations. DNS and DHCP provide the foundation for name resolution, IP address assignment, Active Directory communication, and client connectivity throughout the Northwind Technologies environment.

The following incident runbooks address common DNS and DHCP issues encountered by enterprise administrators and Help Desk technicians.

---

# Scenario 5 – DNS Resolution Failure

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | DNS Server, Domain Controllers, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

The Domain Name System (DNS) is a core service within the Northwind Technologies Active Directory environment. Active Directory relies heavily on DNS for authentication, service location, Group Policy processing, domain controller discovery, and network resource access.

DNS resolution failures can prevent users and computers from authenticating, locating network resources, applying Group Policy, and communicating with domain services.

This runbook provides a standardized process for diagnosing and resolving DNS-related issues.

---

## Business Impact

Potential impacts include:
- Users unable to log into the domain.
- Domain Controllers cannot be located.
- Group Policy processing failures.
- Shared folders unavailable.
- Network drives fail to map.
- Applications unable to resolve server names.
- Increased Help Desk incidents.

---

## Symptoms

Users or technicians may experience:
- "DNS server isn't responding."
- "Server not found."
- "The specified domain either does not exist or could not be contacted."
- Unable to browse network resources.
- Unable to ping hosts by name.
- Ping by IP address succeeds.
- Domain join failures.
- Group Policy errors.

---

## Initial Questions

Before beginning troubleshooting, determine:
- Is the issue affecting one user or multiple users?
- Is only one computer affected?
- Can devices communicate by IP address?
- Does the issue affect internal names, external names, or both?
- Has the DNS server recently been modified?
- Has networking equipment recently changed?
- Is the Domain Controller reachable?

---

## Possible Causes

Common causes include:
- Incorrect Preferred DNS Server
- DNS Server service stopped
- Network connectivity failure
- Incorrect IP configuration
- Missing DNS records
- Corrupted DNS cache
- Active Directory replication delay
- Firewall blocking DNS traffic
- DNS zone corruption
- Dynamic DNS registration failure

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

          DNS Resolution Failure
                    │
                    ▼
      Verify Network Connectivity
                    │
                    ▼
         Verify IP Configuration
                    │
                    ▼
        Verify Preferred DNS Server
                    │
                    ▼
       Resolve Internal Hostname
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
      Resolution OK?      Resolution Failed
          │                   │
          ▼                   ▼
 Investigate Client      Verify DNS Server
 Configuration           and DNS Records
          │                   │
          └─────────┬─────────┘
                    ▼
           Validate Resolution

```

---

# Network Infrastructure

The following troubleshooting scenarios address the core network services that support authentication, name resolution, IP address management, and resource accessibility throughout the Northwind Technologies environment.

## Diagnostic Commands

### Verify IP Configuration

```cmd
ipconfig /all
```

Verify:
- IPv4 Address
- Default Gateway
- Preferred DNS Server
- DHCP Status

---

### Verify Network Connectivity

```powershell
Test-NetConnection dc01
```

or

```cmd
ping dc01
```

---

### Resolve Internal Hostname

```powershell
Resolve-DnsName dc01.lab.local
```

Expected Result:
- Correct IP address returned
- No timeout
- No DNS errors

---

### Legacy Name Resolution

```cmd
nslookup dc01
```

---

### Verify Domain Controller Discovery

```cmd
nltest /dsgetdc:lab.local
```

---

### Display DNS Client Cache

```cmd
ipconfig /displaydns
```

---

### Flush DNS Cache

```cmd
ipconfig /flushdns
```

---

### Register DNS

```cmd
ipconfig /registerdns
```

---

### Verify DNS Service

```powershell
Get-Service DNS
```

---

### Verify DNS Zones

```powershell
Get-DnsServerZone
```

---

### Verify DNS Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-RRType "A"
```

---

### Review DNS Event Logs

```powershell
Get-WinEvent `
-LogName "DNS Server" `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Incorrect Preferred DNS Server

Configure the Preferred DNS Server to point to the Domain Controller.

Verify:
- Correct IP address
- No public DNS servers configured
- DHCP Option 006 configured correctly

---

### Corrupted Client Cache

Clear the DNS cache.

```cmd
ipconfig /flushdns
```

Re-register DNS.

```cmd
ipconfig /registerdns
```

---

### DNS Service Stopped

Verify the DNS service.

```powershell
Get-Service DNS
```

Restart if necessary.

```powershell
Restart-Service DNS
```

---

### Missing DNS Records

Verify:
- A Records
- SRV Records
- PTR Records (if implemented)

Recreate missing records if necessary.

---

### Network Connectivity

Verify:
- Physical connectivity
- Switch ports
- VLAN assignment
- Firewall rules
- Routing

---

### Active Directory Issues

Verify:
- Domain Controller health
- Active Directory replication
- DNS-integrated zones
- Netlogon service

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Internal hostnames resolve correctly.
- External name resolution functions (if applicable).
- Domain Controllers can be located.
- Users authenticate successfully.
- Group Policy applies successfully.
- Shared folders are accessible.
- Network drives reconnect.
- No DNS errors appear in Event Viewer.

---

## Escalate When

Escalate if:
- Multiple users or departments are affected.
- DNS Server service repeatedly fails.
- DNS zone corruption is suspected.
- Active Directory-integrated DNS replication is failing.
- Domain Controllers cannot be located.
- Administrative approval is required.

---

## Related Documentation

- DNS-Commands.md
- AD-Commands.md
- DHCP-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 2 – Computer Cannot Join the Domain
- Scenario 4 – Group Policy Not Applying

Scenario 5 End

---

# Scenario 6 – DNS Registration Failure

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | DNS Server, Domain Controllers, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Dynamic DNS registration allows domain-joined computers to automatically create and update their DNS resource records within Active Directory-integrated DNS zones. When registration fails, clients may not be discoverable on the network, authentication may fail, and services that rely on DNS can become unavailable.

This runbook provides a standardized process for diagnosing and resolving DNS registration failures within the Northwind Technologies environment.

---

## Business Impact

Potential impacts include:
- Workstations unavailable by hostname.
- Domain Controller records missing.
- Authentication failures.
- Group Policy processing failures.
- Shared resources unavailable.
- Duplicate or stale DNS records.
- Increased Help Desk workload.

---

## Symptoms

Users or technicians may experience:
- Computer cannot be reached by hostname.
- Newly joined computer does not appear in DNS.
- Incorrect IP address returned.
- Duplicate DNS records.
- Dynamic updates fail.
- Event Viewer reports DNS registration errors.
- Clients resolve some hosts but not others.

---

## Initial Questions

Before beginning troubleshooting, determine:
- Is the issue affecting one computer or multiple computers?
- Has the computer recently joined the domain?
- Was the IP address recently changed?
- Is the workstation using DHCP or a static IP?
- Has DNS recently been modified?
- Is the DNS Server operational?
- Are dynamic updates enabled on the DNS zone?

---

## Possible Causes

Common causes include:
- Dynamic DNS updates disabled
- Incorrect Preferred DNS Server
- DHCP Option 006 misconfigured
- DNS service unavailable
- Network connectivity issues
- Duplicate host records
- Missing A or PTR records
- Incorrect permissions on the DNS zone
- Netlogon service stopped
- Active Directory replication delay

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text
         DNS Registration Failure
                   │
                   ▼
      Verify Network Connectivity
                   │
                   ▼
         Verify IP Configuration
                   │
                   ▼
     Verify Preferred DNS Server
                   │
                   ▼
     Attempt DNS Registration
                   │
          ┌────────┴─────────┐
          ▼                  ▼
 Registration OK?      Registration Failed
          │                  │
          ▼                  ▼
 Validate Record      Verify DNS Zone,
 Exists               Permissions, Services
          │                  │
          └────────┬─────────┘
                   ▼
          Validate Resolution
```

---

## Diagnostic Commands

### Verify IP Configuration

```cmd
ipconfig /all
```

Verify:
- IPv4 Address
- Preferred DNS Server
- DHCP Enabled
- DNS Suffix

---

### Register DNS

```cmd
ipconfig /registerdns
```

---

### Flush DNS Cache

```cmd
ipconfig /flushdns
```

---

### Verify DNS Registration

```powershell
Resolve-DnsName CLIENT01.lab.local
```

---

### Verify DNS Service

```powershell
Get-Service DNS
```

---

### Verify Netlogon Service

```powershell
Get-Service Netlogon
```

---

### Verify DNS Records

```powershell
Get-DnsServerResourceRecord `
-ZoneName "lab.local" `
-Name "CLIENT01"
```

---

### Verify DNS Zones

```powershell
Get-DnsServerZone
```

---

### Review DNS Event Logs

```powershell
Get-WinEvent `
-LogName "DNS Server" `
-MaxEvents 20
```

---

### Verify Domain Controller

```cmd
nltest /dsgetdc:lab.local
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Register DNS Manually

```cmd
ipconfig /registerdns
```

---

### Restart Netlogon

```powershell
Restart-Service Netlogon
```

The Netlogon service re-registers Domain Controller SRV records and can help resolve missing registrations.

---

### Restart DNS Service

```powershell
Restart-Service DNS
```

---

### Verify Dynamic Updates

Confirm:
- Dynamic updates enabled.
- Zone is Active Directory integrated.
- Secure updates configured.

---

### Remove Duplicate Records

Delete stale or duplicate host records.

Allow the client to register again.

---

### Verify DHCP Configuration

Confirm:
- Option 006 configured correctly.
- DNS suffix assigned.
- Correct Preferred DNS Server.

---

### Verify Permissions

Ensure the computer account has permission to update its DNS record.

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Hostname resolves successfully.
- A record exists.
- PTR record exists (if implemented).
- Domain Controller can locate the workstation.
- Event Viewer contains no registration errors.
- Authentication succeeds.
- Group Policy processes successfully.

---

## Escalate When

Escalate if:
- Multiple systems fail to register.
- DNS zones are corrupted.
- Active Directory replication issues exist.
- DNS Server repeatedly fails.
- Secure Dynamic Updates fail.
- Administrative approval is required.

---

## Related Documentation

- DNS-Commands.md
- DHCP-Commands.md
- AD-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 5 – DNS Resolution Failure

Scenario 6 End

---

# Scenario 7 – DHCP Lease Failure

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | DHCP Server, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Dynamic Host Configuration Protocol (DHCP) automatically assigns IP configuration information to client devices within the Northwind Technologies environment. When DHCP fails to issue or renew a lease, clients may receive an Automatic Private IP Address (APIPA), lose network connectivity, or be unable to access Active Directory resources.

This runbook provides a standardized process for diagnosing and resolving DHCP lease failures.

---

## Business Impact

Potential impacts include:
- Users unable to access network resources.
- Authentication failures.
- Internet connectivity unavailable.
- Shared folders inaccessible.
- Group Policy processing failures.
- Increased Help Desk workload.
- Delayed workstation deployments.

---

## Symptoms

Users or technicians may experience:
- No network connectivity.
- "Limited connectivity."
- APIPA address (169.254.x.x).
- Unable to browse network resources.
- Unable to reach Domain Controllers.
- Internet unavailable.
- DHCP lease renewal fails.
- Network icon indicates no connection.

---

## Initial Questions

Before beginning troubleshooting, determine:
- Is the issue affecting one device or multiple devices?
- Wired or wireless connection?
- Static IP or DHCP?
- Has the computer recently been moved?
- Have network changes recently occurred?
- Is the DHCP Server operational?
- Are other users experiencing the same issue?

---

## Possible Causes

Common causes include:
- DHCP Server unavailable
- Scope exhausted
- DHCP service stopped
- Incorrect VLAN assignment
- Network cable disconnected
- Switch port disabled
- DHCP relay failure
- Firewall blocking DHCP traffic
- Incorrect DHCP scope configuration
- Client network adapter issue

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

           DHCP Lease Failure
                    │
                    ▼
       Verify Physical Connection
                    │
                    ▼
        Verify Network Adapter
                    │
                    ▼
         Check IP Configuration
                    │
                    ▼
        Attempt DHCP Renewal
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
     Lease Acquired?      Lease Failed
          │                   │
          ▼                   ▼
   Validate Network     Verify DHCP Server
   Connectivity         Scope / Services
          │                   │
          └─────────┬─────────┘
                    ▼
          Validate Resolution

```

---

## Diagnostic Commands

### Display IP Configuration

```cmd
ipconfig /all
```

Verify:
- IPv4 Address
- Default Gateway
- Preferred DNS Server
- DHCP Enabled

---

### Release Current Lease

```cmd
ipconfig /release
```

---

### Request New Lease

```cmd
ipconfig /renew
```

---

### Verify Network Configuration

```powershell
Get-NetIPConfiguration
```

---

### Test Network Connectivity

```powershell
Test-NetConnection dc01
```

---

### Verify DHCP Service

```powershell
Get-Service DHCPServer
```

---

### Verify DHCP Scopes

```powershell
Get-DhcpServerv4Scope
```

---

### Verify Scope Statistics

```powershell
Get-DhcpServerv4ScopeStatistics
```

---

### Verify Active Leases

```powershell
Get-DhcpServerv4Lease
```

---

### Review DHCP Event Logs

```powershell
Get-WinEvent `
-LogName "Microsoft-Windows-DHCP Server Events/Operational" `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Client Has APIPA Address

Release the current lease.

```cmd
ipconfig /release
```

Request a new lease.

```cmd
ipconfig /renew
```

---

### DHCP Service Stopped

Verify the service status.

```powershell
Get-Service DHCPServer
```

Restart if necessary.

```powershell
Restart-Service DHCPServer
```

---

### Scope Exhausted

Review scope utilization.

```powershell
Get-DhcpServerv4ScopeStatistics
```

Expand the scope or shorten lease duration if appropriate.

---

### Network Connectivity

Verify:
- Ethernet cable
- Switch port
- VLAN assignment
- Network adapter status

---

### Incorrect DHCP Options

Confirm:
- Option 003 (Default Gateway)
- Option 006 (DNS Server)
- Option 015 (DNS Suffix)

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Valid IPv4 address assigned.
- Default Gateway configured.
- Preferred DNS Server configured.
- Domain Controller reachable.
- Internet connectivity restored.
- Shared folders accessible.
- Group Policy processes successfully.
- No DHCP errors in Event Viewer.

---

## Escalate When

Escalate if:
- Multiple users are affected.
- DHCP Server is unavailable.
- Scope exhaustion cannot be resolved.
- DHCP database corruption is suspected.
- Network infrastructure failure is suspected.
- Administrative approval is required.

---

## Related Documentation

- DHCP-Commands.md
- DNS-Commands.md
- AD-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 5 – DNS Resolution Failure
- Scenario 6 – DNS Registration Failure

Scenario 7 End

---

# Scenario 8 – DHCP Scope Exhaustion (Address Pool Full)

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | DHCP Server, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

A DHCP scope exhaustion occurs when all available IP addresses within a DHCP scope have been leased or reserved, preventing new clients from obtaining an IP address. Existing clients may continue functioning until their lease expires, while new devices or renewing clients may receive an APIPA address or fail to connect to the network.

This runbook provides a standardized process for diagnosing and resolving DHCP scope exhaustion within the Northwind Technologies environment.

---

## Business Impact

Potential impacts include:
- New devices unable to join the network.
- Existing clients unable to renew DHCP leases.
- Users receive APIPA addresses (169.254.x.x).
- Authentication failures.
- Shared resources become unavailable.
- Increased Help Desk workload.
- Business operations delayed.

---

## Symptoms

Users or technicians may experience:
- Computer receives an APIPA address.
- Unable to obtain an IP address.
- "Limited" or "No Internet" connectivity.
- DHCP lease renewal fails.
- Event Viewer reports DHCP allocation failures.
- New workstations cannot join the network.
- Scope utilization reaches 100%.

---

## Initial Questions

Before troubleshooting, determine:
- Is the issue affecting one device or multiple devices?
- Are existing devices still connected?
- Have many new devices recently been added?
- Were lease durations recently modified?
- Are reservations consuming available addresses?
- Has the DHCP scope recently changed?
- Is the DHCP Server operational?

---

## Possible Causes

Common causes include:
- DHCP scope fully utilized
- Lease duration too long
- Excessive DHCP reservations
- Stale DHCP leases
- Rogue DHCP server
- Misconfigured exclusions
- Scope configuration errors
- Multiple devices consuming addresses unexpectedly

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text
         DHCP Scope Exhaustion
                    │
                    ▼
        Verify DHCP Server Status
                    │
                    ▼
        Review Scope Statistics
                    │
                    ▼
      Check Available Addresses
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
     Addresses Available?   Scope Full
          │                   │
          ▼                   ▼
 Investigate Client     Expand Scope /
 Configuration          Reclaim Leases
          │                   │
          └─────────┬─────────┘
                    ▼
           Validate Resolution
```

---

## Diagnostic Commands

### Display DHCP Scopes

```powershell
Get-DhcpServerv4Scope
```

---

### Review Scope Statistics

```powershell
Get-DhcpServerv4ScopeStatistics
```

Verify:
- Addresses In Use
- Addresses Available
- Percentage Utilized

---

### Display Active Leases

```powershell
Get-DhcpServerv4Lease
```

---

### Display Reservations

```powershell
Get-DhcpServerv4Reservation
```

---

### Review Exclusion Ranges

```powershell
Get-DhcpServerv4ExclusionRange
```

---

### Verify DHCP Service

```powershell
Get-Service DHCPServer
```

---

### Review DHCP Event Logs

```powershell
Get-WinEvent `
-LogName "Microsoft-Windows-DHCP Server Events/Operational" `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Reclaim Stale Leases

Identify inactive or obsolete leases.
Remove stale leases when appropriate.

```powershell
Remove-DhcpServerv4Lease
```

---

### Expand the DHCP Scope

Increase the available address range if network design permits.
Document all scope modifications.

---

### Reduce Lease Duration

If appropriate, temporarily reduce lease duration to reclaim addresses more quickly.

---

### Review Reservations

Remove unnecessary DHCP reservations.
Confirm all remaining reservations are still required.

---

### Review Exclusion Ranges

Verify exclusion ranges are correct and not consuming excessive address space.

---

### Check for Rogue DHCP Servers

Confirm only authorized DHCP servers are issuing leases.

```powershell
Get-DhcpServerInDC
```

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Scope utilization has decreased.
- Clients successfully obtain IP addresses.
- No APIPA addresses remain.
- DHCP lease renewals succeed.
- Domain authentication functions normally.
- Shared resources are accessible.
- Event Viewer reports no allocation failures.

---

## Escalate When

Escalate if:
- Multiple scopes are exhausted.
- Scope expansion requires network redesign.
- Rogue DHCP servers are detected.
- DHCP database corruption is suspected.
- Infrastructure changes require change management approval.

---

## Related Documentation

- DHCP-Commands.md
- DNS-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 7 – DHCP Lease Failure

Scenario 8 End

---

### Next Section

Continue to **Part III – Enterprise Resource Access** to troubleshoot shared folders, file services, and mapped network drives.

⬆️ **Back to [Table of Contents](#table-of-contents)**

---

# Part III – Enterprise Resource Access

## Overview

Enterprise file services enable users to securely access departmental resources using centralized file shares, mapped network drives, and Active Directory security groups. Proper permissions, authentication, and Group Policy ensure users have reliable access to the resources required for daily operations.

The following incident runbooks address common file service and resource access issues.

---

# Scenario 9 – Shared Folder Access Denied (File Services)

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | File Server, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Shared folders provide centralized access to departmental files and resources throughout the Northwind Technologies environment. Access is controlled through a combination of Share Permissions, NTFS Permissions, Active Directory security groups, and Group Policy.

When users receive an "Access Denied" message, the issue is typically related to permissions, group membership, network connectivity, authentication, or file server availability.

This runbook provides a standardized process for diagnosing and resolving shared folder access issues.

---

## Business Impact

Potential impacts include:
- Users unable to access departmental documents.
- Interrupted collaboration.
- Reduced productivity.
- Delayed business operations.
- Increased Help Desk workload.
- Potential security concerns if permissions are incorrectly configured.

---

## Symptoms

Users or technicians may experience:
- "Access is Denied."
- "You do not have permission to access this folder."
- Network path unavailable.
- Folder opens but files cannot be modified.
- User can access one department share but not another.
- Shared drive appears empty.
- File Explorer prompts repeatedly for credentials.

---

## Initial Questions

Before beginning troubleshooting, determine:
- Which shared folder is affected?
- Is the issue affecting one user or multiple users?
- Has the user recently changed departments?
- Can the user access other network shares?
- Has permissions recently been modified?
- Is the file server online?
- Is the user connected to the corporate network or VPN?

---

## Possible Causes

Common causes include:
- Incorrect NTFS permissions
- Incorrect Share permissions
- Missing Active Directory group membership
- Incorrect OU assignment
- Group Policy not applied
- Network connectivity issues
- File server unavailable
- DNS resolution failure
- Authentication failure
- Folder inheritance disabled incorrectly

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

          Shared Folder Access Denied
                     │
                     ▼
        Verify Network Connectivity
                     │
                     ▼
        Verify DNS Resolution
                     │
                     ▼
        Verify User Authentication
                     │
                     ▼
      Verify File Server Reachability
                     │
                     ▼
        Verify Group Membership
                     │
                     ▼
        Verify Share Permissions
                     │
                     ▼
        Verify NTFS Permissions
                     │
          ┌──────────┴──────────┐
          ▼                     ▼
     Permissions OK?      Permissions Incorrect
          │                     │
          ▼                     ▼
 Investigate Other        Correct Permissions
 Causes                   or Group Membership
          │                     │
          └──────────┬──────────┘
                     ▼
            Validate Access

```

---

## Diagnostic Commands

### Verify Network Connectivity

```powershell
Test-NetConnection FS01
```

or

```cmd
ping FS01
```

---

### Verify DNS Resolution

```powershell
Resolve-DnsName FS01.lab.local
```

---

### Verify Current User

```cmd
whoami
```

---

### Display Group Membership

```cmd
whoami /groups
```

---

### Verify Active Directory Group Membership

```powershell
Get-ADPrincipalGroupMembership username
```

---

### Verify Network Shares

```cmd
net view \\FS01
```

---

### Display Mapped Drives

```cmd
net use
```

---

### Test Share Access

```cmd
dir \\FS01\HR
```

Replace **HR** with the appropriate department share.

---

### Verify NTFS Permissions

```powershell
Get-Acl "D:\Shares\HR"
```

---

### Review SMB Sessions

```powershell
Get-SmbSession
```

---

### Review SMB Shares

```powershell
Get-SmbShare
```

---

### Review Event Logs

```powershell
Get-WinEvent `
-LogName Security `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Incorrect Group Membership

Verify the user belongs to the appropriate department security group.

Example:
- HR_Users
- Finance_Users
- IT_Users
- Sales_Users
- Marketing_Users
- Operations_Users

Refresh the user's Kerberos ticket or have them sign out and back in after membership changes.

---

### Incorrect NTFS Permissions

Verify:
- Read
- Modify
- Full Control

Ensure permissions follow the principle of least privilege.

---

### Incorrect Share Permissions

Review the share configuration.

Verify:
- Share permissions
- Hidden administrative shares
- Correct share path

---

### Group Policy Not Applied

Force Group Policy refresh.

```cmd
gpupdate /force
```

Restart if prompted.

---

### Authentication Issues

Verify:
- Domain login
- Secure channel
- Time synchronization

---

### File Server Unavailable

Verify:
- Server online
- SMB service running
- Storage available
- Network connectivity

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- User accesses the correct departmental share.
- Required folders and files are visible.
- Read and write permissions function correctly.
- Unauthorized folders remain inaccessible.
- Mapped drives reconnect successfully.
- Event Viewer reports no SMB or authentication errors.

---

## Escalate When

Escalate if:
- Multiple departments are affected.
- File server unavailable.
- Storage failure suspected.
- Permission inheritance corruption detected.
- Security breach suspected.
- Administrative approval required.

---

## Related Documentation

- File-Services.md
- Group-Design.md
- Group-Creation-Procedure.md
- Group-Membership-Procedure.md
- GPO-Standards.md
- AD-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 4 – Group Policy Not Applying

---

## Northwind Departmental Shares

The Northwind Technologies environment includes the following departmental shared folders:

| Department | Example Share |
|------------|---------------|
| Human Resources | \\FS01\HR |
| Finance | \\FS01\Finance |
| Information Technology | \\FS01\IT |
| Sales | \\FS01\Sales |
| Marketing | \\FS01\Marketing |
| Operations | \\FS01\Operations |

Each share is secured using department-specific Active Directory security groups and NTFS permissions following the principle of least privilege.

Scenario 9 End

---

# Scenario 10 – Network Drive Not Mapping

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | File Server, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Network drive mappings provide users with consistent access to departmental resources by automatically connecting shared folders during logon. In the Northwind Technologies environment, network drives are deployed through Group Policy Preferences and secured using Active Directory security groups and NTFS permissions.

When a mapped drive fails to appear or disconnects unexpectedly, users may lose access to business-critical resources even though the file server remains operational.

This runbook provides a standardized process for diagnosing and resolving network drive mapping failures.

---

## Business Impact

Potential impacts include:
- Departmental files unavailable.
- Users unable to save documents.
- Login scripts incomplete.
- Reduced productivity.
- Increased Help Desk workload.
- Delayed business operations.

---

## Symptoms

Users or technicians may experience:
- Network drive missing after logon.
- Red X displayed on mapped drive.
- "The network path was not found."
- Drive reconnects intermittently.
- Login completes without mapped drives.
- Drive mappings differ between users.
- Applications cannot locate shared files.

---

## Initial Questions

Before beginning troubleshooting, determine:
- Which mapped drive is affected?
- Is the issue affecting one user or multiple users?
- Is the issue affecting one computer or multiple computers?
- Was the computer recently joined to the domain?
- Has Group Policy recently changed?
- Is the user connected to the corporate network or VPN?
- Are other shared folders accessible?

---

## Possible Causes

Common causes include:
- Group Policy not applied
- Incorrect Group Policy filtering
- DNS resolution failure
- File server unavailable
- Incorrect drive mapping configuration
- Missing security group membership
- Authentication failure
- Network connectivity issues
- Incorrect share permissions
- Offline Files synchronization issues

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text
         Network Drive Missing
                  │
                  ▼
      Verify Network Connectivity
                  │
                  ▼
         Verify DNS Resolution
                  │
                  ▼
     Verify Domain Authentication
                  │
                  ▼
       Verify File Server Access
                  │
                  ▼
        Verify Group Policy
                  │
                  ▼
       Verify Drive Mapping
                  │
         ┌────────┴─────────┐
         ▼                  ▼
   Mapping Exists?     Mapping Missing
         │                  │
         ▼                  ▼
 Investigate User     Verify GPO /
 Configuration        Drive Preferences
         │                  │
         └────────┬─────────┘
                  ▼
          Validate Resolution
```

---

## Diagnostic Commands

### Display Current Drive Mappings

```cmd
net use
```

---

### Verify Network Connectivity

```powershell
Test-NetConnection FS01
```

or

```cmd
ping FS01
```

---

### Verify DNS Resolution

```powershell
Resolve-DnsName FS01.lab.local
```

---

### Force Group Policy Update

```cmd
gpupdate /force
```

---

### Display Applied Group Policies

```cmd
gpresult /r
```

---

### Generate GPResult Report

```cmd
gpresult /h C:\Reports\DriveMapping-GPO.html
```

---

### Verify Share Access

```cmd
dir \\FS01\HR
```

Replace **HR** with the appropriate department share.

---

### Display Current User

```cmd
whoami
```

---

### Display Group Membership

```cmd
whoami /groups
```

---

### Review Event Logs

```powershell
Get-WinEvent `
-LogName Microsoft-Windows-GroupPolicy/Operational `
-MaxEvents 20
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Force Group Policy Refresh

```cmd
gpupdate /force
```

Restart if prompted.

---

### Verify Group Policy Preferences

Confirm:
- Drive mapping configured.
- Correct drive letter assigned.
- Correct UNC path.
- Item-level targeting configured correctly.

---

### Verify Share Path

Example:

```
\\FS01\HR
```

Confirm the path exists and is accessible.

---

### Verify Active Directory Group Membership

Ensure the user belongs to the correct department security group.
Log off and log back on after membership changes.

---

### Verify File Server

Confirm:
- Server online.
- SMB service running.
- Shares published.
- Storage available.

---

### Recreate Mapping Manually

```cmd
net use H: \\FS01\HR
```

If successful, review the Group Policy configuration.

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- Network drive appears after logon.
- Drive reconnects automatically.
- User can browse folders.
- Read and write permissions function correctly.
- Group Policy applies successfully.
- Applications can access required files.

---

## Escalate When

Escalate if:
- Multiple users are affected.
- File server unavailable.
- Group Policy corruption suspected.
- DFS or replication issues are identified (if implemented).
- Infrastructure changes require approval.

---

## Related Documentation

- Drive-Mapping-GPO.md
- GPO-Standards.md
- Group-Design.md
- File-Services.md
- AD-Commands.md
- DNS-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Scenario 4 – Group Policy Not Applying
- Scenario 9 – Shared Folder Access Denied

Scenario 10 End

---

### Next Section

Continue to **Part IV – Infrastructure Services** to troubleshoot critical enterprise services including Domain Controllers and Windows Time synchronization.

⬆️ **Back to [Table of Contents](#table-of-contents)**

---

# Part IV – Infrastructure Services

## Overview

Infrastructure services provide the core operational foundation of the Northwind Technologies enterprise environment. Domain Controllers, Active Directory, Kerberos, DNS, and Windows Time services work together to deliver secure authentication, policy management, and enterprise-wide service availability.

The following incident runbooks address high-impact infrastructure incidents that may affect multiple users, departments, or enterprise services.

---

# Scenario 11 – Domain Controller Unavailable

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain Controller (DC01) |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

The Domain Controller (DC01) is the core infrastructure server within the Northwind Technologies Active Directory environment. It provides authentication, directory services, DNS, Group Policy processing, and centralized identity management.

When the Domain Controller becomes unavailable, users may be unable to authenticate, access shared resources, receive Group Policy updates, or locate network services.

This runbook provides a standardized process for diagnosing and resolving Domain Controller outages while minimizing business disruption.

---

## Business Impact

Potential impacts include:
- Domain authentication unavailable.
- New user logins fail.
- Group Policy processing fails.
- DNS resolution fails.
- DHCP services unavailable (if hosted on DC01).
- Shared folders inaccessible.
- Network drive mappings unavailable.
- Enterprise-wide service disruption.

---

## Symptoms

Users or technicians may experience:
- "The specified domain either does not exist or could not be contacted."
- Users unable to log in.
- DNS lookups fail.
- Group Policy processing errors.
- Network drives unavailable.
- Shared folders inaccessible.
- Domain joins fail.
- Active Directory tools cannot connect.
- Server monitoring reports DC01 offline.

---

## Initial Questions

Before troubleshooting, determine:
- Is DC01 powered on?
- Is the issue affecting all users?
- Can DC01 be reached by IP address?
- Can DC01 be reached by hostname?
- Were recent configuration changes made?
- Has Windows Update recently installed?
- Are virtualization services functioning correctly?
- Are other servers operational?

---

## Possible Causes

Common causes include:
- Server powered off
- Virtual machine unavailable
- DNS failure
- Network outage
- Active Directory service failure
- Hardware failure
- Storage unavailable
- Windows Update failure
- Firewall blocking required services
- Critical Windows service stopped

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

         Domain Controller Offline
                    │
                    ▼
          Verify Server Power State
                    │
                    ▼
       Verify Network Connectivity
                    │
                    ▼
          Verify DNS Resolution
                    │
                    ▼
       Verify Required Services
                    │
                    ▼
         Review Event Logs
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
     Service Failure      Infrastructure
                               Failure
          │                   │
          ▼                   ▼
 Restart Services       Restore VM /
                        Restore Hardware
          │                   │
          └─────────┬─────────┘
                    ▼
          Validate Domain Services

```

---

## Diagnostic Commands

### Verify Network Connectivity

```powershell
Test-NetConnection DC01
```

---

### Verify DNS Resolution

```powershell
Resolve-DnsName dc01.lab.local
```

---

### Verify Domain Controller Discovery

```cmd
nltest /dsgetdc:lab.local
```

---

### Verify Active Directory

```powershell
Get-ADDomainController -Discover
```

---

### Verify Active Directory Services

```powershell
Get-Service NTDS
```

---

### Verify DNS Service

```powershell
Get-Service DNS
```

---

### Verify Netlogon

```powershell
Get-Service Netlogon
```

---

### Verify Kerberos KDC

```powershell
Get-Service KDC
```

---

### Verify DHCP Service (if applicable)

```powershell
Get-Service DHCPServer
```

---

### Review System Event Logs

```powershell
Get-WinEvent `
-LogName System `
-MaxEvents 25
```

---

### Review Directory Service Logs

```powershell
Get-WinEvent `
-LogName "Directory Service" `
-MaxEvents 25
```

---

### Verify Active Directory Replication

```cmd
repadmin /replsummary
```

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Domain Controller Powered Off

Power on DC01.
Verify VirtualBox or hypervisor status.
Allow all services to initialize before testing.

---

### Network Connectivity

Verify:
- Virtual network adapters
- Host-only network
- NAT adapter
- Switch connectivity
- IP configuration

---

### Restart Critical Services

Restart services as appropriate:
- NTDS
- DNS
- Netlogon
- KDC
- DHCP Server (if installed)

---

### Active Directory Failure

Verify:
- NTDS database
- SYSVOL
- Replication
- Authentication

Restart services if appropriate.

---

### DNS Failure

Verify:
- Forward Lookup Zone
- SRV Records
- Dynamic Updates
- DNS Service

---

### Storage Issues

Verify:
- Disk space
- Virtual disk availability
- Event Viewer disk errors

---

### Virtual Machine Failure

Verify:
- VirtualBox running
- VM not paused
- VM not saved
- Snapshots intact

Restart the virtual machine if appropriate.

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- DC01 responds to ping.
- DNS resolves correctly.
- Users authenticate successfully.
- Group Policy processes successfully.
- Shared folders accessible.
- Network drives reconnect.
- Active Directory Users and Computers opens normally.
- Event Viewer reports no critical errors.

---

## Escalate When

Escalate if:
- Hardware failure suspected.
- Active Directory database corruption suspected.
- SYSVOL corruption identified.
- Multiple infrastructure services unavailable.
- Disaster Recovery procedures required.
- Executive notification required.

---

## Related Documentation

- AD-Commands.md
- DNS-Commands.md
- DHCP-Commands.md
- PowerShell-Commands.md
- Validation-Checklist.md
- Troubleshooting.md
- Scenario 1 – User Cannot Log In
- Scenario 2 – Computer Cannot Join the Domain
- Scenario 3 – Secure Channel Failure
- Scenario 4 – Group Policy Not Applying
- Scenario 5 – DNS Resolution Failure
- Scenario 6 – DNS Registration Failure

Scenario 11 End

---

## Virtualization Verification

When the Domain Controller is hosted as a virtual machine:
- Verify Oracle VirtualBox is running.
- Confirm the DC01 virtual machine is powered on.
- Verify Adapter 1 (NAT) is connected.
- Verify Adapter 2 (Host-Only) is connected.
- Confirm the VM is not paused or in a saved state.
- Review VirtualBox logs for startup errors.

---

# Scenario 12 – Time Synchronization Failure

| Property | Value |
|----------|-------|
| Category | Authentication & Directory Services |
| **Affected Systems** | Domain Controller (DC01), Member Servers, Windows Clients |
| Priority | High |
| Estimated Resolution Time | 15–30 Minutes |
| Escalation Level | Tier 2 |
| Difficulty | Intermediate |

## Overview

Accurate time synchronization is essential for the proper operation of Active Directory, Kerberos authentication, Group Policy processing, DNS registration, and domain communications. All domain-joined systems rely on a consistent time source to establish trust relationships and authenticate securely.

When time synchronization fails, users may experience authentication failures, Group Policy errors, secure channel issues, and domain communication problems.

This runbook provides a standardized process for diagnosing and resolving Windows Time Service (W32Time) synchronization issues within the Northwind Technologies environment.

---

## Business Impact

Potential impacts include:
- Domain authentication failures.
- Kerberos ticket validation failures.
- Group Policy processing failures.
- Secure channel failures.
- Domain joins unsuccessful.
- Event log timestamp inconsistencies.
- Increased Help Desk workload.
- Enterprise-wide authentication issues.

---

## Symptoms

Users or technicians may experience:
- Users unable to log into the domain.
- "The clock on this computer is out of sync."
- Kerberos authentication failures.
- Group Policy processing errors.
- Secure channel failures.
- Domain trust issues.
- Time displayed incorrectly on workstations.
- Event Viewer reports Windows Time Service errors.

---

## Initial Questions

Before troubleshooting, determine:
- Is the issue affecting one computer or multiple systems?
- Is the Domain Controller reporting the correct time?
- Has the CMOS clock recently been modified?
- Has the virtual machine recently resumed from a saved state?
- Has the workstation been disconnected from the network?
- Are all systems using the same time source?
- Is the Windows Time Service running?

---

## Possible Causes

Common causes include:
- Windows Time Service stopped
- Incorrect NTP configuration
- Domain Controller unavailable
- Virtual machine time drift
- Incorrect system time
- Network connectivity failure
- Firewall blocking NTP traffic
- PDC Emulator unavailable
- Manual time configuration
- BIOS or CMOS clock incorrect

> **Tip**
>
> Complete the Initial Health Checks before continuing with scenario-specific troubleshooting.

---

## Diagnostic Workflow

```text

          Time Synchronization Failure
                     │
                     ▼
         Verify Current System Time
                     │
                     ▼
      Verify Windows Time Service
                     │
                     ▼
       Verify Domain Connectivity
                     │
                     ▼
        Verify Time Source (NTP)
                     │
            ┌────────┴────────┐
            ▼                 ▼
      Time Correct?      Time Incorrect
            │                 │
            ▼                 ▼
 Investigate Other      Resynchronize
 Authentication Issues  Windows Time
            │                 │
            └────────┬────────┘
                     ▼
            Validate Synchronization

```

---

## Diagnostic Commands

### Display Current Date and Time

```cmd
date /t
time /t
```

---

### Display Windows Time Configuration

```cmd
w32tm /query /configuration
```

---

### Display Time Source

```cmd
w32tm /query /source
```

---

### Display Time Status

```cmd
w32tm /query /status
```

---

### Verify Windows Time Service

```powershell
Get-Service W32Time
```

---

### Restart Windows Time Service

```powershell
Restart-Service W32Time
```

---

### Force Time Synchronization

```cmd
w32tm /resync
```

---

### Rediscover Domain Time Source

```cmd
w32tm /resync /rediscover
```

---

### Verify Domain Controller

```cmd
nltest /dsgetdc:lab.local
```

---

### Verify Network Connectivity

```powershell
Test-NetConnection DC01
```

---

### Review Windows Time Event Logs

```powershell
Get-WinEvent `
-LogName System `
-MaxEvents 20
```

Review Windows Time Service events and synchronization errors.

---

> **Warning**
>
> Verify the root cause before making configuration changes. Document all changes according to Northwind Technologies change management procedures.

## Resolution Procedures

### Restart Windows Time Service

```powershell
Restart-Service W32Time
```

Confirm the service is configured for Automatic startup.

---

### Force Time Synchronization

```cmd
w32tm /resync
```

If synchronization fails:

```cmd
w32tm /resync /rediscover
```

---

### Verify Domain Time Hierarchy

Confirm:
- Workstations synchronize with the Domain Controller.
- Member servers synchronize with the Domain Controller.
- The Domain Controller synchronizes with the appropriate time source.

---

### Verify Virtual Machine Time

If using Oracle VirtualBox:
- Confirm the VM is not paused.
- Verify VirtualBox Guest Additions are functioning correctly.
- Ensure the guest operating system is synchronized with the domain hierarchy.
- Avoid conflicting host and guest time synchronization settings.

---

### Verify Network Connectivity

Confirm:
- Domain Controller reachable.
- DNS functioning correctly.
- Firewall permits required communication.
- No excessive network latency.

---

> **Best Practice**
>
> Validate the issue from the end user's perspective and confirm that all affected services have been restored.

## Validation

Confirm:
- System time is accurate.
- Windows Time Service is running.
- Time source is correct.
- Domain authentication succeeds.
- Kerberos tickets are issued successfully.
- Group Policy processes normally.
- Secure channel tests pass.
- Event Viewer contains no Windows Time Service errors.

---

## Escalate

Escalate if:
- Multiple systems are out of synchronization.
- The PDC Emulator is unavailable.
- Time hierarchy is incorrectly configured.
- Hardware clock failures are suspected.
- Domain-wide authentication failures continue after synchronization.
- Disaster Recovery procedures are required.

Scenario 12 End.

---

### Next Section

Continue to the **Appendices** for enterprise reference material, troubleshooting matrices, administrative command references, Windows Event IDs, and quick-reference documentation.

⬆️ **Back to [Table of Contents](#table-of-contents)**

---

# Appendices

## Overview

The appendices provide quick-reference information to support enterprise troubleshooting activities. These reference materials include incident severity classifications, escalation guidance, common network ports, Windows services, Event IDs, administrative commands, troubleshooting workflows, and enterprise terminology used throughout this runbook.

These resources are intended to supplement the incident runbooks and provide technicians with rapid access to commonly referenced operational information.

---

## Appendix A – Incident Severity Matrix

| Severity | Description | Response Time | Example |
|----------|-------------|--------------|---------|
| Critical | Business-wide outage | Immediate | Domain Controller offline |
| High | Multiple users affected | < 30 minutes | DNS Server failure |
| Medium | Single department affected | < 2 hours | File Share unavailable |
| Low | Single user issue | Next available | Password reset |

---

## Appendix B – Estimated Resolution Times

| Scenario | Estimated Time |
|-----------|----------------|
| User Cannot Log In | 10–20 min |
| Computer Cannot Join Domain | 20–40 min |
| Secure Channel Failure | 15–30 min |
| Group Policy Not Applying | 20–45 min |
| DNS Resolution Failure | 20–40 min |
| DNS Registration Failure | 15–30 min |
| DHCP Lease Issues | 15–30 min |
| IP Address Conflict | 15–25 min |
| Shared Folder Access Denied | 20–45 min |
| Printer Unavailable | 15–30 min |
| Domain Controller Unavailable | 30–90 min |
| Active Directory Replication Failure | 45–120 min |

---

## Appendix C – Escalation Matrix

| Problem | Escalate To |
|-----------|-------------|
| Password Issues | Help Desk |
| DNS Issues | Systems Administrator |
| DHCP Issues | Systems Administrator |
| Active Directory | Systems Administrator |
| Domain Controller Failure | Infrastructure Team |
| Replication Failure | Infrastructure Team |
| Security Incident | Security Operations |

---

## Appendix D – Common Network Ports

| Port | Protocol | Service |
|------|----------|----------|
| 53 | TCP/UDP | DNS |
| 67 | UDP | DHCP Server |
| 68 | UDP | DHCP Client |
| 88 | TCP/UDP | Kerberos |
| 135 | TCP | RPC |
| 139 | TCP | NetBIOS |
| 389 | TCP/UDP | LDAP |
| 445 | TCP | SMB |
| 464 | TCP/UDP | Kerberos Password Change |
| 636 | TCP | LDAPS |
| 3268 | TCP | Global Catalog |
| 3269 | TCP | Global Catalog SSL |

---

## Appendix E – Critical Windows Services

| Service | Purpose |
|----------|---------|
| NTDS | Active Directory Database |
| DNS | Name Resolution |
| DHCPServer | IP Address Assignment |
| Netlogon | Domain Authentication |
| KDC | Kerberos Authentication |
| DFSR | SYSVOL Replication |
| W32Time | Time Synchronization |
| LanmanServer | SMB File Sharing |

---

## Appendix F – Important Event IDs

| Event ID | Description |
|----------|-------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4740 | User Locked Out |
| 4768 | Kerberos Ticket Requested |
| 4769 | Kerberos Service Ticket |
| 4771 | Kerberos Authentication Failure |
| 5719 | Netlogon Failure |
| 4013 | DNS Startup Delay |
| 4015 | DNS Critical Error |
| 1058 | Group Policy Failure |
| 1129 | Group Policy Network Error |

---

## Appendix G – Administrative Command References

| Technology | Reference Document |
|------------|-------------------|
| Active Directory | AD-Commands.md |
| DNS | DNS-Commands.md |
| DHCP | DHCP-Commands.md |
| PowerShell | PowerShell-Commands.md |
| Validation | Validation-Checklist.md |

---

## Appendix H - Troubleshooting Decision Tree

User reports issue
        │
        ▼
Health Checks
        │
        ▼
Authentication?
 │
 ├──Yes → Scenario 1–4
 │
 ├──DNS?
 │      │
 │      ├──Scenario 5
 │      └──Scenario 6
 │
 ├──DHCP?
 │      │
 │      ├──Scenario 7
 │      └──Scenario 8
 │
 ├──File Access?
 │      │
 │      ├──Scenario 9
 │      └──Scenario 10
 │
 └──Infrastructure?
        │
        ├──Scenario 11
        └──Scenario 12

---

## Appendix I - Enterprise Troubleshooting Checklist

☐ Gather information
☐ Determine scope
☐ Verify symptoms
☐ Collect evidence
☐ Analyze evidence
☐ Form hypothesis
☐ Test hypothesis
☐ Implement resolution
☐ Validate resolution
☐ Document findings
☐ Close incident

---

## Appendix J – Acronyms

| Acronym | Meaning |
|----------|---------|
| AD | Active Directory |
| DC | Domain Controller |
| DHCP | Dynamic Host Configuration Protocol |
| DNS | Domain Name System |
| GPO | Group Policy Object |
| ITS | Information Technology Services |
| KDC | Key Distribution Center |
| LDAP | Lightweight Directory Access Protocol |
| SMB | Server Message Block |
| SYSVOL | System Volume |
| OU | Organizational Unit |
| FQDN | Fully Qualified Domain Name |

---

### End of Runbook

You have reached the end of the **Northwind Technologies Enterprise Operations Runbook**.

Continue to the **Revision History** and **Approval** sections for document governance information.

⬆️ **Back to [Table of Contents](#table-of-contents)**

---

## Related Documentation

The following documentation provides additional administrative procedures, command references, and incident runbooks that support this troubleshooting scenario.

### Administrative Command References

- AD-Commands.md
- DHCP-Commands.md
- DNS-Commands.md
- PowerShell-Commands.md

### Enterprise Documentation

- Troubleshooting.md
- Validation-Checklist.md

### Related Incident Runbooks

- Scenario 3 – Secure Channel Failure
- Scenario 5 – DNS Resolution Failure
- Scenario 11 – Domain Controller Unavailable
- Scenario 12 – Time Synchronization Failure

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
|----------|------|--------|-------------|
| 1.0 | July 2026 | Brandon J. Cooper | Initial Release |

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
