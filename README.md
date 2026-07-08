# 🧱 LittleBuilds AD Lab

A hands-on Windows Server Active Directory homelab designed to practice real-world IT administration tasks, including domain setup, user and group management, shared folder permissions, Group Policy, DNS basics, Windows client domain joining, DHCP, file services, backup planning, firewall/routing concepts, Wireshark traffic analysis, and PowerShell automation.

## 🎯 Project Goal

The goal of this lab is to build a small business-style Windows domain using Windows Server and Windows client VMs.

This project documents the setup process, configuration choices, screenshots, troubleshooting notes, lessons learned, and future improvements while building a practical Active Directory environment.

The lab starts with manual Windows Server and Active Directory configuration first, then expands into more advanced topics such as Group Policy, client testing, file services, DHCP, Wireshark traffic analysis, firewall/routing concepts, disaster recovery, and PowerShell automation.

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
| Windows 11 Client VM | LittleBuilds-Win11-Client01 |
| Windows 11 Client Name | LB-WIN11-CL01 |
| Client OS | Windows 11 Pro |
| Lab Network | LittleBuildsLabNet |
| Lab Type | Small business-style Active Directory environment |
| Current Server Snapshot | 07 - Windows 11 Client Domain Join Complete |
| Current Windows 11 Client Snapshot | 01 - Domain Joined and Phase 8 Tested |

## 🌐 Network Configuration

| System | Adapter / Network | Purpose | Configuration |
|---|---|---|---|
| LB-SRV-DC01 | Ethernet | Internet access | NAT, DHCP |
| LB-SRV-DC01 | Ethernet 2 | Internal Active Directory lab network | Static IP |
| LB-WIN11-CL01 | Internal Network | Domain client communication | Static IP |

Server internal lab adapter configuration:

- Adapter name: `Ethernet 2`
- IP address: `10.10.10.10`
- Subnet mask: `255.255.255.0`
- Preferred DNS server: `10.10.10.10`
- Internal network name: `LittleBuildsLabNet`

Windows 11 client lab adapter configuration:

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
- VirtualBox display and boot troubleshooting
- Static IP configuration
- Internal network configuration in VirtualBox
- Active Directory Domain Services
- Domain controller setup
- DNS role installation
- DNS record cleanup
- DNS troubleshooting with `nslookup`
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
- Testing allowed and denied share access from a domain client
- Group Policy Management
- Group Policy Object creation
- GPO linking and OU targeting
- Computer Configuration vs User Configuration
- GPO inheritance basics
- Legal notice policy testing
- Control Panel restriction policy testing
- Workstation local administrator configuration through Group Policy Preferences
- `gpupdate /force`
- `gpresult`
- Elevated PowerShell troubleshooting
- Windows client domain joining
- Active Directory computer object organization
- DHCP planning and configuration
- File server planning
- Wireshark traffic analysis planning
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

- Branch structure expansion
- Bulk user import
- PowerShell automation
- Advanced groups and permissions
- Mapped network drives
- Dedicated file server setup
- DHCP configuration
- Wireshark traffic analysis
- Firewall and routing concepts
- Backup and disaster recovery
- Optional advanced Windows Server services
- Troubleshooting and documentation

## 🖥️ Planned Server and Client Roadmap

| System | Suggested Name | Purpose | Status |
|---|---|---|---|
| Domain Controller / DNS | LB-SRV-DC01 | Active Directory, DNS, users, groups, OUs, Group Policy | ✅ Built |
| Windows 11 Client | LB-WIN11-CL01 | Domain login, permissions testing, GPO testing | ✅ Built |
| File Server | LB-SRV-FS01 | Dedicated shared folder hosting | ⏳ Planned |
| DHCP Server | LB-SRV-DHCP01 | DHCP scopes, leases, reservations, client IP assignment | ⏳ Planned |
| Wireshark Analysis Workstation | TBD | Traffic capture, DNS/DHCP/AD troubleshooting practice | ⏳ Planned |
| Firewall / Router VM | LB-FW-01 | Firewall rules, routing, NAT, network separation | ⏳ Planned |
| Backup / DR Server | LB-SRV-BACKUP01 | Backup, restore, and disaster recovery testing | ⏳ Planned |
| Management Server | LB-SRV-MGMT01 | RSAT, admin tools, scripts, remote management | ⏳ Optional |
| WSUS Server | LB-SRV-WSUS01 | Windows update management | ⏳ Future |
| Certificate Authority | LB-SRV-CA01 | Internal certificates and trust services | ⏳ Future |
| Monitoring Server | LB-SRV-MON01 | Monitoring, uptime checks, and alerts | ⏳ Future |

