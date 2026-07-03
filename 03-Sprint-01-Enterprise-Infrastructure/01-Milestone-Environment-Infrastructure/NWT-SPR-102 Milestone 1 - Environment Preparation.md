| Property | Value |
|----------|-------|
| **Company** | Northwind Technologies |
| **Department** | Information Technology Services (ITS) |
| **Document ID** | NWT-SPR-102 |
| **Document Type** | Milestone Documentation |
| **Classification** | Internal Use |
| **Version** | 1.0 |
| **Status** | Approved |
| **Author** | Brandon J. Cooper |
| **Document Owner** | Information Technology Services (ITS) |
| **Last Updated** | June 2026 |

# NWT-SPR-102 Milestone 1 – Environment Preparation

*Enterprise IT Modernization Project*

---

# Executive Summary

Milestone 1 establishes the virtual infrastructure required to support the Northwind Technologies Enterprise IT Modernization Project.

This phase focuses on preparing a standardized deployment environment that provides the foundation for all subsequent infrastructure implementation activities, including Active Directory, enterprise networking, file services, and Help Desk operations.

---

# Project Snapshot

| Property | Value |
|----------|-------|
| Project | Enterprise IT Modernization Project |
| Sprint | Sprint 1 |
| Milestone | 1 |
| Phase | Environment Preparation |
| Project Lead | Brandon J. Cooper |
| Status | Complete |

---

# Business Impact

Establishing a standardized virtualization platform provided Northwind Technologies with a repeatable, isolated, and scalable environment for deploying enterprise infrastructure.

By investing in a consistent deployment environment before implementing production services, the organization reduced deployment risk, simplified troubleshooting, improved documentation accuracy, and created a reliable foundation for future infrastructure expansion.

This milestone ensures that all subsequent implementation activities are performed within a controlled and validated environment that reflects enterprise deployment practices.

---

# Business Need

Northwind Technologies required a dedicated enterprise infrastructure capable of supporting centralized identity management, network services, file services, and Help Desk operations.

Before production services could be deployed, a standardized virtualization platform needed to be designed, configured, and validated to ensure consistent system performance and repeatable implementation procedures.

Milestone 1 addresses these requirements by establishing the foundational infrastructure upon which all remaining Sprint 1 activities depend.

---

# Objectives

Milestone 1 was designed to accomplish the following objectives:

- Prepare the Oracle VirtualBox virtualization platform.
- Deploy Windows Server 2025.
- Deploy Windows 11 Enterprise.
- Deploy Ubuntu Server.
- Configure enterprise virtual networking.
- Assign standardized system names.
- Validate communication between systems.
- Prepare the environment for Active Directory deployment.

---

# Architecture References

This milestone supports the enterprise architecture defined in:

- NWT-ENT-001 Company Profile
- NWT-ENT-002 Enterprise Architecture
- NWT-ENT-003 Enterprise Network Diagram
- NWT-PM-001 Project Charter

---

# Implementation

## Phase 1 – Environment Planning

The Enterprise IT Modernization Project began with the objective of building a realistic Help Desk environment. As planning progressed and additional enterprise services were introduced, the project naturally evolved into a fully functioning Information Technology Services (ITS) department for Northwind Technologies.

A virtualized infrastructure was selected to provide a flexible, scalable, and cost-effective deployment platform. Virtualization significantly reduced the need for additional physical hardware while minimizing space requirements, simplifying maintenance, and allowing the environment to be easily modified, tested, and restored throughout the implementation process. These advantages made virtualization the preferred solution for developing and validating the enterprise infrastructure.

During the planning phase, three core systems were identified as essential to the project:
Each virtual machine was assigned a clearly defined operational role to support the enterprise services planned for Sprint 1.

- **DC01** – Windows Server 2025 to provide enterprise infrastructure services including Active Directory, DNS, DHCP, file services, and centralized administration.
- **CLIENT01** – Windows 11 Enterprise workstation used for domain integration, end-user validation, policy testing, and troubleshooting activities.
- **Ubuntu Server** – Linux server hosting the osTicket Help Desk platform and supporting services.

Although each virtual machine was assigned an initial purpose during planning, the overall environment evolved throughout implementation as additional enterprise services, documentation standards, and operational requirements were identified. This iterative approach allowed the infrastructure to grow naturally while maintaining alignment with the goals of the Enterprise IT Modernization Project.

