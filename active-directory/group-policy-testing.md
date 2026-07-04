# Phase 7 - Group Policy Testing

## Overview

This phase documents beginner-friendly Group Policy testing in the LittleBuilds Active Directory lab.

The goal of this phase was to learn the manual Group Policy process before using PowerShell. Two Group Policy Objects were created:

1. A legal notice GPO that displays a message before sign-in.
2. A Control Panel restriction GPO for standard users.

The legal notice GPO was fully tested on the domain controller. The Control Panel restriction GPO was created and linked, but full testing will be completed later after a Windows 11 client is joined to the domain.

## Lab Environment

- Server VM: `LittleBuilds-Server01`
- Server name: `LB-SRV-DC01`
- Operating system: Windows Server 2022 Standard Evaluation, Desktop Experience
- Domain: `littlebuilds.local`
- NetBIOS domain name: `LITTLEBUILDS`
- Domain controller: `LB-SRV-DC01`
- Internal network name: `LittleBuildsLabNet`
- Server IP address: `10.10.10.10`
- Preferred DNS: `10.10.10.10`

## Group Policy Concepts Practiced

This phase introduced the basic Group Policy workflow:

1. Open Group Policy Management.
2. Create a new Group Policy Object.
3. Edit the GPO settings.
4. Link the GPO to the correct OU.
5. Run `gpupdate /force`.
6. Verify applied policies with `gpresult`.
7. Test the visible policy result.
8. Document the configuration with screenshots.
9. Shut down the VM normally.
10. Create a VirtualBox snapshot.

## What Group Policy Does

Group Policy is used to apply settings to users and computers in an Active Directory domain.

Instead of manually configuring every computer or user account, a domain administrator can create Group Policy Objects and link them to domains or organizational units.

Examples of settings that can be managed with Group Policy include:

- Logon messages
- Security settings
- Desktop settings
- Mapped drives
- Control Panel restrictions
- Printer settings
- User environment settings

## User Configuration vs Computer Configuration

Group Policy has two main sections:

### Computer Configuration

Computer Configuration applies to the computer itself, regardless of which user logs in.

Examples:

- Security settings
- Startup scripts
- Windows firewall settings
- Logon/legal notice settings

### User Configuration

User Configuration applies to the user account.

Examples:

- Desktop settings
- Mapped drives
- Control Panel restrictions
- Start menu restrictions
- Logon scripts

## GPO 1 - Legal Notice Test

### GPO Name

`LittleBuilds - Legal Notice Test`

### Purpose

This GPO displays a legal notice before users can sign in.

This was chosen as the first test GPO because it is beginner-friendly, visible, and can be tested on the domain controller.

### Configuration Path

The policy was configured in:

`Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options`

### Settings Configured

| Setting | Value |
|---|---|
| Interactive logon: Message title for users attempting to log on | `LittleBuilds Authorized Access Only` |
| Interactive logon: Message text for users attempting to log on | `This system is part of the LittleBuilds Active Directory lab. Access is limited to authorized LittleBuilds users only. Activity may be monitored for training, testing, and troubleshooting purposes.` |

### GPO Link

The GPO was linked to:

`littlebuilds.local > Domain Controllers`

### Reason for Linking to Domain Controllers

The Windows 11 client is not domain-joined yet. Because the domain controller is currently the only domain-joined computer available for testing, the legal notice GPO was linked to the Domain Controllers OU.

This allowed the policy to be tested on `LB-SRV-DC01`.

## Group Policy Update

After creating and linking the legal notice GPO, Group Policy was refreshed using:

    gpupdate /force

The update completed successfully for both computer policy and user policy.

## Group Policy Result Verification

The applied computer policies were checked using:

    gpresult /scope computer /r

The results showed that the following GPOs applied to the domain controller:

- Default Domain Controllers Policy
- LittleBuilds - Legal Notice Test
- Default Domain Policy

This confirmed that the legal notice GPO applied successfully.

## Legal Notice Test Result

After signing out of the domain controller, the legal notice appeared before login.

The sign-in notice displayed the configured title and message, confirming that the GPO was working.

## GPO 2 - Control Panel Restriction Test

### GPO Name

