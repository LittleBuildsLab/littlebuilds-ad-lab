# Phase 9 - Branch Structure Expansion

## Overview

This phase expands the LittleBuilds Active Directory branch structure from a simple dog-themed branch layout into a more realistic multi-branch company structure.

The goal of this phase was to make the Active Directory environment look more professional and scalable while keeping the LittleBuilds dog-themed company concept in the documentation.

Phase 9 focused on:

- Renaming the original branch OUs into professional location-based branch OUs
- Creating standard sub-OUs under each branch
- Creating branch-specific manager security groups
- Assigning branch managers to their branch manager groups
- Nesting branch manager groups into the main `GG_Branch_Managers` group
- Verifying the structure with PowerShell
- Taking a VirtualBox snapshot after the branch expansion work

---

## Starting Point

Before Phase 9, the `Branches` OU contained simple dog-themed branch OUs:

```text
LittleBuilds
└── Branches
    ├── Ozzy-Branch
    ├── Monty-Branch
    ├── Chewy-Branch
    ├── Penny-Branch
    ├── Daisy-Branch
    ├── PorkChop-Branch
    └── Ted-Branch
```

A VirtualBox snapshot was taken before beginning the branch expansion work.

Snapshot:

```text
08 - Phase 9 Branch Expansion Starting Point
```

![Server Phase 9 Starting Snapshot Created](../screenshots/69%20-%20Server%20Phase%209%20Starting%20Snapshot%20Created.png)

The original branch OU structure was also captured before making changes.

![ADUC Original Branch OUs Before Expansion](../screenshots/70%20-%20ADUC%20Original%20Branch%20OUs%20Before%20Expansion.png)

---

## Branch OU Renaming

The original dog-themed branch OUs were renamed into professional location-based branch OUs.

| Original OU | New Branch OU | Purpose |
|---|---|---|
| `Ted-Branch` | `Winnipeg-HQ` | Head Office / Main Operations |
| `Ozzy-Branch` | `Reykjavik-DR` | Disaster Recovery / Business Continuity |
| `Monty-Branch` | `Tokyo` | Regional Operations |
| `Penny-Branch` | `London` | Regional Administration / Compliance |
| `Daisy-Branch` | `Sydney` | Field Operations |
| `Chewy-Branch` | `Paris` | Client Relations / Design |
| `PorkChop-Branch` | `New-York` | Security / Infrastructure |

After renaming, the `Branches` OU contained the following professional branch OUs:

```text
LittleBuilds
└── Branches
    ├── Winnipeg-HQ
    ├── Reykjavik-DR
    ├── Tokyo
    ├── London
    ├── Sydney
    ├── Paris
    └── New-York
```

![ADUC Professional Branch OUs Created](../screenshots/71%20-%20ADUC%20Professional%20Branch%20OUs%20Created.png)

---

## Branch Sub-OU Structure

Each branch OU was expanded with the same standard sub-OU structure:

```text
Users
Computers
Groups
Resources
```

This creates a cleaner and more scalable Active Directory layout. Each branch can now have its own users, computers, groups, and resources.

Example branch structure:

```text
Branches
└── Winnipeg-HQ
    ├── Users
    ├── Computers
    ├── Groups
    └── Resources
```

The same structure was created under all seven branch OUs:

```text
Branches
├── Winnipeg-HQ
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
├── Reykjavik-DR
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
├── Tokyo
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
├── London
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
├── Sydney
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
├── Paris
│   ├── Users
│   ├── Computers
│   ├── Groups
│   └── Resources
└── New-York
    ├── Users
    ├── Computers
    ├── Groups
    └── Resources
```

Verification screenshot:

![ADUC All Branch Sub-OUs Verified](../screenshots/79%20-%20ADUC%20All%20Branch%20Sub-OUs%20Verified.png)

---

## Branch Manager Security Groups

A branch-specific manager security group was created under each branch's `Groups` OU.

| Branch | Branch Manager Group | Assigned Manager |
|---|---|---|
| `Winnipeg-HQ` | `GG_BR_WPG_MGRS` | `ted.it` |
| `Reykjavik-DR` | `GG_BR_RVK_MGRS` | `ozzy.security` |
| `Tokyo` | `GG_BR_TYO_MGRS` | `monty.operations` |
| `London` | `GG_BR_LON_MGRS` | `penny.executive` |
| `Sydney` | `GG_BR_SYD_MGRS` | `daisy.sales` |
| `Paris` | `GG_BR_PAR_MGRS` | `chewy.hr` |
| `New-York` | `GG_BR_NYC_MGRS` | `porkchop.risk` |

