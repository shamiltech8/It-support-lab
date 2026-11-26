# Phase 3 — Lesson 2: NTFS Permissions and SMB File Sharing

## Project

Small Business IT Support & Cloud Operations Lab

Company: Desert Bay Trading LLC (simulated)

Classification: Implemented / Lab practice

## 1. Objective

Implement secure departmental file storage, group-based NTFS permissions, SMB network sharing, access verification and permission incident troubleshooting.

## 2. Environment

- Windows 11
- Windows PowerShell 5.1
- NTFS file system
- Local Windows security groups
- SMB file sharing
- GLPI helpdesk
- Ubuntu WSL
- Git and GitHub

## 3. Topics covered

- File systems and NTFS fundamentals
- NTFS permission levels
- Access Control Lists and Access Control Entries
- DACL and SACL
- Permission inheritance
- Explicit and inherited permissions
- File ownership
- Security identifiers
- Windows access tokens
- Effective permissions
- Group-based access control
- Principle of least privilege
- SMB protocols and TCP port 445
- UNC paths
- Share permissions
- Access-Based Enumeration
- Network drive mapping
- SMB session monitoring
- Permission troubleshooting
- Windows Security audit events
- GLPI incident management

## 4. Departmental implementation

Company directory: C:\DBT-CompanyData

| Department | Security group | Employee |
|---|---|---|
| Finance | DBT-Finance | dbt.sara |
| Sales | DBT-Sales | dbt.hassan |
| HR | DBT-HR | dbt.mariam |

## 5. NTFS permission configuration

| Group | Finance | Sales | HR | Public |
|---|---|---|---|---|
| DBT-Finance | Modify | No grant | No grant | Read & Execute |
| DBT-Sales | No grant | Modify | No grant | Read & Execute |
| DBT-HR | No grant | No grant | Modify | Read & Execute |
| Administrators | Full Control | Full Control | Full Control | Full Control |
| SYSTEM | Full Control | Full Control | Full Control | Full Control |

Unnecessary inherited permissions were removed from the company root directory. Administrator and SYSTEM permissions were preserved.

Recursive ACL inspection successfully processed nine initial file-system objects with zero processing failures.

All 15 grouped employee access verification items were confirmed by the lab operator.

## 6. SMB implementation

Network share: \\RASLA\DBT-CompanyData

- Administrators: Full share access
- Departmental groups: Change share access
- Access-Based Enumeration
- Departmental NTFS restrictions preserved
- UNC path access testing
- Network drive mapping and disconnection
- SMB session and connection inspection

All 13 SMB practical checklist items were confirmed by the lab operator.

SMB testing was performed within the same Windows host. Separate physical client connectivity was not tested.

## 7. Workplace incident — INC-0024

Title: Finance shared folder access denied

Requester: Sara Ahmed

Technician: Omar Haddad

### Incident simulation

Temporarily removed the Finance employee from the DBT-Finance security group.

### Investigation

- Checked network connectivity and SMB services.
- Verified employee account status.
- Investigated departmental group membership.
- Inspected SMB share permissions.
- Inspected NTFS permissions.
- Reviewed Security event logs.

### Root cause

Missing DBT-Finance security group membership.

### Resolution

Restored the employee's authorized group membership and established a fresh authentication session to obtain an updated access token.

### Verification

- Authorized Finance access restored.
- Unauthorized departmental access remained restricted.
- Public folder remained read-only.
- Existing SMB and NTFS permissions preserved.
- GLPI incident reported as Solved.

All 15 incident practical checklist items were confirmed by the lab operator.

## 8. Security considerations

- Avoid unnecessary Full Control permissions.
- Assign permissions through security groups.
- Preserve administrator and SYSTEM access.
- Do not enable legacy SMB1 for routine troubleshooting.
- Do not expose SMB directly to the public internet.
- Verify both authorized and unauthorized access after changes.

## 9. Evidence limitations

Initial NTFS configuration was reviewed using terminal output.

Employee access tests, SMB implementation and incident resolution were confirmed through practical checklists.

Detailed SMB outputs, exact audit event timestamps and GLPI ticket evidence require separate inspection.

## 10. Result

Implemented secure departmental file access, practised SMB administration and completed a controlled workplace permission troubleshooting incident.
