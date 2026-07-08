# NWT-STD-005 Enterprise Change Management Standard

| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-STD-005 |
| **Document Type** | Enterprise Governance Standard |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | July 2026 |

---

## Executive Summary

The Enterprise Change Management Standard establishes the standardized process for planning, reviewing, approving, implementing, validating, and documenting infrastructure changes throughout the Northwind Technologies Enterprise IT Modernization Project.

This standard minimizes operational risk, improves system stability, ensures consistent documentation, and provides a repeatable framework for infrastructure modifications across Windows Server, Active Directory, Linux servers, networking, PowerShell automation, security configurations, and future enterprise cloud services.

---

## Purpose

This standard defines how enterprise infrastructure changes are requested, evaluated, approved, implemented, validated, documented, and reviewed throughout the project lifecycle.

Objectives include:
- Standardize infrastructure changes
- Reduce operational risk
- Protect production services
- Improve change tracking
- Ensure backup validation
- Maintain documentation accuracy
- Support enterprise scalability

---

## Change Management Principles

Northwind Technologies follows these change management principles:
- Backup Before Change
- Test Before Production
- Document Every Change
- Validate Every Implementation
- Rollback Must Be Available
- Least Operational Impact
- Continuous Improvement
- Security First

---

## Enterprise Change Lifecycle

                  Change Requested
                         │
                         ▼
                 Impact Assessment
                         │
                         ▼
                  Risk Classification
                         │
                         ▼
                  Backup Verification
                         │
                         ▼
                  Change Approval
                         │
                         ▼
                 Implementation
                         │
                         ▼
                   Validation
                         │
                         ▼
                 Documentation Update
                         │
                         ▼
                    Change Closed

---

## Change Classification

| Change Type | Description                          |
| ----------- | ------------------------------------ |
| Standard    | Low-risk repeatable changes          |
| Normal      | Planned infrastructure modifications |
| Emergency   | Immediate corrective action          |

---

## Risk Classificaiton Matrix

| Risk     | Examples                                    |
| -------- | ------------------------------------------- |
| Low      | Documentation updates, PowerShell scripts   |
| Medium   | Group Policy, DHCP Scope Changes            |
| High     | Active Directory, DNS, Server Configuration |
| Critical | Domain Controller Recovery, Forest Changes  |

---

## Change Approval Matrix

| Change                 | Approval Required   |
| ---------------------- | ------------------- |
| Documentation          | Infrastructure Lead |
| PowerShell Script      | Infrastructure Lead |
| Active Directory       | CIO                 |
| DNS                    | CIO                 |
| DHCP                   | CIO                 |
| Group Policy           | CIO                 |
| Server Build           | CIO                 |
| Security Configuration | CIO                 |

---

## Pre-Implementation Checklist

Before implementation:
- Business impact reviewed
- Backup completed
- Snapshot created
- Rollback documented
- Dependencies verified
- Documentation reviewed
- Validation plan created
- Maintenance window scheduled (if required)

---

## Implementation Standards

Every infrastructure change shall include:
- Change Description
- Purpose
- Systems Affected
- Expected Outcome
- Rollback Plan
- Validation Method
- Completion Status

---

## Validation Requirements

Validation includes:
- Service Availability
- Authentication
- DNS Resolution
- DHCP Functionality
- Group Policy Processing
- File Share Access
- Application Availability
- Event Log Review

---

## Rollback Strategy

Rollback procedures include:
- Restore VirtualBox Snapshot
- Restore Configuration Export
- Restore Documentation
- Restore Previous PowerShell Version
- Verify Enterprise Services
- Revalidate Infrastructure

---

## Documentation Requirements

Every change must update:
- Enterprise Documentation
- Network Diagram (if required)
- Server Inventory (if required)
- IP Address Plan (if required)
- Security Baseline (if required)
- Repository README
- Sprint Documentation

---

## Change Record Template

| Item                  | Description         |
| --------------------- | ------------------- |
| Change ID             | CHG-YYYY-001        |
| Requestor             | Infrastructure Lead |
| Date                  | YYYY-MM-DD          |
| Systems Affected      | DC01                |
| Risk Level            | Medium              |
| Backup Completed      | Yes                 |
| Validation Complete   | Yes                 |
| Documentation Updated | Yes                 |
| Status                | Closed              |

---

## Emergency Changes

Emergency changes require:
- Immediate implementation
- Backup when possible
- Post-change documentation
- Validation
- Management notification
- Lessons Learned review

---

## Enterprise Change Workflow

Need Identified
       │
       ▼
Create Change
       │
       ▼
Review Risk
       │
       ▼
Backup
       │
       ▼
Implement
       │
       ▼
Validate
       │
       ▼
Update Documentation
       │
       ▼
Close Change

---

## Change Success Matrix

| Metric                   | Target |
| ------------------------ | ------ |
| Successful Changes       | >95%   |
| Rollback Rate            | <5%    |
| Documentation Compliance | 100%   |
| Backup Compliance        | 100%   |
| Validation Completion    | 100%   |

---

## Future Enterprise Enhancements

Planned improvements include:
- GitHub Change Tracking
- PowerShell Deployment Automation
- Automated Validation Scripts
- Automated Change Requests
- Infrastructure as Code
- Azure DevOps Integration
- Microsoft Intune Change Control
- Microsoft Entra ID Governance

---

## Validation Checklist

| Validation                         | Status   |
| ---------------------------------- | -------- |
| Backup Verified                    | Verified |
| Approval Process Defined           | Verified |
| Rollback Procedure Documented      | Verified |
| Validation Process Defined         | Verified |
| Documentation Requirements Defined | Verified |
| Workflow Standardized              | Complete |

---

## Related Documentation
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-004 Server Inventory
- NWT-ENT-005 Enterprise IP Address Plan
- NWT-ENT-008 Enterprise Security Baseline
- NWT-ENT-009 Enterprise Backup & Recovery Plan
- NWT-STD-001 Enterprise Documentation Standard
- NWT-STD-003 Engineering Documentation Standard
- NWT-STD-004 Repository Structure Standard

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

**Northwind Technologies**

**Information Technology Services (ITS)**

*Innovate • Secure •Support*

© 2026 Northwind Technologies
