
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
