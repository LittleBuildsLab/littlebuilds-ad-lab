# Active Directory Structure

## Overview

This phase documents the organizational unit structure created for the LittleBuilds Active Directory lab.

The goal of this phase was to create a clean, small business-style Active Directory layout before adding users, groups, computers, shared folders, or Group Policy Objects.

## Domain

- Domain name: `littlebuilds.local`
- NetBIOS domain name: `LITTLEBUILDS`
- Domain controller: `LB-SRV-DC01`

## Top-Level OU

A top-level organizational unit was created to keep lab objects separate from the default Active Directory containers.

Top-level OU:

`LittleBuilds`

## Main OU Structure

The following main OUs were created under `LittleBuilds`:

- `Branches`
- `Departments`
- `Users`
- `Groups`
- `Computers`
- `Resources`

## Branch OUs

The `Branches` OU contains branch OUs based on the LittleBuilds dog-themed company structure:

- `Ozzy-Branch`
- `Monty-Branch`
- `Chewy-Branch`
- `Penny-Branch`
- `Daisy-Branch`
- `PorkChop-Branch`
- `Ted-Branch`

## Department OUs

The `Departments` OU contains the following department OUs:

- `Administration`
- `Finance`
- `HR`
- `IT`
- `Operations`
- `Sales`

## User OUs

The `Users` OU contains:

- `Admin-Users`
- `Standard-Users`
- `Service-Accounts`

## Group OUs

The `Groups` OU contains:

- `Security-Groups`
- `Distribution-Groups`

## Computer OUs

The `Computers` OU contains:

- `Workstations`
- `Servers`

## Resource OUs

The `Resources` OU contains:

- `Shared-Folders`
- `Printers`

```

## Configuration Notes

- The OU structure was created manually using Active Directory Users and Computers.
- Default Active Directory containers such as `Users` and `Computers` were left unchanged.
- Lab objects will be created inside the custom `LittleBuilds` OU structure.
- The option to protect containers from accidental deletion was left enabled when creating OUs.
- The structure was created before adding users, groups, computers, shared folders, or Group Policy Objects.

## Screenshots

### Active Directory OU structure created

This screenshot shows the custom LittleBuilds OU structure created under the `littlebuilds.local` domain. The structure includes OUs for branches, departments, users, groups, computers, and resources.

![Active Directory OU structure created](../screenshots/08%20-%20Active%20Directory%20OU%20Structure%20Created.png)

### Branch OU structure

This screenshot shows the dog-themed branch OUs created under the `Branches` OU, including Ozzy, Monty, Chewy, Penny, Daisy, PorkChop, and Ted.

![Branch OU structure](../screenshots/09%20-%20Branch%20OU%20Structure.png)

### Active Directory structure snapshot created

This screenshot shows the VirtualBox snapshot created after completing the Active Directory OU structure.

![Active Directory structure snapshot created](../screenshots/10%20-%20Active%20Directory%20Structure%20Snapshot%20Created.png)

## Snapshot

Snapshot created after completing the Active Directory structure:

`03 - Active Directory Structure Created`

## Notes

This snapshot was created before adding users, groups, computers, shared folders, or Group Policy Objects.

## OU Structure

```text
littlebuilds.local
└── LittleBuilds
    ├── Branches
    │   ├── Ozzy-Branch
    │   ├── Monty-Branch
    │   ├── Chewy-Branch
    │   ├── Penny-Branch
    │   ├── Daisy-Branch
    │   ├── PorkChop-Branch
    │   └── Ted-Branch
    ├── Departments
    │   ├── Administration
    │   ├── Finance
    │   ├── HR
    │   ├── IT
    │   ├── Operations
    │   └── Sales
    ├── Users
    │   ├── Admin-Users
    │   ├── Standard-Users
    │   └── Service-Accounts
    ├── Groups
    │   ├── Security-Groups
    │   └── Distribution-Groups
    ├── Computers
    │   ├── Workstations
    │   └── Servers
    └── Resources
        ├── Shared-Folders
        └── Printers