The primary objective of the planning phase remained consistent throughout the project: to build a realistic enterprise environment that accurately reflected the daily responsibilities of an Information Technology Services department while providing practical experience with enterprise infrastructure deployment, administration, troubleshooting, and documentation.

The environment established during this phase provided the standardized foundation required for the successful implementation of Active Directory, enterprise network services, file services, and Help Desk operations documented throughout the remaining Sprint 1 milestones.

## Phase 2 – Oracle VirtualBox Configuration

Oracle VirtualBox was selected as the virtualization platform for the Enterprise IT Modernization Project due to its familiarity, flexibility, and suitability for enterprise lab development. Having previously used Oracle VirtualBox throughout the NGT Academy training program, the platform provided a reliable foundation while allowing implementation efforts to focus on enterprise infrastructure rather than learning a new virtualization solution.

Before any virtual machines were deployed, the implementation environment required careful preparation. Installation media for Windows Server 2025, Windows 11 Enterprise, Ubuntu Server were downloaded and organized to ensure each operating system was readily available throughout the deployment process. In addition, sufficient host storage, processor resources, and memory allocations were verified to support multiple simultaneously running virtual machines.

Virtual machine resource allocation was planned to provide stable performance while remaining within the capabilities of the host workstation. Each virtual machine was initially assigned a minimum of 4 GB of memory, which provided sufficient performance for operating system installation, enterprise services, validation activities, and troubleshooting throughout Sprint 1.

Enterprise network communication was established through a standardized dual-adapter configuration for every virtual machine. Each system utilized:

- **Adapter 1:** NAT Network for Internet connectivity and software updates.
- **Adapter 2:** Host-Only Adapter to provide isolated communication between enterprise systems within the Northwind Technologies environment.

This configuration allowed the environment to maintain Internet access while simultaneously supporting secure internal communication between the domain controller, client workstation, Linux servers, and supporting enterprise services.

Several implementation challenges were encountered while preparing the virtualization platform. Initial deployment issues included incorrect virtual network adapter assignments, boot failures caused by improper virtual boot order configuration, and installation media that was either improperly attached or failed to mount correctly. Each issue was investigated, corrected, and validated before continuing with subsequent infrastructure deployment activities.

Completing the virtualization platform before installing enterprise services established a stable baseline for the remainder of Sprint 1. By validating the virtualization environment first, future troubleshooting efforts could focus on operating system and infrastructure configuration rather than underlying platform issues. This phased implementation strategy reduced deployment risk while improving consistency throughout the Enterprise IT Modernization Project.

## Phase 3 – Windows Server 2025 Deployment

Windows Server 2025 was selected as the enterprise server platform for the Northwind Technologies Enterprise IT Modernization Project because it represented the latest Microsoft server operating system while providing the most current enterprise features and management capabilities. As the foundation of the organization's infrastructure, Windows Server 2025 offered an ideal environment for developing practical experience with modern enterprise administration while reflecting technologies commonly deployed throughout business environments.

The Windows Server deployment was prioritized before all other enterprise services because it would become the central management platform for the entire environment. Core infrastructure services including Active Directory Domain Services, DNS, DHCP, centralized authentication, and enterprise administration would all rely upon the successful deployment and configuration of this server. Establishing a stable server platform first ensured that subsequent implementation phases were built upon a reliable and validated foundation.

Following the initial operating system installation, the first administrative task was to rename the server according to the Northwind Technologies naming standard. The system was assigned the hostname DC01 in accordance with the Northwind Technologies server naming standard, identifying it as the organization's first Domain Controller. Establishing standardized naming conventions early in the deployment improved administrative consistency while simplifying future management and troubleshooting activities.

Once the server identity had been established, a static IPv4 address was assigned to provide consistent network communication throughout the enterprise environment. Maintaining a fixed IP address ensured that infrastructure services, client systems, and future server roles could consistently locate and communicate with the enterprise server throughout the deployment process.

Successful deployment was validated through multiple verification procedures. Windows Server completed installation successfully, administrative logins were verified, Server Manager loaded without errors, and the operating system demonstrated stable functionality. These validation activities confirmed that the server was ready for enterprise role installation and additional infrastructure configuration.

