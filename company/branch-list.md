# 🏢 Little Builds Inc. Branch List

This document outlines the planned professional branch model for the LittleBuilds AD Lab.

The current Active Directory lab uses dog-themed branch OUs for the early learning phases. This branch list represents the future professional company structure that may be implemented in a later Active Directory redesign or expansion phase.

## Overview

Little Builds Inc. is designed as a fictional small-business-style organization with multiple global branches. Each branch is used to practice realistic Active Directory administration tasks, including Organizational Unit design, user and group management, branch-based permissions, shared folder access, and future Group Policy testing.

The official documentation will describe the company structure professionally, while the internal lab theme can still use the LittleBuilds dog-inspired concept to make the project memorable and fun.

---

# Branch List

## 1. Winnipeg-HQ

**Branch Type:** Head Office / Main Operations

**Purpose:**  
Winnipeg-HQ is the main office for Little Builds Inc. This branch represents company leadership, administration, finance, HR, IT administration, and core business operations.

**Suggested AD Use:**

- Main headquarters OU
- Executive/admin users
- IT admin accounts
- Finance and HR users
- Core security groups
- Main shared folders

**Possible Departments:**

- Executive
- IT
- Finance
- Human Resources
- Administration
- Operations

---

## 2. Reykjavik-DR

**Branch Type:** Disaster Recovery / Business Continuity Branch

**Purpose:**  
Reykjavik-DR is the disaster recovery branch for Little Builds Inc. It is used to represent backup planning, emergency access, business continuity, and recovery-related administrative testing.

**Suggested AD Use:**

- Disaster recovery users
- Backup administrator groups
- Emergency access accounts
- Business continuity testing
- Backup and restore permission groups

**Possible Departments:**

- Disaster Recovery
- Backup Operations
- Security
- Infrastructure
- Emergency Access

---

## 3. Tokyo

**Branch Type:** Regional Operations Branch

**Purpose:**  
Tokyo represents an international branch focused on regional operations, technical coordination, and business support for the Asia-Pacific region.

**Suggested AD Use:**

- Regional users
- Department-based groups
- Location-based access testing
- Time zone/global branch practice

**Possible Departments:**

- Operations
- IT Support
- Sales
- Customer Success
- Administration

---

## 4. London

**Branch Type:** Regional Administration / Compliance Branch

**Purpose:**  
London represents a regional office focused on administration, policy, compliance, documentation, and business coordination.

**Suggested AD Use:**

- Administrative users
- Compliance groups
- Policy-based Group Policy testing
- Department and location group testing

**Possible Departments:**

- Administration
- Compliance
- Finance
- Legal
- IT Support

---

## 5. Sydney

**Branch Type:** Field Operations Branch

**Purpose:**  
Sydney represents a branch focused on field work, project coordination, operations, and support staff.

**Suggested AD Use:**

- Field operations users
- Project coordinator accounts
- Shared folder permissions for active projects
- Branch-based group membership

**Possible Departments:**

- Field Operations
- Project Coordination
- Administration
- IT Support
- Logistics

---

## 6. Paris

**Branch Type:** Client Relations / Design Branch

**Purpose:**  
Paris represents a client-facing branch focused on client relations, design coordination, communications, and project presentation work.

**Suggested AD Use:**

- Client relations users
- Design/project users
- Shared folders for proposals and client documents
- Department-based permissions

**Possible Departments:**

- Client Relations
- Design
- Marketing
- Communications
- Administration

---

## 7. New-York

**Branch Type:** Security / Infrastructure Branch

**Purpose:**  
New-York represents a larger high-activity branch focused on security, infrastructure, access control, and technical operations.

**Suggested AD Use:**

- Security users
- Infrastructure users
- Privileged access group testing
- Group Policy testing
- Restricted shared folder access

**Possible Departments:**

- Security
- Infrastructure
- IT Support
- Operations
- Administration

---

# Suggested Branch Naming Standard

Use simple location-based names for Active Directory OUs:

- `Winnipeg-HQ`
- `Reykjavik-DR`
- `Tokyo`
- `London`
- `Sydney`
- `Paris`
- `New-York`

---

# Suggested Future Branch OU Structure

Each branch can eventually use this structure:

```text
LittleBuilds
└── Branches
    ├── Winnipeg-HQ
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    ├── Reykjavik-DR
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    ├── Tokyo
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    ├── London
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    ├── Sydney
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    ├── Paris
    │   ├── Users
    │   ├── Groups
    │   ├── Computers
    │   └── Service Accounts
    └── New-York
        ├── Users
        ├── Groups
        ├── Computers
        └── Service Accounts
```

---

# Possible Internal Branch Theme

The lab may continue to use the LittleBuilds dog theme internally.

Possible future mapping:

| Internal Lab Character | Professional Branch |
|---|---|
| Janine / Head Office | Winnipeg-HQ |
| Ozzy | Reykjavik-DR |
| Ted | New-York |
| Daisy | Tokyo |
| Chewy | London |
| Monty | Sydney |
| Penny | Paris |
| PorkChop | Security / Risk role under New-York or Reykjavik-DR |

This mapping is optional and may be adjusted later when the branch structure is formally implemented in Active Directory.

---

# Implementation Notes

This document is currently a planning document only.

The existing Active Directory structure will not be changed during Phase 5.5. The location-based branch model is planned for a later phase after shared folders, Group Policy, and client testing are completed.

Planned implementation phase:

- **Phase 9 — Branch Structure Expansion**

Until then, the existing dog-themed branch OUs remain in place.

---

# Lessons Learned

- Planning the company structure before changing Active Directory helps avoid unnecessary redesign work.
- A professional branch naming model makes the project easier to understand in a portfolio.
- A fun internal theme can make the lab more memorable while still keeping official documentation professional.
- Branch-based OUs can later support user organization, computer placement, Group Policy testing, and location-based permissions.
