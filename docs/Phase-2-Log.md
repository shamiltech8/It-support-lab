
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