`LittleBuilds - Control Panel Restriction Test`

### Purpose

This GPO restricts access to Control Panel and PC Settings for standard users.

This was created as a beginner-friendly User Configuration policy. It will be fully tested later after a Windows 11 client is joined to the domain.

### Configuration Path

The policy was configured in:

`User Configuration > Policies > Administrative Templates > Control Panel`

### Setting Configured

| Setting | Value |
|---|---|
| Prohibit access to Control Panel and PC settings | Enabled |

### GPO Link

The GPO was linked to:

`littlebuilds.local > LittleBuilds > Users > Standard-Users`

### Reason for Linking to Standard-Users

This GPO is a User Configuration policy, so it should be linked where the target user accounts are located.

The policy was linked to the Standard-Users OU to avoid applying the restriction to administrator accounts or service accounts.

## Current Testing Limitation

The Control Panel restriction GPO was created, configured, and linked successfully, but it was not fully tested in this phase.

Reason:

- The Windows 11 client is not domain-joined yet.
- Standard users should not be used for normal desktop testing on the domain controller.
- Full workstation testing will be completed after the Windows 11 client joins the domain.

This will be completed in Phase 8.

## GPO Inheritance and OU Targeting Notes

Group Policy applies based on where a GPO is linked.

A GPO linked to an OU applies to objects inside that OU. Group Policy can also flow downward through nested OUs.

Examples:

- A GPO linked to `Domain Controllers` targets domain controllers.
- A GPO linked to `LittleBuilds > Users > Standard-Users` targets standard users.
- A GPO linked higher in the OU structure may apply to child OUs through inheritance.

For this phase:

| GPO | Linked To | Target Type |
|---|---|---|
| LittleBuilds - Legal Notice Test | Domain Controllers | Computer |
| LittleBuilds - Control Panel Restriction Test | LittleBuilds > Users > Standard-Users | User |

## Screenshots

The following screenshots were captured for this phase:

| Screenshot | Description |
|---|---|
| `26 - Legal Notice GPO Linked to Domain Controllers.png` | Shows the legal notice GPO linked to the Domain Controllers OU |
| `27 - Group Policy Update Completed.png` | Shows `gpupdate /force` completing successfully |
| `28 - Group Policy Result Shows Legal Notice GPO.png` | Shows the legal notice GPO listed under applied computer policies |
| `29 - Legal Notice Displayed at Sign-In.png` | Shows the legal notice appearing before sign-in |
| `30 - Legal Notice GPO Settings Configured.png` | Shows the configured legal notice settings |
| `31 - Control Panel Restriction GPO Linked to Standard Users.png` | Shows the Control Panel restriction GPO linked to Standard-Users |
| `32 - Control Panel Restriction GPO Settings Configured.png` | Shows the Control Panel restriction setting enabled |
| `33 - Group Policy Testing Snapshot Created.png` | Shows the Phase 7 VirtualBox snapshot |

## VirtualBox Snapshot

After Group Policy testing was completed, the server was shut down normally and a VirtualBox snapshot was created.

Snapshot name:

`06 - Group Policy Testing Complete`

Snapshot description:

`Phase 7 completed. Created and tested beginner Group Policy Objects including a legal notice GPO linked to Domain Controllers and a Control Panel restriction GPO linked to Standard-Users.`

## Phase 7 Summary

Phase 7 successfully introduced basic Group Policy management.

Completed tasks:

- Opened Group Policy Management
- Created a legal notice GPO
- Configured computer-based legal notice settings
- Linked the legal notice GPO to the Domain Controllers OU
- Ran `gpupdate /force`
- Verified the applied GPO with `gpresult`
- Confirmed the legal notice appeared at sign-in
- Created a Control Panel restriction GPO
- Configured a user-based Control Panel restriction
- Linked the Control Panel restriction GPO to the Standard-Users OU
- Documented Group Policy settings with screenshots
- Created a VirtualBox snapshot after completion

## Next Step

The next phase is:

**Phase 8 - Windows 11 Client Domain Join**

In Phase 8, a Windows 11 client VM will be connected to the LittleBuilds domain. This will allow user-based and computer-based Group Policy testing on a workstation.
