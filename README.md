# 🧱 LittleBuilds AD Lab

A hands-on Windows Server Active Directory homelab designed to practice real-world IT administration tasks, including domain setup, user and group management, shared folder permissions, Group Policy, DNS basics, Windows client domain joining, DHCP, file services, backup planning, firewall/routing concepts, and PowerShell automation.

## 🎯 Project Goal

The goal of this lab is to build a small business-style Windows domain using Windows Server and Windows client VMs.

This project documents the setup process, configuration choices, screenshots, troubleshooting notes, lessons learned, and future improvements while building a practical Active Directory environment.

The lab starts with manual Windows Server and Active Directory configuration first, then expands into more advanced topics such as Group Policy, client testing, file services, DHCP, firewall/routing concepts, disaster recovery, and PowerShell automation.

## 🖥️ Lab Environment

| Component | Details |
|---|---|
| Virtualization Platform | Oracle VirtualBox |
| Server VM | LittleBuilds-Server01 |
| Server Name | LB-SRV-DC01 |
| Server OS | Windows Server 2022 Standard Evaluation |
| Install Type | Desktop Experience |
| Domain Name | littlebuilds.local |
| NetBIOS Domain Name | LITTLEBUILDS |
| Domain Controller | LB-SRV-DC01 |
| Client OS | Windows 11 planned |
| Lab Network | LittleBuildsLabNet |
| Lab Type | Small business-style Active Directory environment |

## 🌐 Network Configuration

| Adapter | Purpose | Configuration |
|---|---|---|
| Ethernet | Internet access | NAT, DHCP |
| Ethernet 2 | Internal Active Directory lab network | Static IP |

Ethernet 2 is configured for the internal lab network:

- IP address: `10.10.10.10`
- Subnet mask: `255.255.255.0`
- Preferred DNS server: `10.10.10.10`
- Internal network name: `LittleBuildsLabNet`

## 🛠️ Skills Practiced

- Windows Server installation and configuration
- Virtual machine setup and snapshot management
- Static IP configuration
- Active Directory Domain Services
- Domain controller setup
- DNS role installation
- Active Directory Users and Computers
- Organizational Unit planning and creation
- User and group administration
- Security group planning
- Group membership management
- Shared folder creation
- Share permissions
- NTFS permissions
- Share permissions vs NTFS permissions
- Group-based access control
- Group Policy basics
- DNS fundamentals
- Windows client domain joining
- DHCP planning and configuration
- File server planning
- Basic firewall and routing concepts
- Backup and disaster recovery planning
- PowerShell automation planning
- Bulk user import planning
- Troubleshooting and documentation
- GitHub portfolio documentation

## 🧩 Project Phases

| Phase | Description | Status |
|---|---|---|
| Phase 1 | Repository setup and project documentation | ✅ Complete |
| Phase 2 | Windows Server VM installation and baseline setup | ✅ Complete |
| Phase 3 | Domain controller setup | ✅ Complete |
| Phase 4 | Active Directory structure | ✅ Complete |
| Phase 5 | Users, groups, and OUs | ✅ Complete |
| Phase 5.5 | Company branch design documentation | ✅ Complete |
| Phase 6 | Shared folders and permissions | ✅ Complete |
| Phase 7 | Group Policy testing | ⏭️ Next |
| Phase 8 | Windows 11 client domain join | ⏳ Planned |
| Phase 9 | Branch structure expansion | ⏳ Planned |
| Phase 10 | Bulk user import and PowerShell automation | ⏳ Planned |
| Phase 11 | Advanced groups and permissions | ⏳ Planned |
| Phase 12 | Dedicated file server | ⏳ Planned |
| Phase 13 | DHCP server | ⏳ Planned |
| Phase 14 | Firewall / routing lab | ⏳ Planned |
| Phase 15 | Backup and disaster recovery | ⏳ Planned |
| Phase 16 | Optional advanced services | ⏳ Planned |
| Phase 17 | Portfolio cleanup and final documentation | ⏳ Planned |

## 🏢 Company Branch Model

LittleBuilds AD Lab is designed as a fictional small-business-style organization with multiple branches.

