
## Lesson 1 — Windows Installation Fundamentals
Status: Concept studied + Lab practice

### Verified environment
- Windows 11 Home Single Language, 64-bit, build 26200
- Firmware: UEFI
- Storage: WD PC SN740 NVMe SSD, 476.94 GB
- Partition style: GPT
- EFI System Partition: 0.25 GB
- Microsoft Reserved Partition: 0.02 GB
- Windows C: partition: 475.60 GB
- Recovery Partition: 1.07 GB
- TPM 2.0: Present, Ready, Enabled and Activated
- TPM manufacturer: Intel
- TPM lockout: False

### Implementation decision
Windows 11 VM installation was deferred because the
8 GB host laptop had insufficient available memory.
Windows installation was studied conceptually.

### Troubleshooting
Initial Get-Tpm command failed because administrator
privileges were required. Retried from elevated
PowerShell and verified TPM successfully.

### Safety
No partitions, firmware settings, or TPM keys were modified.

### Evidence
Screenshot 16: Disk Management partition layout (pending).

## Lesson 2 — BIOS/UEFI and Boot Troubleshooting
Status: Lab practice + Concept studied

### Verified results
- Firmware: UEFI
- Secure Boot: Disabled
- Windows Boot Manager: bootmgfw.efi
- Default boot entry: {current}
- Boot menu timeout: 30 seconds
- Windows OS Loader: winload.efi
- Windows recovery: Enabled
- Windows RE location: Disk 0, Partition 4
- NVMe SSD: Online and Healthy
- Disk partition style: GPT

### Troubleshooting findings
- No active boot failure observed.
- Secure Boot is disabled and was not changed.
- Windows Boot Manager and recovery configuration were inspected.
- Common boot failure scenarios were studied.

### Safety
No firmware, BCD, partition, or recovery settings were modified.

### Evidence
- Screenshot 17: 17-boot-configuration.png
  - Secure Boot status: Disabled (False)
  - Windows Boot Manager configuration
  - Windows Recovery Environment: Enabled
  - All three outputs captured in one screenshot
 
## Lesson 3 — Windows Device Drivers

Status: Lab practice

### Objective
Inspect Windows device drivers, identify device errors,
and understand safe driver troubleshooting.

### Practical Work
- Inspected devices using Get-PnpDevice.
- Verified currently present devices report no non-OK status.
- Identified Intel Wi-Fi and Realtek Ethernet adapters.
- Inspected signed driver information using PowerShell.
- Listed driver packages using pnputil.
- Reviewed safe driver installation and rollback concepts.

### Verified Wi-Fi Driver
Device: Intel Wi-Fi 6E AX211 160MHz
Provider: Intel
Version: 22.170.0.3
Date: 29 August 2022
Status: OK

### Findings
No currently present devices reported a non-OK status.
No driver changes were performed.
The Wi-Fi troubleshooting incident is simulated.

### Evidence
Screenshot 18: 18-device-drivers.png

### Pending
- Complete simulated Wi-Fi troubleshooting incident.
- Complete technical interview assessment.


## Lesson 4 — Hardware Diagnostics

Status: Lab practice

### Objective
Inspect CPU, RAM, SSD health, resource utilization,
and Windows storage-related errors.

### Hardware Inventory
- CPU: Intel Core i5-1240P
- Physical cores: 12
- Logical processors: 16
- Installed RAM: 8 GiB Micron, 3200 MT/s reported
- Storage: WD PC SN740 NVMe SSD
- Storage health: Healthy / OK

### Resource Diagnostics
- CPU load: 7% during measurement
- Available RAM: approximately 1.18 GiB
- Memory Compression working set: 809.2 MB
- Chrome and Edge WebView2 were among the
  highest memory-consuming processes.
- Page-file allocation: 11264 MB
- Current page-file usage: 135 MB
- Recorded peak page-file usage: 2228 MB
- C: free space: approximately 216.4 GiB
- C: filesystem: NTFS
- C: volume health: Healthy

### Windows Event Log
No matching storage-related error events were returned
by the seven-day System log query.

### Findings
- No confirmed hardware failure was identified.
- CPU load was low during the measurement.
- Available RAM was relatively limited.
- Memory pressure should be investigated if
  users report slow performance.
