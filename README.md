# 🧱 LittleBuilds AD Lab

A hands-on Windows Server Active Directory homelab designed to practice real-world IT administration tasks, including domain setup, user and group management, shared folder permissions, Group Policy, DNS basics, and Windows client domain joining.

## 🎯 Project Goal

The goal of this lab is to build a small business-style Windows domain using Windows Server and a Windows client VM.

This project documents the setup process, configuration choices, screenshots, troubleshooting notes, and lessons learned while building a practical Active Directory environment.

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
- Shared folder permissions
- Group Policy basics
- DNS fundamentals
- Windows client domain joining
- Troubleshooting and documentation

## 🧩 Project Phases

| Phase | Description | Status |
|---|---|---|
| Phase 1 | Repository setup and project documentation | ✅ Complete |
| Phase 2 | Windows Server VM installation and baseline setup | ✅ Complete |
| Phase 3 | Domain controller setup | ✅ Complete |
| Phase 4 | Active Directory structure | ✅ Complete |
| Phase 5 | Users, groups, and OUs | ⏳ Planned |
| Phase 6 | Shared folders and permissions | ⏳ Planned |
| Phase 7 | Group Policy testing | ⏳ Planned |
| Phase 8 | Windows client domain join | ⏳ Planned |
| Phase 9 | Troubleshooting notes and final documentation | ⏳ Planned |

## 🔍 Planned Focus Areas

- Users and groups
- Security groups and distribution groups
- Shared folders and permissions
- Group Policy
- DNS basics
- PowerShell practice
- Windows client domain joining
- Troubleshooting and documentation

## 📸 Screenshots

Screenshots are being added throughout the project to document each major configuration step.

Current screenshots include:

- Windows Server VM setup
- Server Manager configuration
- VirtualBox VM configuration
- Baseline snapshot creation
- Domain login screen
- AD DS and DNS installation confirmation
- Domain controller Local Server details
- Domain controller snapshot creation
- Active Directory OU structure
- Branch OU structure
- Active Directory structure snapshot creation

Planned screenshots include:

- User and group creation
- Shared folder permission testing
- Group Policy results
- Windows 11 client domain join

## 📁 Documentation

Current documentation includes:

- `server-setup/windows-server-vm-setup.md`
- `active-directory/domain-controller-setup.md`
- `active-directory/active-directory-structure.md`

Future documentation will include:

- User and group creation
- Shared folder permissions
- Group Policy testing
- Windows client domain join
- Troubleshooting notes

## 💡 Why I Built This

I am building this lab to strengthen my practical IT skills and create a documented portfolio project that shows hands-on experience with Windows Server, Active Directory, virtualization, troubleshooting, and technical documentation.

## 📝 Lessons Learned

This section will be updated as the lab progresses. I will document configuration choices, troubleshooting steps, mistakes, fixes, and key takeaways from each phase.

Current lessons learned:

- A domain controller should use a static IP address.
- DNS is a major part of Active Directory and is installed with the domain controller role in this lab.
- VirtualBox snapshots are useful rollback points before and after major configuration changes.
- The first reboot after promoting a server to a domain controller can take time and may appear stuck.
- Custom OUs keep lab objects organized and separate from the default Active Directory containers.
- Creating the OU structure before users and groups makes the environment easier to manage.
- Clear screenshots and notes make the project easier to understand later.

## 🚧 Current Status

Phase 1, Phase 2, Phase 3, and Phase 4 are complete.

The repository has been created, the Windows Server 2022 VM has been installed, the server has been renamed to `LB-SRV-DC01`, VirtualBox Guest Additions have been installed, and a clean baseline snapshot has been created.

Active Directory Domain Services and DNS have been installed. The server has been promoted to a domain controller for the new domain `littlebuilds.local`, with the NetBIOS name `LITTLEBUILDS`.

A custom Active Directory OU structure has been created under the top-level `LittleBuilds` OU. The structure includes OUs for branches, departments, users, groups, computers, and resources.

A Phase 4 snapshot has been created after completing the Active Directory structure.

Next step: create users and groups inside the LittleBuilds Active Directory structure.