The current early lab structure uses dog-themed branch OUs to make the project memorable and fun. A more professional location-based branch model is planned for a later phase.

Future planned branch model:

- Winnipeg-HQ
- Reykjavik-DR
- Tokyo
- London
- Sydney
- Paris
- New-York

Planned branch purpose:

| Branch | Purpose |
|---|---|
| Winnipeg-HQ | Head Office / Main Operations |
| Reykjavik-DR | Disaster Recovery / Business Continuity |
| Tokyo | Regional Operations |
| London | Regional Administration / Compliance |
| Sydney | Field Operations |
| Paris | Client Relations / Design |
| New-York | Security / Infrastructure |

Each branch may eventually include:

- Users
- Groups
- Computers
- Service Accounts

The official documentation will describe the company model professionally, while the internal lab theme can still use the LittleBuilds dog-inspired concept.

## 🔍 Planned Focus Areas

- Group Policy testing
- DNS basics
- Windows 11 client domain joining
- Client login testing
- Mapped network drives
- Shared folder access testing from a domain-joined client
- File server setup
- DHCP configuration
- Firewall and routing concepts
- Backup and disaster recovery
- PowerShell automation
- Bulk user import
- Troubleshooting and documentation

## 🖥️ Planned Server and Client Roadmap

| System | Suggested Name | Purpose | Status |
|---|---|---|---|
| Domain Controller / DNS | LB-SRV-DC01 | Active Directory, DNS, users, groups, OUs, Group Policy | ✅ Built |
| Windows 11 Client | LB-WIN11-CL01 | Domain login, permissions testing, GPO testing | ⏳ Planned |
| File Server | LB-SRV-FS01 | Dedicated shared folder hosting | ⏳ Planned |
| DHCP Server | LB-SRV-DHCP01 | DHCP scopes, leases, reservations, client IP assignment | ⏳ Planned |
| Firewall / Router VM | LB-FW-01 | Firewall rules, routing, NAT, network separation | ⏳ Planned |
| Backup / DR Server | LB-SRV-BACKUP01 | Backup, restore, and disaster recovery testing | ⏳ Planned |
| Management Server | LB-SRV-MGMT01 | RSAT, admin tools, scripts, remote management | ⏳ Optional |
| WSUS Server | LB-SRV-WSUS01 | Windows update management | ⏳ Future |
| Certificate Authority | LB-SRV-CA01 | Internal certificates and trust services | ⏳ Future |
| Monitoring Server | LB-SRV-MON01 | Monitoring, uptime checks, and alerts | ⏳ Future |

## 📸 Screenshots

Screenshots are being added throughout the project to document each major configuration step.

Current screenshots include:

- `01 - Clean Install - Renamed Server.png`
- `02 - VirtualBox VM Configuration.png`
- `03 - Baseline Snapshot Created.png`
- `04 - Domain Login Screen.png`
- `05 - AD DS and DNS Installed.png`
- `06 - Domain Controller Local Server.png`
- `07 - Domain Controller Snapshot Created.png`
- `08 - Active Directory OU Structure Created.png`
- `09 - Branch OU Structure.png`
- `10 - Active Directory Structure Snapshot Created.png`
- `11 - Admin User Created.png`
- `12 - Standard Users Created.png`
- `13 - Security Groups Created.png`
- `14 - User Group Membership Example.png`
- `15 - Users and Groups Snapshot Created.png`
- `16 - Shares Folder Created.png`
- `17 - Public Folder NTFS Permissions.png`
- `18 - Finance Folder NTFS Permissions.png`
- `19 - HR Folder NTFS Permissions.png`
- `20 - Public Shared Folder Group Members.png`
- `21 - Finance Shared Folder Group Members.png`
- `22 - HR Shared Folder Group Members.png`
- `23 - Shared Folders Listed in Computer Management.png`
- `24 - UNC Share Path Verification.png`
- `25 - Shared Folders Snapshot Created.png`

Planned screenshots include:

- Group Policy configuration
- Group Policy results
- Windows 11 client domain join
- Client share access testing
- Branch structure expansion
- Bulk user import results
- File server configuration
- DHCP configuration
- Backup and restore testing

