# 🧱 LittleBuilds AD Lab

A hands-on Windows Server Active Directory homelab built in Oracle VirtualBox.

This project documents the process of building a small business-style Windows domain, including Active Directory, DNS, users and groups, shared folders, Group Policy, Windows client domain joining, troubleshooting, and future expansion into DHCP, Wireshark, firewall/routing, backups, and automation.

## 🎯 Project Goal

The goal of this lab is to build a practical Windows Server Active Directory environment that demonstrates real IT administration skills.

This project is designed to show:

- Windows Server setup and configuration
- Active Directory Domain Services
- DNS configuration and troubleshooting
- User, group, and OU management
- Shared folder and NTFS permissions
- Group Policy creation and testing
- Windows 11 client domain joining
- Client-side access testing
- Troubleshooting and documentation
- Future PowerShell automation and network services

The lab starts with manual configuration first, then gradually expands into more advanced and realistic small-business IT scenarios.

## 🖥️ Lab Environment

| Component | Details |
|---|---|
| Virtualization Platform | Oracle VirtualBox |
| Server VM | `LittleBuilds-Server01` |
| Server Name | `LB-SRV-DC01` |
| Server OS | Windows Server 2022 Standard Evaluation |
| Install Type | Desktop Experience |
| Domain Name | `littlebuilds.local` |
| NetBIOS Domain Name | `LITTLEBUILDS` |
| Domain Controller | `LB-SRV-DC01` |
| Windows 11 Client VM | `LittleBuilds-Win11-Client01` |
| Windows 11 Client Name | `LB-WIN11-CL01` |
| Client OS | Windows 11 Pro |
| Lab Network | `LittleBuildsLabNet` |
| Lab Type | Small business-style Active Directory environment |

## 🌐 Network Configuration

| System | Purpose | Configuration |
|---|---|---|
| `LB-SRV-DC01` | Domain Controller / DNS | Static IP |
| `LB-WIN11-CL01` | Domain-joined workstation | Static IP |

Server internal lab adapter:

- IP address: `10.10.10.10`
- Subnet mask: `255.255.255.0`
- Preferred DNS server: `10.10.10.10`
- Internal network name: `LittleBuildsLabNet`

Windows 11 client adapter:

- IP address: `10.10.10.20`
- Subnet mask: `255.255.255.0`
- Default gateway: Blank
- Preferred DNS server: `10.10.10.10`
- Internal network name: `LittleBuildsLabNet`

## 🛠️ Skills Practiced

- Windows Server installation and configuration
- Windows 11 Pro installation and configuration
- Virtual machine setup and snapshot management
- VirtualBox Guest Additions installation
- VirtualBox boot and display troubleshooting
- Static IP addressing
- Internal VirtualBox networking
- Active Directory Domain Services
- Domain controller setup
- DNS role installation
- DNS record cleanup
- DNS troubleshooting with `nslookup`
- Active Directory Users and Computers
- Organizational Unit planning
- User and group administration
- Security group planning
- Shared folder creation
- Share permissions
- NTFS permissions
- Share permissions vs NTFS permissions
- Group-based access control
- Group Policy Management
- Group Policy Object creation
- GPO linking and OU targeting
- Computer Configuration vs User Configuration
- `gpupdate /force`
- `gpresult`
- Workstation local administrator configuration through GPO
- Windows client domain joining
- Client-side permissions testing
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
| Phase 7 | Group Policy testing | ✅ Complete |
| Phase 8 | Windows 11 client domain join | ✅ Complete |
| Phase 9 | Branch structure expansion | ⏳ Planned |
| Phase 10 | Bulk user import and PowerShell automation | ⏳ Planned |
| Phase 11 | Advanced groups and permissions | ⏳ Planned |
| Phase 12 | Dedicated file server | ⏳ Planned |
| Phase 13 | DHCP server | ⏳ Planned |
| Phase 14 | Wireshark traffic analysis | ⏳ Planned |
| Phase 15 | Firewall / routing lab | ⏳ Planned |
| Phase 16 | Backup and disaster recovery | ⏳ Planned |
| Phase 17 | Optional advanced services | ⏳ Planned |
| Phase 18 | Portfolio cleanup and final documentation | ⏳ Planned |

## 🏢 Company Branch Model

LittleBuilds AD Lab is designed as a fictional small-business-style organization with multiple branches.

