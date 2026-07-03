# Users and Groups

## Overview

This phase documents the manual creation of user accounts, service accounts, security groups, and group memberships for the LittleBuilds Active Directory lab.

The goal of this phase was to practice creating Active Directory users and groups manually in Active Directory Users and Computers before moving on to bulk user creation with PowerShell in a later phase.

This phase also introduces a basic business-style structure where Janine Admin represents Head Office, and each LittleBuilds dog account represents a branch lead for a different branch.

## Domain Details

| Item | Value |
|---|---|
| Domain name | `littlebuilds.local` |
| NetBIOS domain name | `LITTLEBUILDS` |
| Domain controller | `LB-SRV-DC01` |
| Server VM | `LittleBuilds-Server01` |
| Server IP address | `10.10.10.10` |
| DNS server | `10.10.10.10` |

## User Account Plan

User accounts were created inside the existing `LittleBuilds` OU structure.

Users were separated into different OUs based on account type:

| Account type | OU |
|---|---|
| Admin users | `LittleBuilds/Users/Admin-Users` |
| Standard users | `LittleBuilds/Users/Standard-Users` |
| Service accounts | `LittleBuilds/Users/Service-Accounts` |

## Admin Users

The following admin user was created:

| Username | Full name | Purpose | OU |
|---|---|---|---|
| `janine.admin` | Janine Admin | Head Office / Lab Administrator | `LittleBuilds/Users/Admin-Users` |

This account represents the main Head Office administrator account for the LittleBuilds lab.

## Standard Users

The following standard users were created:

| Username | Full name | Role | OU |
|---|---|---|---|
| `ted.it` | Ted LittleBuilds | IT Manager / Barkdesk Operations | `LittleBuilds/Users/Standard-Users` |
| `ozzy.security` | Ozzy Security | Security Operations | `LittleBuilds/Users/Standard-Users` |
| `monty.operations` | Monty Operations | Operations Manager | `LittleBuilds/Users/Standard-Users` |
| `chewy.hr` | Chewy HR | HR Assistant | `LittleBuilds/Users/Standard-Users` |
| `penny.executive` | Penny Executive | Executive Office | `LittleBuilds/Users/Standard-Users` |
| `daisy.sales` | Daisy Sales | Sales Representative | `LittleBuilds/Users/Standard-Users` |
| `porkchop.risk` | PorkChop Risk | Risk Management | `LittleBuilds/Users/Standard-Users` |

Each standard user represents a LittleBuilds branch lead.

## Service Accounts

The following service account was created:

| Username | Full name | Purpose | OU |
|---|---|---|---|
| `svc.backup` | Backup Service Account | Lab backup/service account practice | `LittleBuilds/Users/Service-Accounts` |

The service account was created separately from normal user accounts to practice separating human users from system or service-based accounts.

## Security Groups

Security groups were created in `LittleBuilds/Groups/Security-Groups`.

The following security groups were created:

| Group name | Purpose |
|---|---|
| `GG_Admin_Staff` | Admin staff group |
| `GG_IT_Staff` | IT staff group |
| `GG_Finance_Staff` | Finance staff group |
| `GG_HR_Staff` | HR staff group |
| `GG_Operations_Staff` | Operations staff group |
| `GG_Sales_Staff` | Sales staff group |
| `GG_Branch_Managers` | Branch manager group |
| `GG_Shared_Finance_RW` | Future read/write access group for Finance shared folder |
| `GG_Shared_HR_RW` | Future read/write access group for HR shared folder |
| `GG_Shared_Public_Read` | Future read-only access group for Public shared folder |

## Group Naming Style

The group names use a simple naming style:

| Part | Meaning |
|---|---|
| `GG` | Global Group |
| Department name | Identifies the department or role |
| `Shared` | Identifies a future shared folder access group |
| `RW` | Read/Write access |
| `Read` | Read-only access |

For example, `GG_Shared_Finance_RW` means Global Group for Finance shared folder Read/Write access.

## Group Membership Plan

Users were added to groups based on their department and branch responsibilities.

| User | Group membership |
|---|---|
| `janine.admin` | `GG_Admin_Staff` |
| `ted.it` | `GG_IT_Staff`, `GG_Branch_Managers` |
| `ozzy.security` | `GG_Operations_Staff`, `GG_Branch_Managers` |
| `monty.operations` | `GG_Operations_Staff`, `GG_Branch_Managers` |
| `chewy.hr` | `GG_HR_Staff`, `GG_Branch_Managers` |
| `penny.executive` | `GG_Admin_Staff`, `GG_Branch_Managers` |
| `daisy.sales` | `GG_Sales_Staff`, `GG_Branch_Managers` |
| `porkchop.risk` | `GG_Operations_Staff`, `GG_Branch_Managers` |
| `svc.backup` | No normal staff group membership assigned |

The `GG_Branch_Managers` group was added to each standard dog account because each dog represents a LittleBuilds branch lead.

## Account and Password Configuration Notes

For this lab, user accounts were created with simple lab-safe settings.

| Setting | Lab configuration |
|---|---|
| User must change password at next logon | Unchecked |
| Password never expires | Checked |
| Account disabled | Unchecked |
| Shared lab password | Used for easier testing |

These settings were chosen to make the lab easier to test while learning Active Directory.

In a real production environment, password and account settings would be stricter. Users would normally receive unique temporary passwords, be required to change their password at first logon, and follow company password and security policies.

Service accounts would also require careful control, limited permissions, and monitoring.

## Screenshots

### Admin User Created

![Admin User Created](../screenshots/11%20-%20Admin%20User%20Created.png)

### Standard Users Created

![Standard Users Created](../screenshots/12%20-%20Standard%20Users%20Created.png)

### Security Groups Created

![Security Groups Created](../screenshots/13%20-%20Security%20Groups%20Created.png)

### User Group Membership Example

![User Group Membership Example](../screenshots/14%20-%20User%20Group%20Membership%20Example.png)

### Users and Groups Snapshot Created

![Users and Groups Snapshot Created](../screenshots/15%20-%20Users%20and%20Groups%20Snapshot%20Created.png)

## VirtualBox Snapshot

After creating users, groups, and group memberships, the VM was shut down normally and a VirtualBox snapshot was created.

| Item | Value |
|---|---|
| Snapshot name | `04 - Users and Groups Created` |
| Snapshot purpose | Restore point after user and group creation |

Snapshot description:

Created sample LittleBuilds users, admin users, service accounts, and security groups. Added users to department and access groups. Snapshot created before configuring shared folders, permissions, Group Policy Objects, or client domain join.

## Notes / Lessons Learned

- Active Directory users should be organized into appropriate OUs.
- Admin users, standard users, and service accounts should be separated.
- Security groups make permissions easier to manage.
- Users should be added to groups based on job role or access needs.
- Shared-folder permission groups can be created before the folders exist.
- Manual user and group creation is useful to understand before using PowerShell automation.
- VirtualBox snapshots are useful restore points before starting a new lab phase.

## Phase 5 Status

Phase 5 is complete.

Next step: `Phase 6 - Shared folders and permissions`
