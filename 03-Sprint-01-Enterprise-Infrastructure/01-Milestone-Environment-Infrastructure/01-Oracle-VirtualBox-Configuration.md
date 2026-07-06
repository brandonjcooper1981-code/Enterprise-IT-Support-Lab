# Oracle VirtualBox Configuration

## Engineering Guide

This document describes the Northwind Technologies engineering standard for deploying Oracle VirtualBox within the Enterprise IT Modernization Project.

## Purpose

Deploy the virtualization platform required to support the Northwind Technologies enterprise environment.

## Business Reason

Oracle VirtualBox provides a repeatable, isolated, and cost-effective platform for developing and validating enterprise infrastructure.

## Architecture Decision

Oracle VirtualBox was selected as the enterprise virtualization platform because it provided a cost-effective, repeatable, and isolated environment suitable for developing enterprise infrastructure. Existing familiarity with the platform reduced implementation time and allowed project effort to focus on infrastructure design rather than learning a new hypervisor.

## Prerequisites

- Oracle VirtualBox installed
- Windows Server ISO
- Windows 11 ISO
- Ubuntu Server ISO

## Procedure

1. Prepare the Virtualization Environment

Before creating any virtual machines, Oracle VirtualBox was installed and verified on the host workstation. Installation media for Windows Server 2025, Windows 11 Enterprise, and Ubuntu Server were downloaded and organized to ensure each operating system was readily available during deployment.

2. Create the Virtual Machines

Three virtual machines were created to support the enterprise infrastructure.

System	Purpose
DC01	Windows Server 2025 Domain Controller
CLIENT01	Windows 11 Enterprise Workstation
Ubuntu Server	Linux server supporting enterprise services

3. Configure Virtual Hardware

Each virtual machine was configured with hardware resources appropriate for its intended role.

Configuration included:

Processor allocation
Memory allocation
Virtual hard disk creation
Installation media attachment
Boot order verification

Hardware resources were selected to provide stable performance while remaining within the limitations of the host workstation.

4. Configure Enterprise Networking

Each virtual machine was configured with two network adapters.

Adapter	Purpose
Adapter 1	NAT – Internet connectivity and updates
Adapter 2	Host-Only Adapter – Internal enterprise communication

This configuration allowed Internet access while maintaining isolated communication between enterprise systems.

5. Verify Environment Readiness

After configuration, each virtual machine successfully powered on, detected the attached installation media, and was prepared for operating system installation.

### Implementation Summary

This procedure documents the standardized Oracle VirtualBox configuration used throughout the Northwind Technologies Enterprise IT Modernization Project.

The virtualization platform provides the foundation for all Windows and Linux systems deployed during Sprint 1 and establishes a repeatable configuration for future enterprise infrastructure expansion.

## Validation Criteria

The following validation criteria were successfully verified:

- All virtual machines powered on successfully.
- Installation media mounted correctly.
- Boot order functioned as expected.
- Dual network adapters were detected.
- Internet connectivity was available through the NAT adapter.
- Internal communication was available through the Host-Only adapter.

## Troubleshooting

| Issue                                   | Resolution                                                      |
| --------------------------------------- | --------------------------------------------------------------- |
| VM booted to hard disk instead of ISO   | Corrected boot order and verified installation media attachment |
| Incorrect network adapter configuration | Reconfigured adapters to use NAT and Host-Only networking       |
| ISO failed to boot                      | Reattached installation media and verified VM storage settings  |
| Communication between VMs failed        | Corrected Host-Only network adapter assignment                  |

## Lessons Learned

Key lessons learned during virtualization deployment included:

- Verify network adapter assignments before beginning operating system installation.
- Confirm installation media is correctly attached prior to powering on each virtual machine.
- Validate boot order before troubleshooting operating system installation failures.
- Establish a standardized virtual machine configuration to simplify future expansion and maintenance.

## Related Engineering Guides

- Windows Server 2025 Installation
- Windows 11 Enterprise Installation
- Ubuntu Server Installation
- Environment Validation

---

Northwind Technologies

Information Technology Services (ITS)

Enterprise IT Modernization Project

Engineering Documentation Standard

© 2026 Northwind Technologies