Several implementation challenges were encountered during server deployment. Initial boot failures were traced to incorrect virtual machine boot order settings, while subsequent networking issues required adjustments to the virtual network adapters, DNS configuration, and static IP addressing. Each issue was systematically investigated and resolved before continuing with additional infrastructure deployment, ensuring that the operating system platform remained stable throughout the remainder of the project.

Preparing the Windows Server environment before introducing Active Directory significantly reduced deployment risk by establishing a stable infrastructure platform capable of supporting enterprise services. As the central management system within the Northwind Technologies environment, the server became the foundation upon which identity management, network services, file services, and centralized administration would ultimately depend. Completing this phase successfully prepared the environment for the Active Directory infrastructure deployment documented in Phase 4.

## Phase 4 – Active Directory Domain Services

Active Directory Domain Services (AD DS) was implemented to establish a centralized identity and access management platform for the Northwind Technologies enterprise environment. By centralizing authentication, authorization, and directory services, Active Directory enabled the organization to control user access, enforce security policies, and provide role-based administration across the network. This implementation significantly improved both security and operational efficiency by ensuring that only authorized users could access enterprise resources appropriate to their assigned responsibilities.

The deployment of Active Directory Domain Services immediately followed the successful installation of Windows Server 2025, establishing the identity and management foundation required for all subsequent enterprise infrastructure services. Domain Services provide the framework for user authentication, organizational management, Group Policy enforcement, and centralized administration. Establishing this foundation before deploying additional services ensured that every future implementation activity aligned with the organization's security and management standards.

The enterprise domain **NORTHWIND.LOCAL** was selected to provide a clearly identifiable internal Active Directory namespace for the organization. The domain name reflects the Northwind Technologies enterprise while providing a simple, recognizable, and standardized namespace for internal authentication and administration.

Following successful installation, the Windows Server was promoted to the organization's first Domain Controller (DC01), transforming it from a standalone server into the centralized management platform for the enterprise. This promotion enabled centralized authentication, integrated DNS services, enterprise administration, and directory management while establishing the core infrastructure required to support future server roles and enterprise services.

Initial Active Directory configuration focused on establishing the logical structure of the enterprise environment. Organizational Units (OUs), user accounts, security groups, and Group Policy foundations were created to organize administrative responsibilities and prepare the environment for role-based access control. This structured design simplified user management while supporting future expansion of the enterprise infrastructure.

Deployment success was validated through functional testing of the Active Directory environment. User accounts were successfully authenticated against the domain, and multiple users were able to sign in to **CLIENT01** using their assigned domain credentials. Successful authentication confirmed that directory services, DNS integration, and domain communications were operating as expected.

Several implementation challenges were encountered during deployment. Domain join failures required additional troubleshooting of DNS and network configuration before client systems could successfully authenticate with the domain. Additional administrative effort was required to ensure users were assigned to the appropriate security groups, allowing permissions and Group Policy settings to function as intended. Each issue was investigated, corrected, and validated before the deployment proceeded.

Implementing Active Directory transformed the environment from a collection of independent virtual machines into a centrally managed enterprise network. By establishing a single source of identity, authentication, authorization, and administrative control, Active Directory became the operational core of the Northwind Technologies infrastructure. This phase established the security, management, and organizational framework required for the remaining Sprint 1 implementation activities.

## Phase 5 – Enterprise Organizational Structure

Following the successful deployment of Active Directory Domain Services, the logical structure of the Northwind Technologies enterprise environment was established through the implementation of Organizational Units (OUs), departmental organization, user accounts, and security groups. Rather than maintaining all users within the default Active Directory containers, a structured organizational hierarchy was developed to improve administration, strengthen security, and support future enterprise growth.

Organizational Units were designed to logically organize enterprise users, computers, administrative resources, and future infrastructure objects according to departmental responsibilities and operational functions. This structure ensured that administrative tasks, security policies, and delegated permissions could be managed independently for each department while reducing the risk of unauthorized access to enterprise resources. By organizing objects into clearly defined administrative boundaries, the environment became significantly easier to manage and maintain.

Departmental Organizational Units were created with both business function and administrative hierarchy in mind. Each department received its own logical container while user accounts were organized according to operational responsibilities and levels of authority. This design provided a scalable framework capable of supporting future organizational expansion without requiring major structural changes to the directory environment.

