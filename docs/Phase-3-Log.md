# Phase 3 — Windows Desktop Support and PowerShell

## Lesson 1 — Windows Users and Groups

**Classification:** Implemented / Lab practice

### Objective

Implement local Windows employee account administration, departmental group management, authentication troubleshooting and security auditing for Desert Bay Trading LLC.

### Topics covered

- Windows local, Microsoft, domain and Entra ID accounts
- Authentication and authorization
- Standard users and administrators
- Principle of least privilege
- Security Account Manager (SAM)
- Security Identifiers (SID)
- LSASS and access tokens
- User profiles
- User Account Control (UAC)
- Local security groups
- Account creation and password management
- Account enabling and disabling
- Departmental group membership management
- Secondary Logon and RUNAS
- Windows Security event logs

### Implementation

Created three local employee accounts:

| Employee | Username | Department | Group |
|---|---|---|---|
| Sara Ahmed | dbt.sara | Finance | DBT-Finance |
| Hassan Rahman | dbt.hassan | Sales | DBT-Sales |
| Mariam Yusuf | dbt.mariam | HR | DBT-HR |

All three accounts were configured as standard users without direct membership in the Administrators group.

### Account administration

- Created three local employee accounts and three departmental groups.
- Assigned employees to their respective departmental groups.
- Verified standard user group memberships.
- Disabled and re-enabled Mariam's account.
- Reset Hassan's and Sara's passwords using secure password input.
- Simulated Hassan's departmental transfer from Sales to Finance.
- Verified the membership changes and restored the original department assignment.
- Enforced password requirements for all three employee accounts.

### Workplace incident — INC-0023

**Title:** Employee unable to authenticate to Windows

**Requester:** Sara Ahmed

**Technician:** Omar Haddad

**Priority:** Medium

**Classification:** Controlled lab simulation

#### Symptoms

The employee was unable to authenticate using the local Windows account.

#### Diagnosis

Used Get-LocalUser, net user, Get-LocalGroupMember and Win32_UserAccount to investigate the account.

Findings:

- Account disabled: True
- Account locked out: False
- Account expiration: Never
- Password not expired
- Departmental membership intact

#### Root cause

The local employee account was intentionally disabled for the incident simulation.

#### Resolution

Re-enabled the account using Enable-LocalUser and verified the enabled status.

Successful authentication was confirmed through RUNAS and Windows Security Event ID 4624.

No additional password reset was required during incident recovery.

#### Security audit evidence

| Time | Event ID | Description |
|---|---|---|
| 16:05:36 | 4724 | Sara password reset attempt |
| 16:11:33 | 4725 | Sara account disabled |
| 16:15:02 | 4722 | Sara account enabled |
| 16:17:29 | 4624 | Successful authentication |
| 16:23:06 | 4625 | Failed authentication |
| 16:23:28 | 4624 | Successful authentication after retry |

Date: 25 November 2026

A filtered PowerShell security audit report returned 15 relevant events:

- Successful logons: 2
- Failed logons: 1
- Account enabled events: 5
- Account disabled events: 2
- Password reset attempts: 5

#### Measured lab results

- Account disable to re-enable interval: 3 minutes 29 seconds.
- Account disable to first verified authentication: 5 minutes 56 seconds.
- Final failed authentication to successful retry: 22 seconds.

These are controlled lab measurements, not production SLA metrics.

#### Limitations

- Full Windows desktop sign-in was not tested.
- Successful alternate-user authentication was verified through security logs.
- A disabled-account-specific failed logon event was not captured.
- Final employee process identity output was not supplied for review.
- The exact cause of the initial RUNAS password acquisition error remains unknown.

## Troubleshooting Log

### Problem 1 — Incorrect whoami syntax

- Symptom: whoami/user was not recognized.
- Root cause: Missing space between the command and argument.
- Fix: Used whoami /user.
- Status: Resolved.

### Problem 2 — Invalid PowerShell cmdlet

- Symptom: Get-Local returned CommandNotFoundException.
- Root cause: Incomplete cmdlet name.
- Fix: Used Get-LocalUser or Get-LocalGroup as appropriate.
- Status: Resolved.

### Problem 3 — Incorrect parameter name