## 🔎 Future Networking and Troubleshooting Expansion

A future phase will add Wireshark traffic analysis to the LittleBuilds AD Lab.

This phase will focus on observing and documenting common network traffic generated by the lab, such as DNS lookups, DHCP activity, domain authentication, Group Policy refreshes, and file share access.

The goal is to strengthen troubleshooting skills by connecting Windows Server and Active Directory concepts to the actual network traffic they create.

This Wireshark phase is planned after DHCP configuration and before firewall/routing work.

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
- `26 - Legal Notice GPO Linked to Domain Controllers.png`
- `27 - Group Policy Update Completed.png`
- `28 - Group Policy Result Shows Legal Notice GPO.png`
- `29 - Legal Notice Displayed at Sign-In.png`
- `30 - Legal Notice GPO Settings Configured.png`
- `31 - Control Panel Restriction GPO Linked to Standard Users.png`
- `32 - Control Panel Restriction GPO Settings Configured.png`
- `33 - Group Policy Testing Snapshot Created.png`
- `34 - Server IP Configuration Before Client Join.png`
- `35 - Windows 11 Client VM Created.png`
- `36 - Windows 11 VM System Settings Verified.png`
- `37 - Windows 11 VM Boot Troubleshooting Settings.png`
- `38 - Windows 11 Client VM Recreated with Boot Fix Settings.png`
- `39 - Windows 11 Client Display and ISO Settings Verified.png`
- `41 - Windows 11 Installer Started After Boot Troubleshooting.png`
- `42 - Windows 11 Install Disk Selected.png`
- `43 - Windows 11 OOBE Checking for Updates.png`
- `44 - Windows 11 Client Device Name Entered.png`
- `47 - Windows 11 Client Desktop After Guest Additions.png`
- `49 - Windows 11 Client Static IP and DNS Configured.png`
- `50 - Windows 11 Client Network Connectivity Verified.png`
- `50A - DNS Lookup Shows Extra Server NAT Address.png`
- `50C - DNS Zone After Removing NAT Address.png`
- `50D - NAT Adapter DNS Registration Disabled.png`
- `50E - DNS Lookup After Removing NAT Address.png`
- `51 - Windows 11 Client Joined to littlebuilds.local Domain.png`
- `52 - Windows 11 Domain User Login Verified.png`
- `53 - Windows 11 Client Computer Object in ADUC.png`
- `54 - Windows 11 Client Group Policy Update.png`
- `55 - Windows 11 Client gpresult User Policy as janine.admin.png`
- `56 - Windows 11 Client gpresult Computer Policy.png`
- `56A - Windows 11 Client User Groups Show No Local Administrator Membership.png`
- `56B - Windows 11 Client Computer gpresult Requires Administrator.png`
- `56C - Workstation Local Admin GPO Created.png`
- `56D - Workstation Local Admin GPO Adds GG_Admin_Staff.png`
- `56E - Windows 11 Client Local Administrators Group Updated by GPO.png`
- `57 - Windows 11 Standard User Group Policy Update.png`
- `58 - Windows 11 Standard User gpresult Shows Control Panel GPO.png`
- `59 - Windows 11 Standard User Control Panel Restricted.png`
- `60 - Windows 11 Standard User Settings Restricted.png`
- `61 - Windows 11 Standard User Public Share Access Allowed.png`
- `62 - Windows 11 Standard User Finance Share Access Denied.png`
- `63 - Windows 11 Standard User HR Share Access Denied.png`
- `64 - Windows 11 Admin User Finance Share Access Allowed.png`
- `65 - Windows 11 Admin User HR Share Access Allowed.png`
- `66 - Windows 11 Admin User Finance Modify Permission Verified.png`
- `67 - Windows 11 Client Phase 8 Snapshot Created.png`
- `68 - Server Phase 8 Snapshot Created.png`

Some screenshot numbers are skipped because certain planned or optional screenshots were not captured.

Planned screenshots include:

- Branch structure expansion
- Bulk user import results
- Advanced permissions testing
- Dedicated file server configuration
- DHCP configuration
- Wireshark traffic analysis
- Firewall/routing configuration
- Backup and restore testing

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

    Authenticated Users → Full Control

NTFS permissions were used for the actual folder access control.

