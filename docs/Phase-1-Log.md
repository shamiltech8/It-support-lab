# Phase 1 Log: GLPI helpdesk
Label: Real

## Problem 1: Docker install conflict
- Symptom: apt failed with a file clash on the Compose plugin.
- Root cause: Ubuntu's docker.io and Docker's official docker-ce ship the same files.
- Fix: removed the Ubuntu packages, reinstalled the official ones.
- Verification: docker --version, docker compose version, hello-world.

## Problem 2: GLPI container would not start
- Symptom: "address already in use" on port 8080.
- Investigation: sudo ss -ltnp showed a java process.
- Root cause: Jenkins was already using port 8080.
- Fix: published GLPI on 8081, stopped and disabled Jenkins to free RAM.

## Problem 3: Low RAM from earlier projects
- Symptom: high memory and swap use, unexpected /metrics requests in the GLPI log.
- Root cause: an earlier project's containers and services restarted with WSL.
- Fix: stopped them for lab sessions, without deleting anything.

## Problem 4: Could not log in with the default GLPI account
- Symptom: glpi/glpi and tech/tech were rejected.
- Investigation: the install log showed the default account was created, and the database listed the accounts as active.
- Fix: reset the password hash from the command line, then created my own admin and disabled the defaults.
- Root cause: not confirmed (probably an input problem).
- Lesson: check what the system actually holds before changing it.

## Problem 5: Could not see a group in a dropdown
- Symptom: Sales was missing from the options after I had added everyone.
- Investigation: a database query counted the members of each group.
- Finding: all four groups had the right number of members, so the dropdown was hiding groups already assigned.

## Problem 6: Manufacturer typo in the asset list
- Symptom: the manufacturer list showed "Lenova" instead of "Lenovo".
- Investigation: a database query listing the manufacturers.
- Root cause: a typing error when I created the dropdown value.
- Fix: renamed the entry once in GLPI, which updated every linked laptop.
- Prevention: check spelling and confirm each value in the list after adding it.

## Problem 7: Printer type and model dropdowns were empty
- Symptom: the Type and Model fields on the printer form showed no options.
- Investigation: queried the printer types and models tables. Both were empty.
- Root cause: my earlier entries had not been saved.
- Fix: recreated them under Setup > Dropdowns and confirmed each one appeared in the list.
- Lesson: "no error" does not prove it saved. Verify with a query.

## Problem 8: Extra clone records
- Symptom: an audit query found three records with "(copy)" in the name.
- Investigation: listed them with their serial numbers and deleted flag. All three were in the GLPI trash.
- Root cause: I entered the wrong number of copies when cloning.
- Fix: checked each serial first, then permanently deleted the three junk records.
- Verification: copies = 0, live laptops = 20, no serial outside the SN-XX-NNNN pattern.
- Prevention: check the number-of-copies box before cloning, then run the audit query.

## Lesson 5: Categories, SLA and escalation (GLPI 12.0.2)

Implemented: 10 ITIL categories, an office-hours calendar (Mon-Fri 08:00-17:00), four SLAs (P1-P4) each with time to own and time to resolve, and two escalation alarms on P1.
Verified: a ticket created on a Sunday got due dates on Monday 08:15 and 12:00, so the calendar works.
At the time of Lesson 5, automatic SLA assignment was not configured, so SLAs were assigned manually. Automatic SLA assignment was subsequently implemented and successfully tested during Phase 1 final verification (see below).

### Problem 9: SLA items had no names
- Symptom: the SLA dropdown showed only numbers (1, 3, 5, 7).
- Root cause: I created the items without a name.
- Fix: named all eight items (for example "P1 TTO 15 MIN").

### Problem 10: Escalation alarms were not running
- Symptom: the SLA task last ran 42 minutes earlier.
- Investigation: queried the scheduled tasks table. The task was in web mode.
- Fix: switched it to CLI mode, then confirmed it runs every minute.

### Problem 11: Test alarm showed no effect
- Symptom: the alarm ran but no group was added.
- Investigation: checked tickets, groups, the alarm schedule and the ticket history by query.
- Findings: the alarm was only scheduled when it existed before the SLA was attached. GLPI also auto-assigned me as technician on ticket creation.
- Status: the final confirmation uses the real P1 alarm on ticket 1 (see below).

### Known limitations
- Times are in server time (UTC), because time zone support is not enabled.
- Email reminders were not configured, because the lab has no mail server (Concept studied).
- I created a test service level while the Root entity was selected. Prevention: check the entity indicator before creating anything.

### Lesson 5 final result: escalation alarm
- Real P1 alarm on ticket 1 (no technician assigned): the schedule row was consumed at 08:05 server time and the scheduler logged "fully processed".
- No group appeared on the ticket afterwards.
- Status: alarm scheduling and execution confirmed. Visible effect of the action NOT confirmed. I do not claim it as working end to end.
- If revisited: check the ticket history and GLPI 12 documentation for how escalation actions apply.

