# Domain Controller Setup

## Overview

This phase documents the setup of the first domain controller for the LittleBuilds Active Directory lab.

The Windows Server VM was promoted to a domain controller for a new Active Directory forest and domain.

## Server Details

- Server name: `LB-SRV-DC01`
- Domain name: `littlebuilds.local`
- NetBIOS domain name: `LITTLEBUILDS`
- Operating system: Windows Server 2022 Standard Evaluation
- Virtualization platform: Oracle VirtualBox

## Network Configuration

The server has two network adapters:

| Adapter | Purpose | Configuration |
|---|---|---|
| Ethernet | Internet access | NAT, DHCP |
| Ethernet 2 | Internal Active Directory lab network | Static IP |

Ethernet 2 was configured with the following static IP settings:

- IP address: `10.10.10.10`
- Subnet mask: `255.255.255.0`
- Default gateway: blank
- Preferred DNS server: `10.10.10.10`

## Roles Installed

The following server roles were installed:

- Active Directory Domain Services
- DNS Server

## Domain Controller Promotion

The server was promoted using the Active Directory Domain Services Configuration Wizard.

Configuration selected:

- Deployment option: Add a new forest
- Root domain name: `littlebuilds.local`
- Forest functional level: Windows Server 2016
- Domain functional level: Windows Server 2016
- DNS server: enabled
- Global Catalog: enabled
- Read-only domain controller: disabled
- DNS delegation: not created

## Verification

After promotion and reboot, the server login screen showed:

`LITTLEBUILDS\Administrator`

Server Manager confirmed that the following roles were installed and visible:

- AD DS
- DNS

The Local Server page confirmed:

- Computer name: `LB-SRV-DC01`
- Domain: `littlebuilds.local`
- Ethernet 2 static IP: `10.10.10.10`

## Snapshot

Snapshot created after the domain controller setup:

`02 - Domain Controller Created`

## Screenshots

### Domain login screen

This screenshot confirms that the server is now using the new Active Directory domain login format, showing `LITTLEBUILDS\Administrator`.

![Domain login screen](../screenshots/04%20-%20Domain%20Login%20Screen.png)

### AD DS and DNS installed

This screenshot shows Server Manager after the domain controller promotion. The left menu confirms that both AD DS and DNS roles are installed.

![AD DS and DNS installed](../screenshots/05%20-%20AD%20DS%20and%20DNS%20Installed.png)

### Domain controller local server details

This screenshot confirms the server name, domain membership, and static internal IP address used for the LittleBuilds Active Directory lab.

![Domain controller local server details](../screenshots/06%20-%20Domain%20Controller%20Local%20Server.png)

### Domain controller snapshot created

This screenshot shows the VirtualBox snapshot created after the domain controller setup was completed.

![Domain controller snapshot created](../screenshots/07%20-%20Domain%20Controller%20Snapshot%20Created.png)

## Notes

The reboot after domain controller promotion appeared to hang on the Restarting screen. After waiting, a normal ACPI shutdown did not respond, so the VM was powered off and restarted. On restart, Windows successfully continued applying computer settings and booted to the new domain login screen.

This snapshot was created before adding organizational units, users, groups, shared folders, Group Policy Objects, or client machines.