Separating users into departmental Organizational Units also established a clearer chain of administrative accountability. Restricting access to department-specific resources allowed changes to be traced back to authorized personnel while reducing the likelihood of accidental modification or unauthorized access by users outside their assigned responsibilities. This approach improved both operational security and administrative oversight across the enterprise.

Security groups were implemented to simplify permission management throughout the Northwind Technologies environment. Rather than assigning permissions directly to individual user accounts, access was granted through role-based security groups aligned with departmental responsibilities. This methodology improved consistency, simplified user administration, and supported the Principle of Least Privilege by ensuring users received only the permissions required to perform their assigned job functions.

Establishing the Organizational Unit structure before implementing Group Policy provided a standardized administrative framework for enterprise management. Group Policy Objects (GPOs) could then be applied to entire departments, ensuring users within each Organizational Unit received consistent security settings, desktop configurations, software deployments, and administrative policies. This centralized management approach reduced administrative effort while improving configuration consistency throughout the organization.

Successful implementation was validated by confirming that user accounts appeared within their designated Organizational Units, security groups populated correctly, Group Policy updates were successfully applied, and users authenticated to **CLIENT01** using their assigned domain credentials. Additional validation confirmed that access to shared resources aligned with departmental security group memberships and organizational policies.

Several implementation challenges were encountered while organizing the Active Directory environment. Initial issues included users being assigned to incorrect Organizational Units or security groups, resulting in improper permission assignments and policy application. As directory changes propagated throughout the environment, administrative verification ensured each object was correctly placed before proceeding with additional configuration activities.

Designing the enterprise Organizational Unit structure before expanding the environment established a secure, scalable, and standardized administrative framework for Northwind Technologies. By organizing users, departments, and administrative responsibilities according to business function, the directory structure became the foundation for enterprise security, policy enforcement, software deployment, delegated administration, and future organizational growth.

## Phase 6 – Enterprise Network Services

Following the successful deployment of Active Directory and the enterprise organizational structure, Northwind Technologies implemented Domain Name System (DNS) and Dynamic Host Configuration Protocol (DHCP) services to establish reliable enterprise network communication. Together, these services automated client configuration, simplified network administration, and provided the infrastructure required for centralized authentication and resource access throughout the enterprise environment.

Implementing DNS and DHCP significantly reduced the administrative effort required to manage enterprise workstations. Rather than manually configuring every client system, DHCP automatically assigned network settings while DNS provided reliable name resolution between enterprise resources. This approach eliminated unnecessary manual configuration, reduced the likelihood of IP address conflicts, improved scalability, and simplified future workstation deployment and migration.

DNS quickly proved to be one of the most critical infrastructure services within the Northwind Technologies environment. Active Directory relies heavily upon DNS to locate domain controllers, authenticate users, register enterprise services, and maintain communication between client systems and domain resources. During implementation it became clear that incorrect DNS configuration prevented client authentication and disrupted normal Active Directory functionality, reinforcing the importance of accurate name resolution throughout the enterprise.

DHCP was implemented to automate network configuration and centrally manage enterprise IP address allocation. By maintaining a controlled address pool, DHCP simplified workstation deployment, reduced administrative overhead, and ensured consistent network configuration across client systems. Automated IP address management also reduced the risk of duplicate addresses and configuration inconsistencies while supporting future growth of the enterprise environment.

The enterprise network architecture was designed around a centralized Domain Controller using a static IPv4 address while all client systems received network configuration dynamically through DHCP. Each virtual machine was configured with standardized VirtualBox networking, including NAT connectivity for Internet access and a Host-Only Adapter for secure internal communication. This design ensured reliable connectivity between enterprise systems while maintaining access to external resources required for updates and software installation.

Network services were validated through comprehensive functional testing. CLIENT01 successfully obtained a valid IP address through DHCP, authenticated against the Active Directory domain, accessed enterprise shared folders, and communicated successfully with DC01. These validation activities confirmed that DNS resolution, DHCP address assignment, authentication services, and enterprise resource access were functioning as designed.

Several networking challenges were encountered throughout implementation. The most significant issues involved incorrect DNS server assignments and client systems that were unable to join the Active Directory domain. Additional troubleshooting included VirtualBox network adapter configuration and verification of static IP addressing on DC01. Each issue was systematically investigated, corrected, and validated before deployment activities continued. These experiences reinforced the importance of accurate network configuration as the foundation of enterprise infrastructure.