Shared folder access was later tested from the Windows 11 domain-joined client during Phase 8.

## 🧪 Current Group Policy Configuration

Phase 7 introduced beginner Group Policy testing.

Two Group Policy Objects were created manually in Group Policy Management.

### GPO 1 - Legal Notice Test

GPO name:

- `LittleBuilds - Legal Notice Test`

Purpose:

- Displays a legal notice before sign-in.

Configuration path:

- `Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options`

Settings configured:

| Setting | Value |
|---|---|
| Interactive logon: Message title for users attempting to log on | `LittleBuilds Authorized Access Only` |
| Interactive logon: Message text for users attempting to log on | `This system is part of the LittleBuilds Active Directory lab. Access is limited to authorized LittleBuilds users only. Activity may be monitored for training, testing, and troubleshooting purposes.` |

Linked to:

- `littlebuilds.local > Domain Controllers`

Testing completed:

- Ran `gpupdate /force`
- Verified with `gpresult /scope computer /r`
- Signed out and confirmed the legal notice appeared before login
- Confirmed during Phase 8 that this GPO did not apply to the Windows 11 workstation because it is linked only to Domain Controllers

### GPO 2 - Control Panel Restriction Test

GPO name:

- `LittleBuilds - Control Panel Restriction Test`

Purpose:

- Restricts access to Control Panel and PC Settings for standard users.

Configuration path:

- `User Configuration > Policies > Administrative Templates > Control Panel`

Setting configured:

| Setting | Value |
|---|---|
| Prohibit access to Control Panel and PC settings | Enabled |

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

Configuration path:

- `Computer Configuration > Preferences > Control Panel Settings > Local Users and Groups`

Setting configured:

| Local Group | Added Member |
|---|---|
| Administrators | `LITTLEBUILDS\GG_Admin_Staff` |

Linked to:

- `littlebuilds.local > LittleBuilds > Computers > Workstations`

Testing completed:

- Ran `gpupdate /force`
- Restarted the Windows 11 client
- Verified using `net localgroup administrators`
- Confirmed `LITTLEBUILDS\GG_Admin_Staff` was added to the local Administrators group
- Confirmed elevated PowerShell could run `gpresult /scope computer /r`

## 💻 Windows 11 Client Domain Join

Phase 8 added a Windows 11 Pro client to the LittleBuilds domain.

Windows 11 client details:

| Item | Value |
|---|---|
| VirtualBox VM name | LittleBuilds-Win11-Client01 |
| Computer name | LB-WIN11-CL01 |
| Operating system | Windows 11 Pro |
| Domain | littlebuilds.local |
| Static IP address | 10.10.10.20 |
| Subnet mask | 255.255.255.0 |
| Default gateway | Blank |
| Preferred DNS | 10.10.10.10 |
| Internal network | LittleBuildsLabNet |

The Windows 11 client successfully joined the domain:

`littlebuilds.local`

The client was tested with the domain account:

`LITTLEBUILDS\janine.admin`

The login was verified using:

`whoami`

The result confirmed:

`littlebuilds\janine.admin`

The computer object `LB-WIN11-CL01` was moved from the default `Computers` container to:

`LittleBuilds > Computers > Workstations`

## 🧪 Phase 8 Client Testing

Phase 8 tested the Windows 11 client from both an administrator account and a standard user account.

Testing included:

- Domain login as `LITTLEBUILDS\janine.admin`
- Domain login as `LITTLEBUILDS\daisy.sales`
- `gpupdate /force`
- `gpresult /scope user /r`
- `gpresult /scope computer /r`
- Control Panel restriction testing
- Windows Settings restriction testing
- Shared folder access testing
- Finance share modify permission testing

A workstation local admin GPO was also created:

`LittleBuilds - Workstation Local Admins`

This GPO added:

`LITTLEBUILDS\GG_Admin_Staff`

to the local Administrators group on the Windows 11 client.

This allowed `janine.admin` to run elevated tools on the workstation.

## 🗂️ Phase 8 Shared Folder Test Results

Shared folder access was tested from the Windows 11 client.

| User | Public | Finance | HR |
|---|---|---|---|
| `daisy.sales` | ✅ Allowed | ❌ Denied | ❌ Denied |
| `janine.admin` | ✅ Expected allowed | ✅ Allowed | ✅ Allowed |

A modify permission test was completed in the Finance share while logged in as `janine.admin`.

A test file was created and deleted:

