# IT Infrastructure & Service Operations

A hands-on IT infrastructure and service operations project simulating a business IT environment, with practical implementations in IT service management, Windows administration, endpoint troubleshooting, identity and access management, networking, infrastructure monitoring and cloud operations.

## Project Overview

| Attribute | Details |
|---|---|
| Organization | Desert Bay Trading LLC (Fictional) |
| Organization Size | 20–30 simulated employees |
| Environment | Business IT Infrastructure |
| Project Type | Personal Technical Project |
| Status | In Progress |

## Technology Stack

### Implemented Technologies
- Windows 11
- Windows PowerShell
- GLPI
- MariaDB
- Docker and Docker Compose
- Linux — Ubuntu WSL2
- NTFS and SMB
- Git and GitHub

### Planned and Ongoing Technologies
- Cisco Packet Tracer
- Active Directory
- Group Policy
- Microsoft 365
- Microsoft Entra ID
- Microsoft Intune
- Remote Desktop Support
- AWS
- Prometheus and Grafana
- Ansible
- Terraform
- CI/CD

## Project Objectives

- Implement centralized IT helpdesk operations.
- Manage IT assets and employee service requests.
- Perform Windows endpoint administration and troubleshooting.
- Implement secure identity and access management.
- Develop network troubleshooting capabilities.
- Practise enterprise endpoint and Microsoft 365 administration.
- Automate routine infrastructure administration.
- Integrate infrastructure monitoring and cloud operations.

## Implementation Progress

| Phase | Module | Status |
|---|---|---|
| 0 | Project Preparation | Completed |
| 1 | IT Helpdesk & Asset Management | Practical Completed |
| 2 | Hardware & Operating System Support | Practical and Concept Study Completed |
| 3 | Windows Administration & PowerShell | In Progress |
| Upcoming | Networking & Troubleshooting | Planned |
| Upcoming | Active Directory Administration | Planned |
| Upcoming | Microsoft 365 & Endpoint Management | Planned |
| Upcoming | Remote Support & Incident Simulations | Planned |
| Upcoming | Cloud Operations & Automation | Planned |

## Phase 1 — IT Helpdesk & Asset Management

### Implemented Features

- Deployed GLPI and MariaDB using Docker Compose.
- Configured a fictional business helpdesk environment.
- Created employee accounts, technicians and support groups.
- Configured user profiles and permissions.
- Created an inventory of laptops, printers and network equipment.
- Allocated laptop DBT-LT-016 to a simulated employee.
- Practised five initial incident and service request workflows.
- Configured manual and automatic SLA assignment.
- Verified automatic Time to Own and Time to Resolve SLA assignment.
- Practised incident escalation and ticket resolution.
- Created five knowledge base articles.

### Initial Ticket Workflow Results

| Ticket | Recorded Status |
|---|---|
| Outlook will not open | Closed |
| Printer offline on Floor 2 | Closed |
| Locked account | Closed |
| New joiner needs a laptop and account | Pending |
| Floor 2 Wi-Fi has no internet | Processing |

These are simulated helpdesk scenarios. Some underlying technical implementations remain for later phases.

## Phase 2 — Hardware & Operating System Support

### Practical Activities

- Inspected Windows operating system configuration and disk partitions.
- Verified UEFI, GPT, TPM and Secure Boot configuration.
- Investigated Windows Boot Manager and recovery environment.
- Inspected device drivers and wireless network adapter information.
- Performed CPU, memory, storage and battery health diagnostics.
- Investigated application crashes using Event Viewer and Reliability Monitor.
- Performed file backup and restoration with SHA256 integrity verification.
- Troubleshot printer queues and Windows Print Spooler services.

### Implementation Limitations

Windows installation was studied conceptually due to available hardware resources. Supported practical diagnostics were performed on the Windows host. Printer troubleshooting used virtual printers rather than physical printing equipment.

## Phase 3 — Windows Administration & PowerShell

### Lesson 1 — Windows Users and Groups

Status: Practical Completed

- Created three employee test accounts.
- Created three departmental security groups.
- Configured standard user permissions.
- Performed password resets and account enable/disable operations.
- Managed departmental group membership.
- Investigated Windows authentication events.
- Practised authentication incident troubleshooting.

### Lesson 2 — NTFS Permissions & SMB File Sharing

Status: Practical Completed

- Implemented Finance, Sales, HR and Public directories.
- Configured departmental NTFS permissions and inheritance.
- Applied group-based least-privilege access control.
- Configured SMB file sharing and Access-Based Enumeration.
- Practised network drive mapping and SMB session monitoring.
- Tested authorized and unauthorized departmental access.
- Investigated and resolved a simulated file access incident.

SMB testing was performed using the same Windows host.

### Lesson 3 — Windows Application Management

Status: In Progress

### Remaining Lessons

- Windows Services and Processes
- Windows Updates and Security
- PowerShell Fundamentals and Scripting
- PowerShell Administration Automation

## Incident Management Portfolio

| Incident | Description | Recorded Outcome |
|---|---|---|
| INC-0021 | Hardware and application reliability investigation | Investigation performed; final repair unconfirmed |
| INC-0022 | Printer and Print Spooler troubleshooting | Solved |
| INC-0023 | Windows authentication failure | Solved in lab |
| INC-0024 | Departmental shared folder access denied | Solved in lab |

## Repository Structure

- `docs/` — Implementation documentation and troubleshooting logs
- `docker/` — Container configurations
- `incidents/` — Incident documentation
- `labs/` — Practical lab exercises
- `screenshots/` — Implementation evidence
- `scripts/` — Administration and automation scripts
- `aws/` — Cloud infrastructure activities

## Documentation and Evidence

- [Phase 1 — Implementation Log](docs/Phase-1-Log.md)
- [Phase 2 — Implementation Log](docs/Phase-2-Log.md)
- [Phase 3 — Implementation Log](docs/Phase-3-Log.md)
- [Phase 3 — NTFS and SMB Implementation](docs/Phase-3-Lesson-2.md)
- [Practical Screenshots](screenshots/phase1/)

## Scope and Limitations

This project represents a simulated business IT environment, not a production company infrastructure.

Activities are classified as implemented, lab practice or concept studied. Planned technologies are not represented as completed implementations.

## Project Status

Actively developing Windows administration, enterprise IT support, networking, infrastructure automation and cloud operations capabilities.