Successful implementation of DNS and DHCP transformed the Northwind Technologies environment into a centrally managed enterprise network capable of supporting secure authentication, automated workstation configuration, and reliable communication between enterprise systems. The deployment significantly improved operational efficiency while establishing the networking foundation required for all remaining Sprint 1 implementation activities.

One of the most valuable operational lessons learned during this phase was the importance of verifying DNS configuration before performing extensive troubleshooting. Because Active Directory depends upon accurate DNS resolution, validating DNS settings early in the troubleshooting process often resolved connectivity and authentication issues before more complex diagnostics were required. This approach became a standard troubleshooting practice throughout the remainder of the project.

## Phase 7 – Enterprise Validation & Operational Readiness

Following the successful deployment of the Northwind Technologies enterprise infrastructure, comprehensive validation testing was performed to confirm that all systems operated together as a fully integrated enterprise environment. Successful installation alone did not guarantee operational readiness; each infrastructure component required functional verification to ensure reliable communication, authentication, security enforcement, and resource accessibility before the environment could be considered production ready.

The validation process followed a structured approach designed to verify the enterprise from the core infrastructure outward. Testing began by confirming the operational status of **DC01**, ensuring that Active Directory, DNS, DHCP, and supporting infrastructure services were functioning correctly. Once server functionality was confirmed, validation proceeded to **CLIENT01**, where network connectivity, authentication, and enterprise resource access were verified from the perspective of an end user.

Infrastructure validation focused on confirming reliable communication between the Domain Controller and client workstation. Particular attention was given to DNS name resolution, DHCP address assignment, Active Directory authentication, and secure communication between enterprise systems. Establishing confidence in these foundational services allowed subsequent troubleshooting efforts to be isolated to either the server infrastructure or client workstation rather than the enterprise network as a whole.

End-to-end operational testing simulated normal business operations within the Northwind Technologies environment. Test users successfully authenticated to **CLIENT01**, automatically received network configuration through DHCP, authenticated against Active Directory, received the appropriate Group Policy settings, accessed authorized departmental shared folders, and were prevented from accessing resources outside their assigned security groups. Successful completion of these validation activities demonstrated that authentication, authorization, networking, and file services were functioning together as a unified enterprise solution.

Operational readiness was achieved once users consistently authenticated to the domain, accessed authorized resources, and were prevented from accessing unauthorized departmental information. Successful completion of these validation scenarios confirmed that enterprise security policies, network services, Active Directory, and file permissions were operating as designed and that the environment was prepared for continued infrastructure expansion.

Validation testing also identified several configuration issues requiring correction before final approval. These included incorrect Organizational Unit assignments, improper security group membership, and file share permission inconsistencies that prevented users from accessing the appropriate departmental resources. Each issue was investigated, corrected, and revalidated to ensure the final environment accurately reflected the intended enterprise security model.

Completing comprehensive validation significantly improved the operational reliability of the Northwind Technologies environment. Centralized administration simplified ongoing management, Group Policy and security groups strengthened enterprise security, and standardized configuration procedures established a repeatable deployment methodology for future users, systems, and infrastructure expansion.

Several important engineering lessons emerged during Sprint 1. Accurate DNS configuration proved essential to nearly every aspect of Active Directory functionality, reinforcing the practice of validating DNS before beginning extensive troubleshooting. Proper security group membership and Organizational Unit placement directly influenced policy application and resource access, emphasizing the importance of careful administrative verification. Finally, disciplined review of administrative commands, configuration settings, and implementation procedures consistently prevented unnecessary troubleshooting while improving overall deployment accuracy.

Successful completion of enterprise validation confirmed that Northwind Technologies had transitioned from a collection of individually configured systems into a fully integrated enterprise infrastructure. With operational readiness verified and all major Sprint 1 objectives successfully validated, the environment was approved for transition into the next implementation milestone.

## Phase 8 – Sprint Transition & Implementation Summary

Sprint 1 began as an effort to deploy Active Directory within a home lab environment and evolved into the foundational implementation phase of the Northwind Technologies Enterprise IT Modernization Project. What started as a Help Desk-focused Active Directory lab expanded into a complete enterprise infrastructure environment designed from the perspective of an Information Technology Services department. This evolution established a scalable foundation capable of supporting centralized administration, secure authentication, departmental access control, file services, documentation, and future infrastructure growth.