- Symptom: NamedParameterNotFound error.
- Root cause: Typed -Nmae instead of -Name.
- Fix: Corrected the parameter and reviewed cmdlet syntax.
- Status: Resolved.

### Problem 4 — Incorrect object property names

- Symptom: Selected properties returned blank values.
- Root cause: Misspelled Name and Description properties.
- Fix: Corrected property names and reviewed available properties using Get-Member.
- Status: Resolved.

### Problem 5 — Null password variable

- Symptom: Password parameter validation failed.
- Root cause: Referenced $NewPasswor instead of $NewPassword.
- Fix: Used the correct variable containing the SecureString password.
- Status: Resolved.

### Problem 6 — Terminal prompts copied as commands

- Symptom: Get-Process parameter error and unrecognized continuation prompt.
- Root cause: Copied PowerShell prompt text along with commands.
- Fix: Executed only the actual commands.
- Status: Resolved.

### Problem 7 — RUNAS password acquisition failure

- Symptom: RUNAS ERROR: Unable to acquire user password.
- Investigation: Retried password entry and opened an alternative terminal.
- Result: Subsequent authentication succeeded, confirmed by Event ID 4624.
- Root cause: Unconfirmed.
- Status: Authentication functionality recovered.

### Problem 8 — RUNAS error 1326

- Symptom: Username or password incorrect.
- Evidence: Security Event ID 4625.
- Probable cause: Incorrectly entered credentials.
- Fix: Retried authentication with the correct credentials.
- Verification: Event ID 4624 recorded 22 seconds later.
- Status: Resolved.

### Problem 9 — Docker commands not recognized

- Symptom: Windows Sudo disabled and Docker CommandNotFoundException.
- Root cause: Linux Docker commands executed in Windows PowerShell instead of Ubuntu WSL.
- Fix: Enterered Ubuntu WSL and used the existing Docker installation.

Status: GLPI recovery reported by user.

Screenshot evidence

27-glpi-authentication-incident.png — GLPI incident INC-0023.

Lesson status

Practical implementation: Completed.

Authentication audit: Verified.

GLPI documentation: Completed as reported.

Git commit: Pending.

Interview assessment: Pending.

## Lesson 2 — NTFS and SMB Troubleshooting

### Problem: Truncated ACL information

- Symptom: PowerShell table output truncated access control information.
- Root cause: Long identity and permission values exceeded the available display width.
- Resolution: Used Format-List instead of Format-Table.
- Status: Resolved.

### Problem: Incomplete quotation in PowerShell

- Symptom: PowerShell displayed the continuation prompt (>>).
- Root cause: An incomplete quoted path.
- Resolution: Cancelled the incomplete command and entered a correctly quoted path.
- Status: Resolved.

### Problem: Incorrect variable reference

- Symptom: icacls reported that the specified path could not be found.
- Root cause: Used Lab as a literal directory name instead of the $Lab variable.
- Resolution: Used the correct PowerShell variable reference and directory path.
- Status: Resolved.

### Problem: Incorrect Advanced Security Settings navigation

- Symptom: Opened the identity selection dialog instead of inspecting existing permissions.
- Root cause: Incorrect GUI navigation.
- Resolution: Returned to the Advanced Security Settings window and inspected inherited permissions.
- Status: Resolved.

### Problem: RUNAS authentication failure

- Symptom: RUNAS returned Error 1326 — The user name or password is incorrect.
- Affected accounts: dbt.sara, dbt.hassan and dbt.mariam.
- Observed failures: Nine failed attempts.
- Investigation: Account status, password status and Security Event ID 4625 were identified as diagnostic checks.
- Root cause: Exact underlying cause not confirmed.
- Resolution: Subsequent employee access tests were reported successful. Exact corrective action was not supplied.
- Status: Access restored according to operator confirmation.

### Simulated incident: INC-0024 — Finance shared folder access denied

- Symptom: Finance employee unable to access authorized departmental files.
- Root cause: Finance security group membership intentionally removed during controlled incident simulation.
- Resolution: Restored DBT-Finance membership and established a fresh authentication session.
- Verification: Authorized access restored while unauthorized access remained restricted.
- GLPI status: Solved, as confirmed by the lab operator.
- Classification: Controlled incident simulation.