## 📁 Documentation

Current documentation includes:

- `server-setup/windows-server-vm-setup.md`
- `active-directory/domain-controller-setup.md`
- `active-directory/active-directory-structure.md`
- `active-directory/users-and-groups.md`
- `company/branch-list.md`
- `active-directory/shared-folders-and-permissions.md`

Planned documentation includes:

- `active-directory/group-policy-testing.md`
- `client-setup/windows-11-domain-join.md`
- `active-directory/branch-structure-expansion.md`
- `automation/bulk-user-import.md`
- `active-directory/advanced-groups-and-permissions.md`
- `server-setup/file-server-setup.md`
- `server-setup/dhcp-server-setup.md`
- `network/firewall-routing-lab.md`
- `disaster-recovery/backup-and-restore.md`
- `server-setup/wsus-server-setup.md`
- `server-setup/certificate-authority-setup.md`
- `monitoring/monitoring-server-setup.md`
- `docs/project-summary.md`
- `docs/network-diagram.md`
- `docs/skills-demonstrated.md`
- `docs/future-improvements.md`

## 📂 Current Active Directory Structure

Current OU structure:

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

## 👥 Current Lab Users

Admin user:

- `janine.admin` — Janine Admin — Head Office / Lab Administrator

Standard users:

- `ted.it` — Ted LittleBuilds — IT Manager / Barkdesk Operations
- `ozzy.security` — Ozzy Security — Security Operations
- `monty.operations` — Monty Operations — Operations Manager
- `chewy.hr` — Chewy HR — HR Assistant
- `penny.executive` — Penny Executive — Executive Office
- `daisy.sales` — Daisy Sales — Sales Representative
- `porkchop.risk` — PorkChop Risk — Risk Management

Service account:

- `svc.backup` — Backup Service Account

## 🔐 Current Security Groups

Security groups created in:

`LittleBuilds/Groups/Security-Groups`

Current security groups:

- `GG_Admin_Staff`
- `GG_IT_Staff`
- `GG_Finance_Staff`
- `GG_HR_Staff`
- `GG_Operations_Staff`
- `GG_Sales_Staff`
- `GG_Branch_Managers`
- `GG_Shared_Finance_RW`
- `GG_Shared_HR_RW`
- `GG_Shared_Public_Read`

Current group memberships:

| User | Group Membership |
|---|---|
| `janine.admin` | `GG_Admin_Staff`, `GG_Shared_Public_Read`, `GG_Shared_Finance_RW`, `GG_Shared_HR_RW` |
| `ted.it` | `GG_IT_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read` |
| `ozzy.security` | `GG_Operations_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read` |
| `monty.operations` | `GG_Operations_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read` |
| `chewy.hr` | `GG_HR_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read`, `GG_Shared_HR_RW` |
| `penny.executive` | `GG_Admin_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read`, `GG_Shared_Finance_RW` |
| `daisy.sales` | `GG_Sales_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read` |
| `porkchop.risk` | `GG_Operations_Staff`, `GG_Branch_Managers`, `GG_Shared_Public_Read` |
| `svc.backup` | No normal staff group membership assigned |

## 🗂️ Shared Folder Configuration

Phase 6 created shared folders and configured access using security groups.

Folder paths:

- `C:\Shares`
- `C:\Shares\Public`
- `C:\Shares\Finance`
- `C:\Shares\HR`

Share names:

- `Public`
- `Finance`
- `HR`

UNC paths:

- `\\LB-SRV-DC01\Public`
- `\\LB-SRV-DC01\Finance`
- `\\LB-SRV-DC01\HR`

Access groups:

| Folder | Security Group | Access |
|---|---|---|
| Public | `GG_Shared_Public_Read` | Read & Execute |
| Finance | `GG_Shared_Finance_RW` | Modify |
| HR | `GG_Shared_HR_RW` | Modify |

Share permissions were configured as:

```text
Authenticated Users → Full Control
```

NTFS permissions were used for the actual folder access control.

## ⚙️ Future Automation Plan

A later phase will introduce PowerShell automation and bulk user import.

Planned automation work:

- Create a CSV employee list
- Include employee details such as first name, last name, username, branch, department, title, manager, and group membership
- Use PowerShell to create users in Active Directory
- Place users into the correct branch and department OUs
- Assign users to appropriate security groups
- Test import with a small group before importing a larger batch
- Import a larger test set of 100–300 users

Possible future files:

- `scripts/import-users.ps1`
- `data/littlebuilds-employees.csv`
- `automation/bulk-user-import.md`

## 💡 Why I Built This

I am building this lab to strengthen my practical IT skills and create a documented portfolio project that shows hands-on experience with Windows Server, Active Directory, virtualization, troubleshooting, permissions, networking concepts, automation, and technical documentation.

The project is designed to grow from a simple domain controller lab into a more complete small-business-style IT environment.

## 📝 Lessons Learned

This section will be updated as the lab progresses. I will document configuration choices, troubleshooting steps, mistakes, fixes, and key takeaways from each phase.

Current lessons learned:

- A domain controller should use a static IP address.
- DNS is a major part of Active Directory and is installed with the domain controller role in this lab.
- VirtualBox snapshots are useful rollback points before and after major configuration changes.
- The first reboot after promoting a server to a domain controller can take time and may appear stuck.
- Custom OUs keep lab objects organized and separate from the default Active Directory containers.
- Creating the OU structure before users and groups makes the environment easier to manage.
- Admin users, standard users, and service accounts should be separated into appropriate OUs.
- Security groups make permissions easier to manage than assigning access directly to individual users.
- Group memberships can be based on department, role, or access needs.
- Shared-folder access groups can be created before the folders exist.
- Share permissions and NTFS permissions are separate permission systems.
- Share permissions control access through the network share.
- NTFS permissions control access to the actual folder and files.
- When both share permissions and NTFS permissions apply, the most restrictive permission wins.
- Keeping share permissions broad and NTFS permissions specific can make permissions easier to manage in a beginner lab.
- Disabling inheritance allows folder permissions to be controlled more intentionally.
- Removing generic `Users` permissions helps ensure access is controlled through dedicated security groups.
- A Windows client VM will be needed to fully test domain logins, mapped drives, permissions, and Group Policy.
- Hosting shared folders on the domain controller is acceptable for early lab practice, but a dedicated file server is more realistic for a production-style environment.
- Planning the lab in phases helps keep the project organized and beginner-friendly.
- It is useful to learn the manual Windows Server process before adding PowerShell automation.
- Clear screenshots and notes make the project easier to understand later.

## 🚧 Current Status

Phase 1, Phase 2, Phase 3, Phase 4, Phase 5, Phase 5.5, and Phase 6 are complete.

The repository has been created, the Windows Server 2022 VM has been installed, the server has been renamed to `LB-SRV-DC01`, VirtualBox Guest Additions have been installed, and a clean baseline snapshot has been created.

Active Directory Domain Services and DNS have been installed. The server has been promoted to a domain controller for the new domain `littlebuilds.local`, with the NetBIOS name `LITTLEBUILDS`.

A custom Active Directory OU structure has been created under the top-level `LittleBuilds` OU. The structure includes OUs for branches, departments, users, groups, computers, and resources.

Sample users, a service account, security groups, and group memberships have been created manually in Active Directory Users and Computers. Janine Admin represents Head Office, and each standard dog account represents a LittleBuilds branch lead.

A professional company branch model has been documented for future expansion. This includes planned branches for Winnipeg-HQ, Reykjavik-DR, Tokyo, London, Sydney, Paris, and New-York.

Shared folders have been created on the domain controller under `C:\Shares`. The Public, Finance, and HR folders were shared and secured using share permissions, NTFS permissions, and Active Directory security groups.

The shares were verified in Computer Management and through the UNC path `\\LB-SRV-DC01`.

A Phase 6 snapshot has been created after completing shared folder and permissions configuration.

The project roadmap has expanded to include Group Policy, Windows client testing, branch expansion, bulk user import, a dedicated file server, DHCP, firewall/routing concepts, backup and disaster recovery, and optional advanced Windows Server services.

Next step: Phase 7 - Group Policy testing.