Through the successful completion of Sprint 1, Northwind Technologies gained several important business and operational capabilities. The organization now has centralized authentication, standardized infrastructure, improved departmental security, structured user and group management, enterprise file services, and a documentation framework that supports repeatable administration and future maintenance. These capabilities provide a consistent operational baseline for managing users, resources, policies, and support activities across the environment.

One of the most significant accomplishments of Sprint 1 was the successful deployment of a working Active Directory environment capable of supporting real enterprise administration. The completed environment demonstrates that Northwind Technologies now has a functional infrastructure platform that can authenticate users, enforce access control, support department-based permissions, and provide the foundation for additional enterprise services.

Several engineering lessons emerged throughout Sprint 1 that will guide future implementation work. Planning before deployment proved essential, as changing an existing plan is significantly easier than trying to recover from the absence of one. DNS validation became a standard troubleshooting priority due to its direct impact on Active Directory functionality, authentication, and domain communication. The importance of disciplined verification was reinforced throughout the sprint: check, double-check, and triple-check critical settings before moving forward.

Sprint 1 also reduced several operational risks. Automated DHCP configuration reduced the need for manual IP address assignment and lowered the likelihood of address conflicts. Standardized network configuration improved consistency across the environment. Centralized documentation created a repeatable process for rebuilding, troubleshooting, or expanding the infrastructure when necessary. Department-based access control also reduced the risk of unauthorized access to sensitive resources.

The Active Directory environment created during Sprint 1 serves as the baseline for all future modernization activities. Like the foundation of a building, this infrastructure must remain stable, documented, and validated so that future sprints can safely build upon it. While later phases will expand and improve the environment, the core infrastructure established during Sprint 1 remains the operational foundation of Northwind Technologies.

Sprint 1 was successful because the environment was planned, implemented, troubleshot, validated, and documented despite several technical challenges. The project encountered configuration issues, networking problems, permission errors, and multiple troubleshooting obstacles; however, each issue was addressed, corrected, and used as a learning opportunity. The final result is a working enterprise infrastructure environment that supports the continued growth of Northwind Technologies.

The completion of Sprint 1 represents more than the successful deployment of enterprise infrastructure. It establishes the operational standards, engineering practices, documentation framework, and technical foundation that will guide every subsequent phase of the Northwind Technologies Enterprise IT Modernization Project. With operational readiness confirmed, Sprint 1 is approved for transition into the next implementation milestone.

The only way the project fails is to give up.

---

# Validation

| Validation Test          | Result |
| ------------------------ | :----: |
| Windows Server Installed |    ✅   |
| Windows 11 Installed     |    ✅   |
| Ubuntu Installed         |    ✅   |
| Static IP Configured     |    ✅   |
| VM Communication         |    ✅   |

---

# Troubleshooting

VM wouldn't boot
Wrong adapter
ISO issue
Boot order
Guest Additions

---

# Lessons Learned

Plan networking before installing services.
Name systems consistently.
Validate after every major configuration.
Snapshots reduce recovery time.

---

# Project Metrics

| Metric              | Value |
| ------------------- | ----: |
| Virtual Machines    |     3 |
| Operating Systems   |     3 |
| Networks Configured |     2 |
| Validation Tests    |     7 |
| Issues Resolved     |     5 |

---

# Operational Readiness

| Component              | Status |
| ---------------------- | :----: |
| Virtual Infrastructure |    ✅   |
| Windows Server         |    ✅   |
| Windows Client         |    ✅   |
| Ubuntu Server          |    ✅   |
| Network Connectivity   |    ✅   |
| Ready for Milestone 2  |    ✅   |

| Question                                         | Status |
| ------------------------------------------------ | :----: |
| Were all milestone objectives completed?         |    ✅   |
| Were validation tests successful?                |    ✅   |
| Are known issues documented?                     |    ✅   |
| Is supporting documentation complete?            |    ✅   |
| Is the environment ready for the next milestone? |    ✅   |

## Operational Readiness Statement

Following successful implementation, validation, and documentation, Milestone 1 has been completed and approved for transition to Milestone 2 – Active Directory Infrastructure.

---

# Related Readiness

NWT-SPR-101

NWT-ENT-001

NWT-ENT-002

NWT-PM-001

NWT-STD-001

NWT-STD-002

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
| 1.0 | June 2026 | Brandon J. Cooper | Initial release |

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
