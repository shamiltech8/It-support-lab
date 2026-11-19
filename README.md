# Small Business IT Support & Cloud Operations Lab

A practical IT infrastructure and cloud operations project simulating the responsibilities of an IT Support and Cloud Operations Engineer in a small business.

## Company Scenario

**Company:** Desert Bay Trading LLC (Fictional)

**Employees:** 20–30

**Environment:** Small business IT infrastructure

**Project Objectives:**
- IT helpdesk and incident management
- IT asset inventory and allocation
- Windows desktop support
- Networking and troubleshooting
- User and access administration
- Microsoft 365 and cloud operations
- Infrastructure monitoring and automation

## Phase 1: GLPI Helpdesk & Asset Management

**Status: Completed — core practical exercises**

### Technologies
- GLPI 12
- MariaDB
- Docker
- Docker Compose
- Ubuntu WSL2

### Implemented Features

**1. Helpdesk Deployment**
- Deployed GLPI and MariaDB using Docker Compose.
- Configured the fictional company environment.

**2. User Management**
- Created fictional employee accounts.
- Configured technicians, groups and user permissions.
- Assigned the Self-Service profile to an employee.

**3. IT Asset Management**
- Created an inventory of laptops, printers and network equipment.
- Linked assets to support tickets.
- Allocated laptop DBT-LT-016 to Costa Danial.
- Updated the laptop inventory status from In stock to In use.

**4. Incident and Service Request Management**
- Practised five helpdesk ticket workflows.
- Recorded public and private follow-ups.
- Documented simulated troubleshooting.
- Practised ticket escalation to IT Management.

**5. SLA Management**
- Configured service-level agreements.
- Assigned SLAs manually to five tickets.
- Created a business rule using Urgency = High.
- Configured automatic SLA TTO and SLA TTR assignment.
- Verified successful automatic assignment using a temporary test ticket.

**6. Knowledge Management**
- Created five IT knowledge-base articles.

### Ticket Workflow Results

| Ticket | Final Status |
|---|---|
| Outlook will not open | Closed |
| Printer offline on Floor 2 | Closed |
| Locked account | Closed |
| New joiner needs a laptop and account | Pending |
| Floor 2 Wi-Fi has no internet | Processing (Assigned) |

The onboarding and Wi-Fi tickets remain unresolved because the remaining technical work has not been completed.

### Scope and Limitations

This is a simulated small-business IT environment.

- Helpdesk workflows and asset records were configured in GLPI.
- Some troubleshooting resolutions were simulated rather than performed on physical equipment.
- Windows and Microsoft 365 account provisioning remain for later project phases.
- Automatic SLA assignment was successfully tested.
- Manual escalation routing was verified; automatic escalation remains unverified.

## Project Evidence

Screenshots are stored in:

`screenshots/phase1/`

The collection documents the GLPI implementation, ticket management and SLA configuration.

## Upcoming Phases

- Windows Desktop Support and PowerShell
- Networking and troubleshooting
- Active Directory administration
- Microsoft 365 and endpoint management
- IT incident simulations
- AWS Cloud and DevOps operations

## Project Status

Phase 1 core exercises completed. Remaining phases are in progress.
