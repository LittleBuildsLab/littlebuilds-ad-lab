# Phase 8 - Windows 11 Client Domain Join

## Overview

This phase documents the installation, configuration, domain join, Group Policy testing, and shared folder access testing for a Windows 11 client in the LittleBuilds Active Directory lab.

The goal of this phase was to add a Windows 11 workstation to the `littlebuilds.local` domain and confirm that the client could communicate with the domain controller, receive Group Policy, and access shared folders based on Active Directory group membership.

## Lab Environment

| Item | Value |
|---|---|
| Server VM | `LittleBuilds-Server01` |
| Server name | `LB-SRV-DC01` |
| Server OS | Windows Server 2022 Standard Evaluation |
| Domain | `littlebuilds.local` |
| NetBIOS domain | `LITTLEBUILDS` |
| Domain controller | `LB-SRV-DC01` |
| Internal network | `LittleBuildsLabNet` |
| Server lab IP | `10.10.10.10` |
| Server DNS | `10.10.10.10` |
| Windows 11 client VM | `LittleBuilds-Win11-Client01` |
| Windows 11 computer name | `LB-WIN11-CL01` |
| Windows 11 edition | Windows 11 Pro |
| Client IP address | `10.10.10.20` |
| Client subnet mask | `255.255.255.0` |
| Client default gateway | Blank |
| Client preferred DNS | `10.10.10.10` |

## Starting Snapshot

Before beginning Phase 8, the server VM had the following VirtualBox snapshot:

`06 - Group Policy Testing Complete`

## Windows 11 VM Creation

A new Windows 11 client VM was created in Oracle VirtualBox.

The VM was named:

`LittleBuilds-Win11-Client01`

Windows 11 Pro was installed, and the Windows computer name was set to:

`LB-WIN11-CL01`

A local setup account was created:

`localadmin`

VirtualBox Guest Additions were installed after Windows reached the desktop.

After installation, the Windows 11 installer ISO and Guest Additions ISO were removed from the virtual optical drive.

## Windows 11 Boot Troubleshooting

During the initial Windows 11 VM setup, the client VM displayed a black screen during boot/install.

Troubleshooting steps included:

- Recreating the Windows 11 VM
- Using Windows 11 Pro
- Disabling unattended install
- Setting chipset to `ICH9`
- Keeping UEFI enabled
- Temporarily disabling Secure Boot
- Setting TPM to `2.0`
- Setting video memory to `128 MB`
- Changing the graphics controller from `VBoxSVGA` to `VMSVGA`
- Remounting the Windows 11 ISO during boot

The issue was resolved by changing the graphics controller to:

`VMSVGA`

After this change, the Windows 11 installer loaded successfully.

## Client Network Configuration

After Windows 11 was installed, the client VM network adapter was changed to:

`Internal Network`

The internal network name was set to:

`LittleBuildsLabNet`

The Windows 11 client was configured with the following static IPv4 settings:

| Setting | Value |
|---|---|
| IP address | `10.10.10.20` |
| Subnet mask | `255.255.255.0` |
| Default gateway | Blank |
| Preferred DNS | `10.10.10.10` |

This allowed the Windows 11 client to communicate with the domain controller using the private lab network.

## DNS Troubleshooting

Before the client joined the domain, DNS testing showed that the `littlebuilds.local` DNS zone contained incorrect records pointing to the server NAT adapter address:

`10.0.2.15`

The incorrect DNS records were found in DNS Manager under:

`Forward Lookup Zones > littlebuilds.local`

The following incorrect records were removed:

- `(same as parent folder) Host (A) 10.0.2.15`
- `lb-srv-dc01 Host (A) 10.0.2.15`

The correct records were kept:

- `(same as parent folder) Host (A) 10.10.10.10`
- `lb-srv-dc01 Host (A) 10.10.10.10`

DNS registration was also disabled on the server NAT adapter so the NAT IP address would not re-register in DNS.

After the fix, `nslookup littlebuilds.local` from the Windows 11 client returned the correct lab address:

`10.10.10.10`

The incorrect `10.0.2.15` address was no longer returned.

## Domain Join

The Windows 11 client successfully joined the domain:

`littlebuilds.local`

After rebooting, the client was logged into using the domain account:

`LITTLEBUILDS\janine.admin`

The login was verified using:

