# Phase 1 ticket 01: Outlook will not open
Label: Lab practice (simulated investigation, real GLPI ticket)

- Date and ticket number: ticket #1 in GLPI, created Sunday 15 Nov 2026, closed Tuesday 17 Nov 2026
- Reported by and priority: Sara Ahmed (HR), priority Very high (urgency Very high, impact High)
- Symptom (user's words): "Outlook closes immediately after I click it. I cannot read email."
- Investigation (simulated, in order):
  1. Asked the user about error messages: none, Outlook closes after about 2 seconds.
  2. Started Outlook in safe mode (outlook.exe /safe): it opened normally.
  3. Conclusion: an add-in is crashing Outlook.
  4. Disabled the PDF add-in in File > Options > Add-ins.
  5. Restarted Outlook normally: it opened and the mailbox loaded.
- Root cause: a faulty PDF add-in after an update
- Fix: disabled the add-in, then confirmed with the user
- Prevention: keep add-ins to the approved list, and link the knowledge article "Outlook will not open: first fixes"
- Asset linked: Sara's laptop (checked in GLPI)
- SLA note: P1 SLA attached by hand. Time to resolve was due Monday 12:00 (server time) but the ticket was solved Tuesday 09:47, because I reused it to test escalation alarms. This is a lab artefact, not a real result.
- Time taken and what I would do faster next time: the hands-on fix would take about 15 minutes. Next time I would use a separate ticket for alarm tests.
