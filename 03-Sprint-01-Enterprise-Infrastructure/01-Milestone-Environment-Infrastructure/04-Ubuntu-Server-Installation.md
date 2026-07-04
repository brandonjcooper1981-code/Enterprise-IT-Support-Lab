# Unbutu Server Installation

## Engineering Guide

This document describes the Northwind Technologies engineering standard for deploying Ubuntu Server within the Enterprise IT Modernization Project.

## Quick Reference

## Purpose

Initially, the Ubuntu Server was introduced to host Wazuh for centralized security monitoring and diagnostics. As the Northwind Technologies environment expanded, its role evolved to include osTicket, providing a dedicated Linux platform for enterprise Help Desk operations and ticket management.

## Business Reason

Ubuntu Server was introduced to the Northwind Technologies environment to support enterprise applications that perform more efficiently on Linux than on Windows Server. Its lightweight architecture, open-source ecosystem, and efficient resource utilization made it well suited for hosting security monitoring platforms, Help Desk applications, automation services, and other Linux-native enterprise workloads.

## Platform Strategy

Northwind Technologies adopts a multi-platform infrastructure strategy by selecting operating systems based on workload requirements rather than maintaining a single-platform environment. Windows Server provides centralized identity, authentication, and enterprise administration, while Ubuntu Server hosts Linux-native applications that benefit from greater resource efficiency, software compatibility, and open-source flexibility. This strategy reflects modern enterprise practices and prepares the infrastructure for future cloud, automation, and security initiatives.

## Architecture Decision

Ubuntu Server was selected because of its widespread adoption across enterprise environments, extensive software compatibility, and strong integration with cloud platforms including Microsoft Azure and Amazon Web Services. Its large support community, long-term support releases, and APT package management system simplify deployment while providing enterprise-grade stability.

## Prerequisites

The following requirements must be completed before beginning this procedure.

- Oracle VirtualBox installed and operational
- Windows Server 2025 (DC01) installed
- Windows 11 Enterprise (CLIENT01) installed
- Virtual machine created for CLIENT01
- Enterprise networking configured
- Static IP and DNS operational on DC01

## Required Software

- Ubuntu Server LTS ISO
- Oracle VirtualBox
- SSH
- APT Package Manager

## Implementation Procedure



## Validation Criteria

Successful deployment was confirmed by verifying:

- Unbuntu Server booted successfully.
- All apt updates completed.
- All services correctly installed and working properly.
- Unbuntu Server communicated with DC01.
- DNS resolution succeeded.
- Umbuntu Server successfully pinged the Domain Controller.
- Workstation prepared for Active Directory domain join.

## Troubleshooting

| Issue                               | Resolution                                               |
| ----------------------------------- | -------------------------------------------------------- |
| SSH communication failures          | Verified networking and SSH configuration                |
| VirtualBox adapter misconfiguration | Reconfigured Adapter 1 (NAT) and Adapter 2 (Host-Only)   |
| sudo command errors                 | Corrected command syntax                                 |
| Package upgrade failures            | Used package commands appropriate for the Ubuntu version |

## Operational Perspective

Linux and Windows Server serve different roles within the Northwind Technologies environment. Windows Server provides centralized identity management, enterprise administration, and Active Directory services, while Ubuntu Server hosts Linux-native enterprise applications including security monitoring and Help Desk platforms. Using each operating system where it performs best creates a more secure, flexible, and scalable infrastructure than relying on a single platform for every workload.

## Lessons Learned

- Verify VirtualBox networking before powering on the server.
- Validate command syntax before troubleshooting operating system issues.
- Confirm package manager commands match the installed Ubuntu release.

---

## Related Engineering Guides

- Oracle VirtualBox Configuration
- Windows Server 2025 Installation
- Windows 11 Enterprise Installation
- Active Directory Deployment
- Enterprise Validation

---

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Engineering Documentation Standard

© 2026 Northwind Technologies