`whoami`

The result confirmed the domain login:

`littlebuilds\janine.admin`

## Active Directory Computer Object

After joining the domain, the Windows 11 client computer object appeared in the default Active Directory `Computers` container.

The computer object was moved to the custom LittleBuilds workstation OU:

`LittleBuilds > Computers > Workstations`

The final computer object location was:

`CN=LB-WIN11-CL01,OU=Workstations,OU=Computers,OU=LittleBuilds,DC=littlebuilds,DC=local`

## Group Policy Update

Group Policy was refreshed on the Windows 11 client using:

`gpupdate /force`

Both computer policy and user policy completed successfully.

## User Group Policy Result - Janine Admin

The following command was run while logged in as `LITTLEBUILDS\janine.admin`:

`gpresult /scope user /r`

The result showed that no user GPOs were applied to `janine.admin`.

This was expected because the Control Panel restriction GPO was linked to:

`LittleBuilds > Users > Standard-Users`

The `janine.admin` account is located in:

`LittleBuilds > Users > Admin-Users`

This confirmed that the standard user restriction did not apply to the admin account.

## Workstation Local Admin GPO

While testing computer Group Policy results, the Windows 11 client returned an access denied error when attempting to run:

`gpresult /scope computer /r`

This happened because the `janine.admin` domain account was not yet a local administrator on the Windows 11 workstation.

To fix this, a new GPO was created:

`LittleBuilds - Workstation Local Admins`

The GPO was linked to:

`LittleBuilds > Computers > Workstations`

The GPO was configured using:

`Computer Configuration > Preferences > Control Panel Settings > Local Users and Groups`

The GPO added the following domain group to the local Administrators group on the Windows 11 workstation:

`LITTLEBUILDS\GG_Admin_Staff`

After Group Policy refreshed and the client restarted, the local Administrators group was checked using:

`net localgroup administrators`

The result confirmed that the local Administrators group included:

- `Administrator`
- `LITTLEBUILDS\Domain Admins`
- `LITTLEBUILDS\GG_Admin_Staff`
- `localadmin`

This confirmed that the workstation local admin GPO worked successfully.

## Computer Group Policy Result

After opening PowerShell as Administrator, the following command was run:

`gpresult /scope computer /r`

The applied computer GPOs included:

- `LittleBuilds - Workstation Local Admins`
- `Default Domain Policy`

The Legal Notice GPO did not apply to the Windows 11 workstation.

This was expected because the Legal Notice GPO is linked only to:

`Domain Controllers`

The Windows 11 workstation is located in:

`LittleBuilds > Computers > Workstations`

Therefore, the Legal Notice GPO applies to the domain controller sign-in screen, not to the Windows 11 client.

## Standard User Group Policy Test

The Windows 11 client was then tested using a standard domain user:

`LITTLEBUILDS\daisy.sales`

The login was verified using:

`whoami`

The result confirmed:

`littlebuilds\daisy.sales`

Group Policy was refreshed using:

`gpupdate /force`

Both computer policy and user policy completed successfully.

The following command was then run:

`gpresult /scope user /r`

The result showed that the following GPO applied to Daisy:

`LittleBuilds - Control Panel Restriction Test`

This was expected because Daisy is located in:

`LittleBuilds > Users > Standard-Users`

## Control Panel and Settings Restriction Test

The Control Panel restriction GPO was tested while logged in as:

`LITTLEBUILDS\daisy.sales`

The Control Panel was blocked successfully.

Windows Settings was also tested. Settings did not open, but no restriction message appeared. This was documented as a silent block.

This confirmed that the GPO setting worked:

`Prohibit access to Control Panel and PC settings = Enabled`

## Shared Folder Access Testing

Shared folder access was tested from the Windows 11 client.

The shared folders tested were:

- `\\LB-SRV-DC01\Public`
- `\\LB-SRV-DC01\Finance`
- `\\LB-SRV-DC01\HR`

### Daisy Sales Access Test

The following access results were confirmed while logged in as:

`LITTLEBUILDS\daisy.sales`

| Share | Result |
|---|---|
| `\\LB-SRV-DC01\Public` | Allowed |
| `\\LB-SRV-DC01\Finance` | Denied |
| `\\LB-SRV-DC01\HR` | Denied |

This was expected because Daisy is a member of:

`GG_Shared_Public_Read`

Daisy is not a member of:

- `GG_Shared_Finance_RW`
- `GG_Shared_HR_RW`

### Janine Admin Access Test

The following access results were confirmed while logged in as:

`LITTLEBUILDS\janine.admin`

| Share | Result |
|---|---|
| `\\LB-SRV-DC01\Finance` | Allowed |
| `\\LB-SRV-DC01\HR` | Allowed |

A modify permission test was also completed in the Finance share.

A test file was created and deleted:

`Finance permission test.txt`

This confirmed that `janine.admin` had Modify permissions on the Finance share.

## VirtualBox Shutdown Note

After Phase 8 testing was completed, the Windows 11 client VM experienced a VirtualBox shutdown hang.

The VM had already booted successfully and all Phase 8 testing was complete.

The stuck VM process was ended using Task Manager. VirtualBox then showed the client VM state as:

`Aborted`

The VM was booted again afterward to confirm that it still loaded successfully.

This was documented as a VirtualBox shutdown issue, not a failed domain join or Active Directory issue.

## Final Snapshots

After Phase 8 testing, final VirtualBox snapshots were created.

### Windows 11 Client Snapshot

`01 - Domain Joined and Phase 8 Tested`

### Server Snapshot

`07 - Windows 11 Client Domain Join Complete`

## Screenshots

Some screenshot numbers are skipped because certain planned or optional screenshots were not captured.

The following screenshots were captured during Phase 8:

```text
34 - Server IP Configuration Before Client Join.png
35 - Windows 11 Client VM Created.png
36 - Windows 11 VM System Settings Verified.png
37 - Windows 11 VM Boot Troubleshooting Settings.png
38 - Windows 11 Client VM Recreated with Boot Fix Settings.png
39 - Windows 11 Client Display and ISO Settings Verified.png
41 - Windows 11 Installer Started After Boot Troubleshooting.png
42 - Windows 11 Install Disk Selected.png
43 - Windows 11 OOBE Checking for Updates.png
44 - Windows 11 Client Device Name Entered.png
47 - Windows 11 Client Desktop After Guest Additions.png
49 - Windows 11 Client Static IP and DNS Configured.png
50 - Windows 11 Client Network Connectivity Verified.png
50A - DNS Lookup Shows Extra Server NAT Address.png
50C - DNS Zone After Removing NAT Address.png
50D - NAT Adapter DNS Registration Disabled.png
50E - DNS Lookup After Removing NAT Address.png
51 - Windows 11 Client Joined to littlebuilds.local Domain.png
52 - Windows 11 Domain User Login Verified.png
53 - Windows 11 Client Computer Object in ADUC.png
54 - Windows 11 Client Group Policy Update.png
55 - Windows 11 Client gpresult User Policy as janine.admin.png
56 - Windows 11 Client gpresult Computer Policy.png
56A - Windows 11 Client User Groups Show No Local Administrator Membership.png
56B - Windows 11 Client Computer gpresult Requires Administrator.png
56C - Workstation Local Admin GPO Created.png
56D - Workstation Local Admin GPO Adds GG_Admin_Staff.png
56E - Windows 11 Client Local Administrators Group Updated by GPO.png
57 - Windows 11 Standard User Group Policy Update.png
58 - Windows 11 Standard User gpresult Shows Control Panel GPO.png
59 - Windows 11 Standard User Control Panel Restricted.png
60 - Windows 11 Standard User Settings Restricted.png
61 - Windows 11 Standard User Public Share Access Allowed.png
62 - Windows 11 Standard User Finance Share Access Denied.png
63 - Windows 11 Standard User HR Share Access Denied.png
64 - Windows 11 Admin User Finance Share Access Allowed.png
65 - Windows 11 Admin User HR Share Access Allowed.png
66 - Windows 11 Admin User Finance Modify Permission Verified.png
67 - Windows 11 Client Phase 8 Snapshot Created.png
68 - Server Phase 8 Snapshot Created.png
```

## Phase 8 Summary

Phase 8 successfully added a Windows 11 Pro client to the LittleBuilds Active Directory domain.

This phase confirmed:

- Windows 11 VM installation and configuration
- VirtualBox display troubleshooting
- Guest Additions installation
- Internal lab network configuration
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

Phase 8 is complete.