## Lesson 6: Knowledge base (GLPI 12.0.2)
Implemented: 5 knowledge base categories and 5 how-to articles (password reset, printer, Outlook, Wi-Fi, slow computer), each with symptom, steps and escalation.

### Problem 12: Could not add a target to an article
- Symptom: the Targets tab showed "unexpected error" when adding a target.
- Investigation: checked the PHP and SQL error logs (no matching entry) and confirmed the target table stayed empty.
- Workaround: inserted the target rows directly into the database (entity = Desert Bay Trading LLC, recursive).
- Status: the UI error was NOT resolved. Targets were set through the database, so this is a lab workaround and not a recommended practice.
- Lesson: the tab is called "Targets" in GLPI 12 (I first looked for "Visibility"). An article with no target is personal and unpublished.

### Problem 13: Duplicate knowledge base article
- Symptom: two articles with the same title ("My computer is slow: checklist").
- Root cause: I clicked Add twice.
- Fix: removed the duplicate (UI delete option was not available, so it was removed through the database, including its target and revision rows).
- Prevention: check the article list after saving, and do not click Add twice.

## Lesson 7: Helpdesk ticket management

Implemented: Five GLPI helpdesk ticket workflows covering incidents, a service request, asset allocation, user permissions, ticket follow-ups and management escalation.

### Problem 14: Existing tickets were missing from the list
- Symptom: only the printer ticket appeared after multiple tickets had been created.
- Investigation: reviewed the ticket list and its search filters.
- Root cause: active search filters were hiding other tickets.
- Fix: cleared the filters and verified that all tickets appeared.
- Lesson: check search filters before assuming a record was deleted.

### Ticket workflow results
- Ticket 1: Outlook will not open — Closed.
- Ticket 2: Printer offline on Floor 2 — Closed.
- Ticket 3: Locked account — Closed.
- Ticket 4: New joiner needs a laptop and account — Pending.
- Ticket 5: Floor 2 Wi-Fi has no internet — Processing (Assigned).

### Asset and account administration
- Linked laptop DBT-LT-016 to Ticket 4.
- Assigned the laptop to Costa Danial.
- Changed asset status from In stock to In use.
- Verified Costa Danial's GLPI account was active.
- Assigned the Self-Service profile.
- Windows and Microsoft 365 account provisioning remain pending.

### Escalation exercise
- Assigned the Floor 2 Wi-Fi incident to Omar Haddad and IT Management.
- Verified both assignments.
- Recorded private escalation notes and a public update.
- Status: manual escalation routing verified; technical resolution and automatic escalation action remain unverified.

### SLA assignment
- Manually assigned SLAs to all five original tickets.

## Phase 1: Automatic SLA assignment verification

### Problem 15: SLA automation rule was created under the wrong rule type
- Symptom: the expected ticket SLA actions were unavailable.
- Investigation: checked the exact rule section in GLPI.
- Root cause: Business rules for assets was being inspected instead of Business rules for tickets.
- Fix: opened Administration > Rules > Business rules for tickets.
- Lesson: confirm the rule type before troubleshooting missing criteria or actions.

### Automatic SLA rule implementation
- Created rule: Automatic SLA Assignment - High Priority.
- Criterion: Urgency = High.
- Action 1: assign the existing SLA TTR.
- Action 2: assign the existing SLA TTO.
- Verified the criterion and both actions before activation.
- Activated the rule.

### Automation test
- Created temporary incident: TEST - Automatic SLA Assignment.
- Set Urgency = High.
- Left both SLA fields empty during ticket creation.
- Verified that GLPI automatically assigned SLA TTO and SLA TTR.
- Closed the temporary test ticket after verification.
- Result: automatic SLA assignment successfully tested for a High urgency ticket.

### Final Phase 1 limitations
- Automatic escalation alarm scheduling and execution were observed, but the intended assignment effect was not confirmed.
- Knowledge-base Targets UI error remains unresolved; database changes were used as a lab workaround.
- Some physical troubleshooting and account provisioning activities were simulated or deferred to later phases.

## Phase 1 Completion Summary

Core GLPI helpdesk and asset management exercises completed.

Verified:
- GLPI and MariaDB deployment using Docker Compose.
- User, group and asset management.
- Five helpdesk ticket workflows.
- Manual SLA assignment.
- Automatic SLA TTO and TTR assignment for a High urgency test ticket.
- Manual escalation routing.
- Knowledge-base article creation.

Evidence:
- Numbered screenshots stored in screenshots/phase1/.
- Project README and troubleshooting log maintained in GitHub.
