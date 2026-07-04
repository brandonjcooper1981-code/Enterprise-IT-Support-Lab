# Windows 11 Enterprise Installation

## Engineering Guide

This document describes the Northwind Technologies engineering standard for deploying Windows 11 Enterprise within the Enterprise IT Modernization Project.

## Quick Reference

| Item | Value |
|------|-------|
| Estimated Build Time | 30–45 Minutes |
| Difficulty | Intermediate |
| System | CLIENT01 |
| Operating System | Windows 11 Enterprise |
| Dependencies | Oracle VirtualBox, Windows Server 2025 (DC01) |
| Validation Required | Yes |
| Expected Outcome | Enterprise workstation installed, configured, and ready for Active Directory domain join |

## Purpose

Deploy and configure a Windows 11 Enterprise workstation that serves as the primary enterprise client for validating Active Directory, Group Policy, enterprise networking, file services, and Help Desk operations throughout the Northwind Technologies environment.

## Business Reason

CLIENT01 was deployed as a dedicated enterprise workstation to simulate the experience of an end user within the Northwind Technologies environment. Rather than performing all administration directly from DC01, the workstation allowed authentication, Group Policy processing, file access, Help Desk validation, and troubleshooting to be tested from the same perspective as employees using the network each day. Separating the server and client systems also provided a more realistic enterprise architecture and improved the ability to diagnose networking and security issues.

## Architecture Decision

Windows 11 Enterprise was selected because it is the current Microsoft enterprise desktop operating system and reflects what many organizations deploy in production environments. Using Windows 11 Enterprise provided realistic experience with modern domain integration, Group Policy processing, and enterprise workstation administration. This decision ensured compatibility with the remaining Microsoft enterprise infrastructure while accurately reflecting modern corporate desktop environments.

## Prerequisites

The following requirements must be completed before beginning this procedure.

- Oracle VirtualBox installed and operational
- Windows Server 2025 (DC01) installed
- Windows 11 Enterprise ISO available
- Virtual machine created for CLIENT01
- Enterprise networking configured
- Static IP and DNS operational on DC01

## Procedure

1. Deploy the CLIENT01 Virtual Machine

   A dedicated Windows 11 Enterprise virtual machine was created to serve as the primary enterprise workstation. Hardware resources and virtual networking were configured according to the Northwind Technologies virtualization standard established during Milestone 1.

2. Install Windows 11 Enterprise

   Successful installation was verified by confirming that Windows 11 booted correctly, all available updates were installed, Device Manager reported no hardware issues, and the operating system functioned normally before enterprise configuration began.

3. Configure Intiial Workstation Settings

   The server hostname was changed to CLIENT01 to align with the Northwind Technologies server naming standard. Establishing standardized naming conventions early in the deployment simplified future administration, troubleshooting, and documentation.

4. Verify Network Connectivity

   CLIENT01 was considered ready once network connectivity was confirmed, DNS resolution successfully located DC01, and communication with the domain controller was verified through successful ping testing. These validation steps confirmed that the workstation was prepared to join the Active Directory domain.

5. Prepare for Domain Join

   Final verification confirmed that Windows 11 Enterprise booted successfully, network connectivity was operational, administrative access functioned correctly, and the system was fully prepared to join the Active Directory domain.

6. Confirm Enterprise Readiness

   Final readiness verification confirmed that CLIENT01 was fully operational and prepared for Active Directory integration. Successful communication with DC01, verified DNS resolution, and a stable Windows installation established the workstation as the enterprise validation platform for all subsequent Sprint 1 activities.

## Validation Criteria

Successful deployment was confirmed by verifying:

- Windows 11 booted successfully.
- All Windows updates completed.
- Device Manager reported no hardware issues.
- CLIENT01 communicated with DC01.
- DNS resolution succeeded.
- CLIENT01 successfully pinged the Domain Controller.
- Workstation prepared for Active Directory domain join.

## Troubleshooting

| Issue                           | Resolution                                         |
| ------------------------------- | -------------------------------------------------- |
| Boot order incorrect            | Adjusted boot priority in VirtualBox               |
| VirtualBox networking incorrect | Reconfigured NAT and Host-Only adapters            |
| DNS configuration incorrect     | Updated preferred DNS server to point to DC01      |
| Client connectivity issues      | Corrected IP addressing and verified communication |

## Operational Perspective

CLIENT01 provides the operational viewpoint of the enterprise environment. While DC01 hosts the infrastructure services, CLIENT01 validates that those services function correctly from the perspective of an end user. Maintaining a dedicated client workstation allows Help Desk personnel to troubleshoot authentication, permissions, network connectivity, and desktop configuration without affecting administrative operations on the domain controller.

## Lessons Learned

 - Always verify DNS configuration before troubleshooting domain connectivity.
 - Install all Windows updates before joining the workstation to the domain.
 - Verify virtual hardware configuration and boot order before beginning operating system installation.

---

## Related Engineering Guides

- Oracle VirtualBox Configuration
- Windows Server 2025 Installation
- Active Directory Deployment
- Enterprise Validation

---

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Engineering Documentation Standard

© 2026 Northwind Technologies