The current early lab structure uses dog-themed branch OUs to make the project memorable and fun. A more professional location-based branch model is planned for a later phase.

Future planned branch model:

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

## 🖥️ Server and Client Roadmap

| System | Suggested Name | Purpose | Status |
|---|---|---|---|
| Domain Controller / DNS | `LB-SRV-DC01` | Active Directory, DNS, users, groups, OUs, Group Policy | ✅ Built |
| Windows 11 Client | `LB-WIN11-CL01` | Domain login, permissions testing, GPO testing | ✅ Built |
| File Server | `LB-SRV-FS01` | Dedicated shared folder hosting | ⏳ Planned |
| DHCP Server | `LB-SRV-DHCP01` | DHCP scopes, leases, reservations, client IP assignment | ⏳ Planned |
| Wireshark Analysis Workstation | TBD | Traffic capture and troubleshooting practice | ⏳ Planned |
| Firewall / Router VM | `LB-FW-01` | Firewall rules, routing, NAT, network separation | ⏳ Planned |
| Backup / DR Server | `LB-SRV-BACKUP01` | Backup, restore, and disaster recovery testing | ⏳ Planned |
| Management Server | `LB-SRV-MGMT01` | RSAT, admin tools, scripts, remote management | ⏳ Optional |
| WSUS Server | `LB-SRV-WSUS01` | Windows update management | ⏳ Future |
| Certificate Authority | `LB-SRV-CA01` | Internal certificates and trust services | ⏳ Future |
| Monitoring Server | `LB-SRV-MON01` | Monitoring, uptime checks, and alerts | ⏳ Future |

## 🔎 Future Networking and Troubleshooting Expansion

A future phase will add Wireshark traffic analysis to the LittleBuilds AD Lab.

This phase will focus on observing and documenting common network traffic generated by the lab, such as DNS lookups, DHCP activity, domain authentication, Group Policy refreshes, and file share access.

The goal is to strengthen troubleshooting skills by connecting Windows Server and Active Directory concepts to the actual network traffic they create.

This Wireshark phase is planned after DHCP configuration and before firewall/routing work.

## 📁 Documentation

Current documentation includes:

- `server-setup/windows-server-vm-setup.md`
- `active-directory/domain-controller-setup.md`
- `active-directory/active-directory-structure.md`
- `active-directory/users-and-groups.md`
- `company/branch-list.md`
- `active-directory/shared-folders-and-permissions.md`
- `active-directory/group-policy-testing.md`
- `client-setup/windows-11-domain-join.md`

Planned documentation includes:

- `active-directory/branch-structure-expansion.md`
- `automation/bulk-user-import.md`
- `active-directory/advanced-groups-and-permissions.md`
- `server-setup/file-server-setup.md`
- `server-setup/dhcp-server-setup.md`
- `network/wireshark-traffic-analysis.md`
- `network/firewall-routing-lab.md`
- `disaster-recovery/backup-and-restore.md`
- `server-setup/wsus-server-setup.md`
- `server-setup/certificate-authority-setup.md`
- `monitoring/monitoring-server-setup.md`
- `docs/project-summary.md`
- `docs/network-diagram.md`
- `docs/skills-demonstrated.md`
- `docs/future-improvements.md`

## 📸 Screenshots

Screenshots are stored in the `screenshots/` folder.

Screenshots currently document:

- Windows Server installation and baseline setup
- Domain controller promotion
- Active Directory OU structure
- User and group creation
- Shared folder permissions
- Group Policy configuration and testing
- Windows 11 client VM setup
- Windows 11 boot troubleshooting
- DNS troubleshooting
- Domain join testing
- Group Policy testing from the Windows 11 client
- Shared folder access testing from the Windows 11 client
- Final Phase 8 snapshots

Some screenshot numbers are skipped because certain planned or optional screenshots were not captured.

## 📂 Current Active Directory Structure