The naming format used was:

```text
GG_BR_<LOCATION>_MGRS
```

Example:

```text
GG_BR_WPG_MGRS
```

This means:

```text
Global Group - Branch - Winnipeg - Managers
```

---

## Branch Manager Group Verification

PowerShell was used to verify that all branch manager groups were created successfully.

Command used:

```powershell
Get-ADGroup -Filter 'Name -like "GG_BR_*_MGRS"' |
Select-Object Name, GroupScope, GroupCategory, DistinguishedName
```

Screenshot:

![PowerShell Branch Manager Groups Verified](../screenshots/87%20-%20PowerShell%20Branch%20Manager%20Groups%20Verified.png)

---

## Branch Manager Memberships

Each branch manager user was added to their matching branch-specific manager group.

PowerShell was used to verify the membership assignments.

Command used:

```powershell
Get-ADGroup -Filter 'Name -like "GG_BR_*_MGRS"' |
Sort-Object Name |
ForEach-Object {
    $groupName = $_.Name
    Get-ADGroupMember $groupName |
    Select-Object @{Name="BranchGroup";Expression={$groupName}}, Name, SamAccountName
}
```

Screenshot:

![PowerShell Branch Manager Memberships Verified](../screenshots/95%20-%20PowerShell%20Branch%20Manager%20Memberships%20Verified.png)

---

## Group Nesting

The branch-specific manager groups were nested into the main company-wide branch manager group:

```text
GG_Branch_Managers
```

This creates a cleaner and more realistic Active Directory group structure.

Instead of adding all users directly to `GG_Branch_Managers`, the design now uses nested groups:

```text
Branch Manager User
└── Branch-Specific Manager Group
    └── GG_Branch_Managers
```

Example:

```text
ted.it
└── GG_BR_WPG_MGRS
    └── GG_Branch_Managers
```

The following groups were added as members of `GG_Branch_Managers`:

```text
GG_BR_WPG_MGRS
GG_BR_RVK_MGRS
GG_BR_TYO_MGRS
GG_BR_LON_MGRS
GG_BR_SYD_MGRS
GG_BR_PAR_MGRS
GG_BR_NYC_MGRS
```

Screenshot:

![ADUC Branch Manager Groups Nested Into GG_Branch_Managers](../screenshots/96%20-%20ADUC%20Branch%20Manager%20Groups%20Nested%20Into%20GG_Branch_Managers.png)

---

## Group Nesting Verification

PowerShell was used to verify that `GG_Branch_Managers` contains only the nested branch manager groups.

Command used:

```powershell
Get-ADGroupMember GG_Branch_Managers |
Sort-Object Name |
Select-Object Name, SamAccountName, objectClass
```

Screenshot:

![PowerShell Branch Manager Group Nesting Verified](../screenshots/97%20-%20PowerShell%20Branch%20Manager%20Group%20Nesting%20Verified.png)

The output confirmed that the members of `GG_Branch_Managers` are groups, not direct user accounts.

---

## Recursive Membership Verification

PowerShell was also used to confirm that the branch manager users are effective members of `GG_Branch_Managers` through nested group membership.

Command used:

```powershell
Get-ADGroupMember GG_Branch_Managers -Recursive |
Sort-Object SamAccountName |
Select-Object Name, SamAccountName, objectClass
```

Screenshot:

![PowerShell Recursive Branch Manager Membership Verified](../screenshots/98%20-%20PowerShell%20Recursive%20Branch%20Manager%20Membership%20Verified.png)

The recursive membership check confirmed the following effective users:

```text
chewy.hr
daisy.sales
monty.operations
ozzy.security
penny.executive
porkchop.risk
ted.it
```

---

## Troubleshooting Note

During verification, `GG_Branch_Managers` was found to contain both nested branch manager groups and direct user memberships from earlier lab work.

To improve the Active Directory design, the direct user memberships were removed from `GG_Branch_Managers`.

After cleanup, `GG_Branch_Managers` contained only the seven branch-specific manager groups.

This created a cleaner nested group structure and avoided duplicate or redundant access paths.

---

## Final Snapshot

After the branch expansion and manager group configuration was completed, a new VirtualBox snapshot was taken.

Snapshot:

```text
09 - Phase 9 Branch Structure and Manager Groups Created
```

Snapshot description:

```text
Snapshot taken after Phase 9 branch structure expansion.
Professional branch OUs were created with Users, Computers, Groups, and Resources sub-OUs.
Branch-specific manager groups were created, manager users were assigned, and the groups were nested into GG_Branch_Managers.
PowerShell verification confirmed recursive group membership.
```

![Server Phase 9 Branch Manager Groups Snapshot Created](../screenshots/99%20-%20Server%20Phase%209%20Branch%20Manager%20Groups%20Snapshot%20Created.png)

---

## Screenshots Captured

| Screenshot | Description |
|---|---|
| `69 - Server Phase 9 Starting Snapshot Created.png` | Starting VirtualBox snapshot before Phase 9 changes |
| `70 - ADUC Original Branch OUs Before Expansion.png` | Original dog-themed branch OUs |
| `71 - ADUC Professional Branch OUs Created.png` | Professional branch OUs after renaming |
| `72 - ADUC Winnipeg-HQ Branch Sub-OUs Created.png` | Winnipeg-HQ sub-OUs created |
| `73 - ADUC Reykjavik-DR Branch Sub-OUs Created.png` | Reykjavik-DR sub-OUs created |
| `74 - ADUC Tokyo Branch Sub-OUs Created.png` | Tokyo sub-OUs created |
| `75 - ADUC London Branch Sub-OUs Created.png` | London sub-OUs created |
| `76 - ADUC Sydney Branch Sub-OUs Created.png` | Sydney sub-OUs created |
| `77 - ADUC Paris Branch Sub-OUs Created.png` | Paris sub-OUs created |
| `78 - ADUC New-York Branch Sub-OUs Created.png` | New-York sub-OUs created |
| `79 - ADUC All Branch Sub-OUs Verified.png` | All branch sub-OUs verified |
| `80 - ADUC Winnipeg-HQ Branch Manager Group Created.png` | Winnipeg-HQ manager group created |
| `81 - ADUC Reykjavik-DR Branch Manager Group Created.png` | Reykjavik-DR manager group created |
| `82 - ADUC Tokyo Branch Manager Group Created.png` | Tokyo manager group created |
| `83 - ADUC London Branch Manager Group Created.png` | London manager group created |
| `84 - ADUC Sydney Branch Manager Group Created.png` | Sydney manager group created |
| `85 - ADUC Paris Branch Manager Group Created.png` | Paris manager group created |
| `86 - ADUC New-York Branch Manager Group Created.png` | New-York manager group created |
| `87 - PowerShell Branch Manager Groups Verified.png` | Branch manager groups verified with PowerShell |
| `88 - ADUC Winnipeg-HQ Branch Manager Membership Added.png` | Ted added to Winnipeg-HQ manager group |
| `89 - ADUC Reykjavik-DR Branch Manager Membership Added.png` | Ozzy added to Reykjavik-DR manager group |
| `90 - ADUC Tokyo Branch Manager Membership Added.png` | Monty added to Tokyo manager group |
| `91 - ADUC London Branch Manager Membership Added.png` | Penny added to London manager group |
| `92 - ADUC Sydney Branch Manager Membership Added.png` | Daisy added to Sydney manager group |
| `93 - ADUC Paris Branch Manager Membership Added.png` | Chewy added to Paris manager group |
| `94 - ADUC New-York Branch Manager Membership Added.png` | PorkChop added to New-York manager group |
| `95 - PowerShell Branch Manager Memberships Verified.png` | Branch manager memberships verified with PowerShell |
| `96 - ADUC Branch Manager Groups Nested Into GG_Branch_Managers.png` | Branch manager groups nested into main group |
| `97 - PowerShell Branch Manager Group Nesting Verified.png` | Nested groups verified in PowerShell |
| `98 - PowerShell Recursive Branch Manager Membership Verified.png` | Recursive group membership verified |
| `99 - Server Phase 9 Branch Manager Groups Snapshot Created.png` | Final Phase 9 progress snapshot |

---

## Phase 9 Summary

Phase 9 expanded the LittleBuilds Active Directory lab into a more realistic branch-based company structure.

Completed work included:

- Renamed original dog-themed branch OUs into professional location-based branch OUs
- Created standard sub-OUs under each branch
- Created branch-specific manager security groups
- Assigned each branch manager to the correct branch group
- Nested branch-specific manager groups into `GG_Branch_Managers`
- Cleaned up redundant direct user memberships
- Verified group creation, group nesting, and recursive membership with PowerShell
- Took a safe VirtualBox snapshot after the work was completed

This phase prepares the lab for future branch-specific Group Policy, department mapping, automation, and access control testing.
