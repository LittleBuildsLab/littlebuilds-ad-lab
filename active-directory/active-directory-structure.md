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
