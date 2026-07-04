# 📁 Shared Folders and Permissions

This document describes Phase 6 of the LittleBuilds AD Lab: creating shared folders on the domain controller and configuring access using Active Directory security groups.

## Overview

In this phase, shared folders were created for the LittleBuilds Active Directory lab. The folders were shared from the server and secured using a combination of share permissions, NTFS permissions, and Active Directory security groups.

The goal of this phase was to practice the manual Windows Server process first before using PowerShell or automation.

## Domain Details

| Item | Details |
|---|---|
| Domain | `littlebuilds.local` |
| NetBIOS Name | `LITTLEBUILDS` |
| Domain Controller | `LB-SRV-DC01` |
| Server VM | `LittleBuilds-Server01` |
| Server OS | Windows Server 2022 Standard Evaluation |
| Internal Lab Network | `LittleBuildsLabNet` |
| Server IP Address | `10.10.10.10` |
| Preferred DNS | `10.10.10.10` |

## Shared Folder Plan

The shared folders were created under a main folder on the C: drive:

```text
C:\Shares
```

Three shared folders were created:

| Folder Purpose | Local Folder Path | Share Name | UNC Path |
|---|---|---|---|
| Public shared folder | `C:\Shares\Public` | `Public` | `\\LB-SRV-DC01\Public` |
| Finance shared folder | `C:\Shares\Finance` | `Finance` | `\\LB-SRV-DC01\Finance` |
| HR shared folder | `C:\Shares\HR` | `HR` | `\\LB-SRV-DC01\HR` |

## Folder Structure

Final folder structure:

```text
C:\
└── Shares
    ├── Public
    ├── Finance
    └── HR
```

## Security Groups Used

The following security groups were created earlier in Phase 5 and used for shared folder permissions in Phase 6:

| Security Group | Purpose |
|---|---|
| `GG_Shared_Public_Read` | Grants read access to the Public shared folder |
| `GG_Shared_Finance_RW` | Grants modify/read-write access to the Finance shared folder |
| `GG_Shared_HR_RW` | Grants modify/read-write access to the HR shared folder |

These groups are stored in:

```text
LittleBuilds
└── Groups
    └── Security-Groups
```

## Share Permissions

The share permissions were configured broadly using:

```text
Authenticated Users → Full Control
```

This was done for each share:

| Share | Share Permission |
|---|---|
| Public | `Authenticated Users` → Full Control |
| Finance | `Authenticated Users` → Full Control |
| HR | `Authenticated Users` → Full Control |

## Why Share Permissions Were Set Broadly

For this lab, share permissions were kept simple and broad so that access would mainly be controlled using NTFS permissions.

This keeps the permission model easier to understand:

```text
Share permissions = network doorway
NTFS permissions = actual folder access
```

The real access control is handled by the NTFS permissions on the Security tab.

## NTFS Permissions

NTFS permissions were configured directly on each folder.

Inheritance was disabled on each shared folder. Existing inherited permissions were converted into explicit permissions, then the generic `Users (LITTLEBUILDS\Users)` entries were removed.

The following default system/admin entries were kept:

- `SYSTEM`
- `Administrators`
- `CREATOR OWNER`

Then the correct Active Directory security group was added to each folder.

| Folder | NTFS Security Group | NTFS Permission |
|---|---|---|
| `C:\Shares\Public` | `GG_Shared_Public_Read` | Read & Execute |
| `C:\Shares\Finance` | `GG_Shared_Finance_RW` | Modify |
| `C:\Shares\HR` | `GG_Shared_HR_RW` | Modify |

## Group Membership / Access Plan

Users were added to the shared-folder access groups.

### Public Access Group

Security group:

```text
GG_Shared_Public_Read
```

Members:

| User | Display Name |
|---|---|
| `janine.admin` | Janine Admin |
| `ted.it` | Ted LittleBuilds |
| `ozzy.security` | Ozzy Security |
| `monty.operations` | Monty Operations |
| `chewy.hr` | Chewy HR |
| `penny.executive` | Penny Executive |
| `daisy.sales` | Daisy Sales |
| `porkchop.risk` | PorkChop Risk |

Purpose:

```text
Allows selected users and branch leads to read the Public shared folder.
```

### Finance Access Group

Security group:

```text
GG_Shared_Finance_RW
```

Members:

| User | Display Name |
|---|---|
| `janine.admin` | Janine Admin |
| `penny.executive` | Penny Executive |

Purpose:

```text
Allows Head Office / Executive users to modify files in the Finance shared folder.
```

### HR Access Group

Security group:

```text
GG_Shared_HR_RW
```

Members:

| User | Display Name |
|---|---|
| `janine.admin` | Janine Admin |
| `chewy.hr` | Chewy HR |

Purpose:

```text
Allows Head Office / HR users to modify files in the HR shared folder.
```

## Final Permission Summary

| Shared Folder | Share Permission | NTFS Permission | Intended Access |
|---|---|---|---|
| Public | `Authenticated Users` → Full Control | `GG_Shared_Public_Read` → Read & Execute | General read-only access for selected lab users |
| Finance | `Authenticated Users` → Full Control | `GG_Shared_Finance_RW` → Modify | Restricted access for Janine Admin and Penny Executive |
| HR | `Authenticated Users` → Full Control | `GG_Shared_HR_RW` → Modify | Restricted access for Janine Admin and Chewy HR |

## Share Verification

The shares were verified in Computer Management:

```text
Computer Management
└── System Tools
    └── Shared Folders
        └── Shares
```

The following shares were visible:

- `Public`
- `Finance`
- `HR`

The server also displayed normal domain controller/admin shares:

- `ADMIN$`
- `C$`
- `IPC$`
- `NETLOGON`
- `SYSVOL`

These default shares are expected on a Windows Server domain controller.

## UNC Path Verification

The shared folders were also verified using the UNC path:

```text
\\LB-SRV-DC01
```

The following shares were visible:

- `Public`
- `Finance`
- `HR`
- `NETLOGON`
- `SYSVOL`

This confirmed that the server was publishing the shares successfully over the network path.

## Testing Notes

Full user access testing was not completed in this phase because the Windows 11 client VM has not been domain-joined yet.

Since the work was performed while logged into the domain controller as an administrator, this phase confirms that:

- The folders exist
- The folders are shared
- The share names are available
- The NTFS permissions are configured
- The correct security groups were assigned
- The groups have the correct members

Proper user testing will happen later after the Windows 11 client VM is joined to the domain.

Planned future testing examples:

| Test User | Expected Result |
|---|---|
| `daisy.sales` opens `\\LB-SRV-DC01\Public` | Should be allowed |
| `daisy.sales` opens `\\LB-SRV-DC01\Finance` | Should be denied |
| `chewy.hr` opens `\\LB-SRV-DC01\HR` | Should be allowed |
| `penny.executive` opens `\\LB-SRV-DC01\Finance` | Should be allowed |
| `penny.executive` opens `\\LB-SRV-DC01\HR` | Should be denied unless added later |
| `ted.it` opens `\\LB-SRV-DC01\Public` | Should be allowed |
| `ted.it` opens `\\LB-SRV-DC01\Finance` | Should be denied |

## Screenshots

Screenshots for this phase include:

| Screenshot | Description |
|---|---|
| `16 - Shares Folder Created.png` | Shows the main `C:\Shares` folder created |
| `17 - Public Folder NTFS Permissions.png` | Shows Public folder NTFS permissions |
| `18 - Finance Folder NTFS Permissions.png` | Shows Finance folder NTFS permissions |
| `19 - HR Folder NTFS Permissions.png` | Shows HR folder NTFS permissions |
| `20 - Public Shared Folder Group Members.png` | Shows members of `GG_Shared_Public_Read` |
| `21 - Finance Shared Folder Group Members.png` | Shows members of `GG_Shared_Finance_RW` |
| `22 - HR Shared Folder Group Members.png` | Shows members of `GG_Shared_HR_RW` |
| `23 - Shared Folders Listed in Computer Management.png` | Shows the shares listed in Computer Management |
| `24 - UNC Share Path Verification.png` | Shows the shares visible through `\\LB-SRV-DC01` |
| `25 - Shared Folders Snapshot Created.png` | Shows the VirtualBox snapshot after Phase 6 |

## Screenshot Links

> Screenshot files are stored in the `screenshots/` folder.

- [16 - Shares Folder Created](../screenshots/16%20-%20Shares%20Folder%20Created.png)
- [17 - Public Folder NTFS Permissions](../screenshots/17%20-%20Public%20Folder%20NTFS%20Permissions.png)
- [18 - Finance Folder NTFS Permissions](../screenshots/18%20-%20Finance%20Folder%20NTFS%20Permissions.png)
- [19 - HR Folder NTFS Permissions](../screenshots/19%20-%20HR%20Folder%20NTFS%20Permissions.png)
- [20 - Public Shared Folder Group Members](../screenshots/20%20-%20Public%20Shared%20Folder%20Group%20Members.png)
- [21 - Finance Shared Folder Group Members](../screenshots/21%20-%20Finance%20Shared%20Folder%20Group%20Members.png)
- [22 - HR Shared Folder Group Members](../screenshots/22%20-%20HR%20Shared%20Folder%20Group%20Members.png)
- [23 - Shared Folders Listed in Computer Management](../screenshots/23%20-%20Shared%20Folders%20Listed%20in%20Computer%20Management.png)
- [24 - UNC Share Path Verification](../screenshots/24%20-%20UNC%20Share%20Path%20Verification.png)
- [25 - Shared Folders Snapshot Created](../screenshots/25%20-%20Shared%20Folders%20Snapshot%20Created.png)

## VirtualBox Snapshot

After completing the shared folder and permissions configuration, the VM was shut down normally and a new VirtualBox snapshot was created.

Snapshot name:

```text
05 - Shared Folders and Permissions Created
```

Snapshot description:

```text
Created shared folders for the LittleBuilds Active Directory lab. Configured Public, Finance, and HR shares using security groups for access control. Snapshot created before Group Policy configuration or Windows client domain join.
```

## Notes / Lessons Learned

- Shared folders can be created manually through File Explorer.
- Share permissions and NTFS permissions are separate permission systems.
- Share permissions control access through the network share.
- NTFS permissions control access to the actual folder and files.
- When both share permissions and NTFS permissions apply, the most restrictive permission wins.
- Keeping share permissions broad and NTFS permissions specific can make permissions easier to manage in a beginner lab.
- Security groups are better than assigning permissions directly to individual users.
- Users can be added or removed from groups without changing the folder permissions directly.
- Disabling inheritance allows folder permissions to be controlled more intentionally.
- The default `Users` permissions were removed so access could be controlled through dedicated shared-folder groups.
- A Windows client VM will be needed later to properly test user access.
- Hosting shared folders on the domain controller is acceptable for early lab practice, but a dedicated file server is more realistic for a production-style environment.
- VirtualBox snapshots are useful after major configuration milestones.

## Phase Status

Phase 6 is complete.

Completed tasks:

- Created `C:\Shares`
- Created `Public`, `Finance`, and `HR` folders
- Shared each folder
- Configured share permissions
- Disabled inheritance on each folder
- Configured NTFS permissions using security groups
- Added users to shared-folder access groups
- Verified shares in Computer Management
- Verified shares using the UNC path `\\LB-SRV-DC01`
- Shut down the VM normally
- Created the Phase 6 VirtualBox snapshot

Next step:

```text
Phase 7 - Group Policy testing
```