Current OU structure:

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
```

The Windows 11 client computer object is located in:

`LittleBuilds > Computers > Workstations`

Computer object:

- `LB-WIN11-CL01`

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

Shared folder access was later tested from the Windows 11 domain-joined client during Phase 8.

## 🧪 Current Group Policy Configuration

### GPO 1 - Legal Notice Test

GPO name:

- `LittleBuilds - Legal Notice Test`

Purpose:

- Displays a legal notice before sign-in.

Linked to:

- `littlebuilds.local > Domain Controllers`

Testing completed:

- Ran `gpupdate /force`
- Verified with `gpresult /scope computer /r`
- Confirmed the legal notice appeared before login
- Confirmed during Phase 8 that this GPO did not apply to the Windows 11 workstation because it is linked only to Domain Controllers

### GPO 2 - Control Panel Restriction Test

GPO name:

- `LittleBuilds - Control Panel Restriction Test`

Purpose:

- Restricts access to Control Panel and PC Settings for standard users.

Linked to:

- `littlebuilds.local > LittleBuilds > Users > Standard-Users`

Testing completed:

- Tested from the Windows 11 domain-joined client
- Verified with `gpupdate /force`
- Verified with `gpresult /scope user /r`
- Confirmed the GPO applied to `LITTLEBUILDS\daisy.sales`
- Confirmed Control Panel was blocked
- Confirmed Windows Settings did not open for the standard user

### GPO 3 - Workstation Local Admins

GPO name:

- `LittleBuilds - Workstation Local Admins`

Purpose:

- Adds the LittleBuilds admin staff group to the local Administrators group on domain-joined workstations.

Linked to:

- `littlebuilds.local > LittleBuilds > Computers > Workstations`

Configured member:

- `LITTLEBUILDS\GG_Admin_Staff`

Testing completed:

- Ran `gpupdate /force`
- Restarted the Windows 11 client
- Verified using `net localgroup administrators`
- Confirmed `LITTLEBUILDS\GG_Admin_Staff` was added to the local Administrators group
- Confirmed elevated PowerShell could run `gpresult /scope computer /r`

## 💻 Phase 8 - Windows 11 Client Domain Join

Phase 8 added a Windows 11 Pro client to the LittleBuilds domain.

Full documentation:

- `client-setup/windows-11-domain-join.md`

Windows 11 client details:

| Item | Value |
|---|---|
| VirtualBox VM name | `LittleBuilds-Win11-Client01` |
| Computer name | `LB-WIN11-CL01` |
| Operating system | Windows 11 Pro |
| Domain | `littlebuilds.local` |
| Static IP address | `10.10.10.20` |
| Subnet mask | `255.255.255.0` |
| Default gateway | Blank |
| Preferred DNS | `10.10.10.10` |
| Internal network | `LittleBuildsLabNet` |

Phase 8 confirmed:

- Windows 11 VM installation
- VirtualBox display troubleshooting
- Guest Additions installation
- Internal network configuration
- Static IP and DNS configuration
- DNS record cleanup
- Domain join
- Domain user login
- AD computer object organization
- Group Policy refresh and reporting
- Workstation local admin rights through GPO
- Standard user Control Panel restriction
- Shared folder access based on group membership
- Final VirtualBox snapshots

## 🗂️ Phase 8 Shared Folder Test Results

Shared folder access was tested from the Windows 11 client.

| User | Public | Finance | HR |
|---|---|---|---|
| `daisy.sales` | ✅ Allowed | ❌ Denied | ❌ Denied |
| `janine.admin` | ✅ Expected allowed | ✅ Allowed | ✅ Allowed |

A modify permission test was completed in the Finance share while logged in as `janine.admin`.

A test file was created and deleted:

`Finance permission test.txt`

This confirmed that Finance share Modify permissions worked correctly for an authorized user.

## 🧯 Troubleshooting Highlights

Troubleshooting documented so far includes:

- First domain controller reboot appeared slow after promotion
- Windows 11 VM black screen during boot/install
- VirtualBox graphics controller changed from `VBoxSVGA` to `VMSVGA`
- Incorrect DNS records pointing to the server NAT adapter IP address `10.0.2.15`
- DNS registration disabled on the server NAT adapter
- `janine.admin` could log into the workstation but was not initially a local administrator
- Workstation local administrator rights fixed through Group Policy Preferences
- Computer-side `gpresult` required elevated PowerShell
- VirtualBox shutdown hang occurred after Phase 8 testing and was documented honestly

## ⚙️ Future Automation Plan

A later phase will introduce PowerShell automation and bulk user import.

Planned automation work:

- Create a CSV employee list
- Include employee details such as first name, last name, username, branch, department, title, manager, and group membership
- Use PowerShell to create users in Active Directory
- Place users into the correct branch and department OUs
- Assign users to appropriate security groups
- Test import with a small group before importing a larger batch
- Import a larger test set of 100-300 users

Possible future files:

- `scripts/import-users.ps1`
- `data/littlebuilds-employees.csv`
- `automation/bulk-user-import.md`

## 💡 Why I Built This

I am building this lab to strengthen my practical IT skills and create a documented portfolio project that shows hands-on experience with Windows Server, Active Directory, virtualization, troubleshooting, permissions, networking concepts, automation, and technical documentation.

The project is designed to grow from a simple domain controller lab into a more complete small-business-style IT environment.

## 📝 Lessons Learned

Current lessons learned:

- A domain controller should use a static IP address.
- DNS is a major part of Active Directory and is installed with the domain controller role in this lab.
- VirtualBox snapshots are useful rollback points before and after major configuration changes.
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
- Hosting shared folders on the domain controller is acceptable for early lab practice, but a dedicated file server is more realistic for a production-style environment.
- Planning the lab in phases helps keep the project organized and beginner-friendly.
- It is useful to learn the manual Windows Server process before adding PowerShell automation.
- Clear screenshots and notes make the project easier to understand later.
- Group Policy Objects can be created separately before they are linked to an OU.
- A GPO does not apply just because it exists; it must be linked to the correct domain or OU.
- Computer Configuration settings apply to computers.
- User Configuration settings apply to user accounts.
- User-based GPOs should be linked to the OU where the target users are located.
- `gpupdate /force` refreshes Group Policy manually.
- `gpresult` helps confirm which GPOs were applied.
- Windows 11 Pro is required for joining an Active Directory domain.
- A domain-joined computer object may appear in the default `Computers` container before being moved into a custom OU.
- DNS records must point clients to the correct domain controller IP address.
- A server NAT adapter can accidentally register an unwanted DNS record if DNS registration is enabled.
- `nslookup` is useful for confirming that the client resolves the domain to the correct domain controller address.
- A domain user can log into a workstation without automatically being a local administrator.
- A domain security group can be added to local workstation Administrators using Group Policy Preferences.
- Computer-side `gpresult` may require an elevated PowerShell window.
- GPO location matters: the Legal Notice GPO did not apply to the Windows 11 workstation because it was linked only to Domain Controllers.
- Standard user GPO testing is best performed from a domain-joined client using a standard domain account.
- Shared folder permissions should be tested from a client workstation, not only from the server.
- Successful access and denied access are both important test results.
- VirtualBox shutdown hangs can happen and should be documented honestly as troubleshooting notes.

## 🚧 Current Status

Phase 1, Phase 2, Phase 3, Phase 4, Phase 5, Phase 5.5, Phase 6, Phase 7, and Phase 8 are complete.

The repository has been created, the Windows Server 2022 VM has been installed, the server has been renamed to `LB-SRV-DC01`, VirtualBox Guest Additions have been installed, and a clean baseline snapshot has been created.

Active Directory Domain Services and DNS have been installed. The server has been promoted to a domain controller for the new domain `littlebuilds.local`, with the NetBIOS name `LITTLEBUILDS`.

A custom Active Directory OU structure has been created under the top-level `LittleBuilds` OU. The structure includes OUs for branches, departments, users, groups, computers, and resources.

Sample users, a service account, security groups, and group memberships have been created manually in Active Directory Users and Computers.

Shared folders have been created on the domain controller under `C:\Shares`. The Public, Finance, and HR folders were shared and secured using share permissions, NTFS permissions, and Active Directory security groups.

Group Policy testing has been completed. A legal notice GPO was tested on the domain controller, a Control Panel restriction GPO was tested from the Windows 11 client, and a workstation local admin GPO was created for domain-joined workstations.

A Windows 11 Pro client VM has been created, configured, joined to the `littlebuilds.local` domain, and tested. The client computer object was moved to `LittleBuilds > Computers > Workstations`.

Shared folder access was tested from the Windows 11 client. Daisy Sales was allowed into Public but denied access to Finance and HR. Janine Admin was allowed into Finance and HR, and Modify permissions were verified in Finance.

Current VirtualBox snapshots:

- Server: `07 - Windows 11 Client Domain Join Complete`
- Windows 11 client: `01 - Domain Joined and Phase 8 Tested`

The project roadmap has expanded to include branch expansion, bulk user import, a dedicated file server, DHCP, Wireshark traffic analysis, firewall/routing concepts, backup and disaster recovery, and optional advanced Windows Server services.

Next step: Phase 9 - Branch structure expansion.