`Finance permission test.txt`

This confirmed that the Finance share Modify permissions worked correctly for an authorized user.

## 🧯 Phase 8 Troubleshooting Highlights

Phase 8 included several realistic troubleshooting moments.

### Windows 11 VM black screen

The Windows 11 VM initially displayed a black screen during boot/install.

The issue was resolved by changing the VirtualBox graphics controller from:

`VBoxSVGA`

to:

`VMSVGA`

### Incorrect DNS records

The domain DNS zone contained unwanted records pointing to the server NAT adapter IP address:

`10.0.2.15`

These records were removed, and DNS registration was disabled on the server NAT adapter.

After cleanup, the client resolved `littlebuilds.local` to the correct lab address:

`10.10.10.10`

### Local administrator rights

The `janine.admin` domain account could log into the Windows 11 workstation but was not initially a local administrator.

This was fixed by creating the `LittleBuilds - Workstation Local Admins` GPO.

### VirtualBox shutdown hang

After Phase 8 testing was completed, the Windows 11 client VM experienced a VirtualBox shutdown hang.

The VM had already booted successfully and all Phase 8 testing was complete.

The stuck VM process was ended using Task Manager. VirtualBox then showed the client VM state as:

`Aborted`

The VM was booted again afterward to confirm that it still loaded successfully.

This was documented as a VirtualBox shutdown issue, not a failed domain join or Active Directory issue.

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
- Hosting shared folders on the domain controller is acceptable for early lab practice, but a dedicated file server is more realistic for a production-style environment.
- Planning the lab in phases helps keep the project organized and beginner-friendly.
- It is useful to learn the manual Windows Server process before adding PowerShell automation.
- Clear screenshots and notes make the project easier to understand later.
- Group Policy Objects can be created separately before they are linked to an OU.
- A GPO does not apply just because it exists; it must be linked to the correct domain or OU.
- Computer Configuration settings apply to computers.
- User Configuration settings apply to user accounts.
- A legal notice is a beginner-friendly Computer Configuration policy because it can be visibly tested at sign-in.
- User-based GPOs should be linked to the OU where the target users are located.
- The Control Panel restriction GPO was linked to `Standard-Users` so administrator and service accounts are not restricted.
- `gpupdate /force` refreshes Group Policy manually.
- `gpresult` helps confirm which GPOs were applied.
- Group Policy testing is easier to understand when screenshots show both the GPO link and the configured settings.
- The Windows Server time zone should be correct because Active Directory and domain authentication depend on accurate time.
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

Sample users, a service account, security groups, and group memberships have been created manually in Active Directory Users and Computers. Janine Admin represents Head Office, and each standard dog account represents a LittleBuilds branch lead.

A professional company branch model has been documented for future expansion. This includes planned branches for Winnipeg-HQ, Reykjavik-DR, Tokyo, London, Sydney, Paris, and New-York.

Shared folders have been created on the domain controller under `C:\Shares`. The Public, Finance, and HR folders were shared and secured using share permissions, NTFS permissions, and Active Directory security groups.

The shares were verified in Computer Management, through UNC paths, and from the Windows 11 domain-joined client.

Group Policy testing has been completed. A legal notice GPO was created, linked to the Domain Controllers OU, refreshed with `gpupdate /force`, verified with `gpresult`, and tested successfully at sign-in.

A Control Panel restriction GPO was created and linked to the Standard-Users OU. This policy was tested successfully from the Windows 11 client using the standard domain user `daisy.sales`.

A Windows 11 Pro client VM has been created, configured, joined to the `littlebuilds.local` domain, and tested. The client computer object was moved to `LittleBuilds > Computers > Workstations`.

A workstation local admin GPO was created to add `LITTLEBUILDS\GG_Admin_Staff` to the local Administrators group on the Windows 11 client.

Shared folder access was tested from the Windows 11 client. Daisy Sales was allowed into Public but denied access to Finance and HR. Janine Admin was allowed into Finance and HR, and Modify permissions were verified in Finance.

Current VirtualBox snapshots:

- Server: `07 - Windows 11 Client Domain Join Complete`
- Windows 11 client: `01 - Domain Joined and Phase 8 Tested`

The project roadmap has expanded to include branch expansion, bulk user import, a dedicated file server, DHCP, Wireshark traffic analysis, firewall/routing concepts, backup and disaster recovery, and optional advanced Windows Server services.

Next step: Phase 9 - Branch structure expansion.
