# Windows Server VM Setup

## Lab Machine

- VM name in VirtualBox: LittleBuilds-Server01
- Server computer name: LB-SRV-DC01
- Operating system: Windows Server 2022 Standard Evaluation
- Install type: Desktop Experience
- Virtualization platform: Oracle VirtualBox

## Virtual Hardware

- Memory: 4096 MB
- CPUs: 2
- Virtual hard disk: 80 GB VDI, dynamically allocated
- Network adapter: NAT
- Display memory: 128 MB
- Guest Additions: Installed

## Initial Configuration Completed

- Installed Windows Server 2022 Standard Evaluation with Desktop Experience.
- Created the built-in Administrator password.
- Enabled network discovery when prompted.
- Installed VirtualBox Guest Additions.
- Enabled shared clipboard in VirtualBox settings.
- Renamed the server to `LB-SRV-DC01`.

## Snapshot

Snapshot created after clean installation and initial configuration:

`01 - Clean Install - Renamed Server`

## Notes

This snapshot was created before installing any server roles. It provides a clean rollback point before configuring Active Directory Domain Services.

## Screenshots

![Clean install and renamed server](../screenshots/01%20-%20Clean%20Install%20-%20Renamed%20Server.png)

![VirtualBox VM configuration](../screenshots/02%20-%20VirtualBox%20VM%20Configuration.png)

![Baseline snapshot created](../screenshots/03%20-%20Baseline%20Snapshot%20Created.png)