- No hardware or system configuration changes
  were performed.

### Evidence
Screenshot 19: 19-hardware-diagnostics.png

### Pending
- Simulated hardware troubleshooting incident.
- Technical interview assessment.


## Lesson 5 — Windows Backup and Recovery

Status: Lab practice

### Objective
Learn file backup, recovery, integrity verification,
and Windows Recovery Environment fundamentals.

### Backup Fundamentals
- Full backup
- Incremental backup
- Differential backup
- 3-2-1 backup rule
- Backup versus recovery

### Practical Implementation
- Created a fictional finance report.
- Created Original, Backup, and Restored folders.
- Backed up Expense-Report.txt using PowerShell.
- Verified original and backup SHA-256 hashes matched.
- Simulated accidental deletion of the original file.
- Restored the file into a separate recovery folder.
- Verified backup and restored SHA-256 hashes matched.
- Confirmed the recovered report contents.

### Windows Recovery Environment
Windows edition: Windows 11 Home Single Language
Windows version: 10.0.26200
WinRE status: Enabled
WinRE location: Disk 0, Partition 4

### Partition Inspection
Partition 1: System / EFI — 260 MiB
Partition 2: Microsoft Reserved — 16 MiB
Partition 3: Windows C: — approximately 475.6 GiB
Partition 4: Recovery — approximately 1.07 GiB

### Findings
- Test backup and restoration were successful.
- Restored file integrity was verified using SHA-256.
- Windows Recovery Environment is enabled.
- No Windows reset or partition changes were performed.
- Backup and restore were tested on the same laptop,
  not on independent backup storage.
- WinRE configuration was inspected, but recovery
  operations were not tested.

### Evidence
Screenshot 20: 20-backup-recovery.png

### Pending
- Simulated workplace recovery incident.
- Technical interview assessment.

## Lesson 6 — Hardware Troubleshooting

**Status:** Lab practice — diagnostics completed

### Objective
Learn how to investigate hardware-related complaints using Windows diagnostic tools and distinguish software errors from possible hardware failures.

### Topics Covered
- Hardware troubleshooting methodology
- Common CPU, RAM, SSD, overheating, and power problems
- Battery health diagnostics
- Windows Reliability Monitor
- Windows Event Viewer
- Application Error events
- .NET Runtime exceptions
- WHEA hardware error reporting
- Unexpected shutdown events
- Windows system file integrity verification

### Practical Implementation
1. Inspected battery information using PowerShell.
2. Generated and reviewed a Windows battery report.
3. Calculated battery capacity retention.
4. Inspected available Windows power plans.
5. Investigated critical events in Reliability Monitor.
6. Identified recurring Acer AWC application crashes.
7. Examined Application Error Event ID 1000 and .NET Runtime Event ID 1026.
8. Checked recent WHEA hardware events.
9. Checked unexpected shutdown Event IDs 41 and 6008.
10. Verified protected Windows system files using `sfc /verifyonly`.

### Verified Results
- Laptop: Acer Aspire A715-51G
- Battery: AP18C8K
- Design capacity: 48,004 mWh
- Full charge capacity: 43,301 mWh
- Estimated capacity retention: 90.2%
- Active power plan: Acer
- AWC executable version: 2.5.22250.0
- Exception: System.NullReferenceException
- WHEA events: No matching events found in seven days
- Unexpected shutdown events: No matching events found in seven days
- SFC: No integrity violations detected

### Simulated Workplace Incident — INC-0021

**Company:** Desert Bay Trading LLC

**Scenario:** An employee reports recurring critical errors on an Acer laptop.

**Investigation:** Windows Reliability Monitor and Event Viewer identified repeated AWC application crashes.

**Preliminary Diagnosis:** Recurring application failure. No physical hardware fault was confirmed.

**Resolution Status:** Investigation completed; software repair not performed or verified.

**Recommended Next Action:** Identify the relevant Acer software and evaluate an official repair or update option before making changes.

### Evidence
- Screenshot 21: Hardware troubleshooting diagnostics — pending

### Pending
- Save Screenshot 21
- Git commit and push
- Technical interview assessment
