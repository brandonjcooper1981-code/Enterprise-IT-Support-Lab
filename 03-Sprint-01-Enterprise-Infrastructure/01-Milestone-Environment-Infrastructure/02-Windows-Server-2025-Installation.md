# Windows Server 2025 Installation

## Quick Reference

| Item                 | Value                                                           |
| -------------------- | --------------------------------------------------------------- |
| Estimated Build Time | ~45–60 Minutes                                                  |
| Difficulty           | Intermediate                                                    |
| System               | DC01                                                            |
| Operating System     | Windows Server 2025                                             |
| Dependencies         | Oracle VirtualBox Configuration Complete                        |
| Validation Required  | Yes                                                             |
| Expected Outcome     | Windows Server operational and ready for baseline configuration |

## Purpose

Deploy the Windows Server 2025 operating system that serves as the foundational enterprise server for the Northwind Technologies infrastructure.

## Business Reason

Windows Server provides the centralized platform required to support enterprise identity management, network services, file services, and administrative operations. Establishing a stable server operating system is the first step toward deploying a secure and scalable enterprise infrastructure.

## Architecture Decision

Windows Server 2025 was selected because it represents Microsoft's current enterprise server platform while providing modern security features, long-term support, and compatibility with Active Directory Domain Services. Deploying the latest server operating system ensures the environment reflects technologies commonly found in modern enterprise environments.

## Prerequisites

The following requirements must be completed before beginning this procedure:

- Oracle VirtualBox installed and operational
- Virtual machine created for DC01
- Windows Server 2025 installation ISO available
- Hardware resources allocated according to the Milestone 1 deployment standard
- Enterprise networking configured (NAT and Host-Only adapters)

## Procedure

1. Prepare the Installation Media

Before deployment, the Windows Server 2025 installation media was verified to ensure the ISO was available and correctly attached to the DC01 virtual machine. Confirming installation media before powering on the virtual machine reduced the likelihood of deployment delays caused by missing or improperly mounted installation files.

2. Create the Virtual Machine

A virtual machine was created within the existing Oracle VirtualBox environment using the hardware specifications established during Milestone 1 planning. CPU, memory, storage, and networking were configured to support the enterprise server role while maintaining consistency with the Northwind Technologies virtualization standard.

3. Install Windows Server 2025

Windows Server 2025 was installed using the standard Microsoft installation process. Default installation options appropriate for an enterprise server deployment were selected, providing a clean operating system ready for post-installation configuration and enterprise service deployment.

4. Configure Initial Administrative Settings

After installation completed, initial administrative configuration tasks were performed to prepare the operating system for enterprise deployment. These activities included verifying administrative access, confirming successful operating system initialization, and reviewing Server Manager to ensure the installation completed without errors.

5. Rename the Server to DC01

The server hostname was changed to DC01 to align with the Northwind Technologies server naming standard. Establishing standardized naming conventions early in the deployment simplified future administration, troubleshooting, and documentation.

6. Configure Static IPv4 Address

A static IPv4 address was assigned to ensure reliable communication between enterprise systems. Maintaining a fixed address prevents infrastructure services such as Active Directory and DNS from depending on dynamically assigned network configurations, improving stability throughout the environment.

7. Verify Server Readiness

Final verification confirmed that Windows Server booted successfully, network connectivity was operational, administrative access functioned correctly, and the system was fully prepared for Active Directory deployment.

## Validation Criteria

The following validation criteria were successfully verified:

- Windows Server installation completed successfully.
- Administrative login verified.
- Server Manager launched without errors.
- Server renamed to DC01.
- Static IPv4 configuration applied successfully.
- Network connectivity confirmed.
- Environment ready for Active Directory deployment.

## Troubleshooting

| Issue                                     | Resolution                                                  |
| ----------------------------------------- | ----------------------------------------------------------- |
| VM failed to boot from installation media | Verified ISO attachment and corrected boot order            |
| Unable to configure networking            | Corrected VirtualBox adapter configuration                  |
| Incorrect DNS configuration               | Updated preferred DNS server and verified connectivity      |
| Static IP configuration errors            | Corrected IPv4 settings and validated network communication |

## Lessons Learned

- Rename the server immediately after installation to maintain naming consistency.
- Configure the static IPv4 address before installing server roles.
- Verify network connectivity before promoting the server to a Domain Controller.
- Establish a stable operating system baseline before introducing enterprise services.

## Related Engineering Guides

- Oracle VirtualBox Configuration
- Windows 11 Enterprise Installation
- Ubuntu Server Installation
- Environment Validation
