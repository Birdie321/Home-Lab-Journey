# Day 1: Ubuntu Server Installation Using VirtualBox

**Date:** 22 November 2026  
**Project:** Home Lab Journey  
**Phase:** Virtualisation  
**Status:** Completed

## 1. Objective

The objective of this project was to create my first virtual Linux server using Oracle VirtualBox.

This project is part of my long-term goal of transitioning from a virtual home lab to dedicated physical infrastructure while developing practical skills in networking, Linux administration, virtualisation and cloud computing.

## 2. Environment

### Physical Computer (Host)

| Component | Specification |
|---|---|
| Processor | AMD Ryzen 7 9800X3D |
| CPU Cores | 8 |
| CPU Threads | 16 |
| RAM | 32 GB |
| Storage | 2 NVMe SSDs |
| Operating System | Windows 11 |
| Virtualisation | Enabled |

### Virtual Machine (Guest)

| Component | Specification |
|---|---|
| Virtualisation Software | Oracle VirtualBox 7.2.22 |
| Virtual Machine Name | Ubuntu-Server-01 |
| Guest Operating System | Ubuntu Server 26.04.1 LTS |
| Allocated RAM | 4096 MB |
| Virtual CPUs | Initially 2, changed to 1 |
| Virtual Hard Disk | 40 GB |
| Network Adapter | NAT |
| IPv4 Address | 10.0.2.15 |
| SSH | OpenSSH Server installed |

## 3. Tasks Performed

- Installed Oracle VirtualBox on Windows 11.
- Downloaded the Ubuntu Server 26.04.1 LTS ISO.
- Created a virtual machine named Ubuntu-Server-01.
- Allocated virtual CPU, memory and disk resources.
- Booted the virtual machine using the Ubuntu ISO.
- Configured networking using DHCP and NAT.
- Selected the default Australian Ubuntu package mirror.
- Configured storage using LVM.
- Created a Linux administrator account.
- Installed OpenSSH Server.
- Completed the Ubuntu Server installation.
- Removed the installation ISO and booted from the virtual hard disk.
- Successfully logged into Ubuntu.
- Created a VirtualBox snapshot named Fresh-Ubuntu-Installation.

## 4. Troubleshooting

### Issue 1: Ubuntu Installer Appeared to Freeze

During the initial boot, Ubuntu appeared to stop progressing at:

`Loading essential drivers...`

### Resolution

I attempted to pause and resume the virtual machine.

The installer eventually progressed to the language selection screen.

### Issue 2: CPU Soft Lockup Warnings

During the installation's security update stage, Ubuntu displayed warnings similar to:

`watchdog: BUG: soft lockup - CPU#0 stuck for 24s!`

### Resolution

I changed the virtual CPU allocation from two processors to one.

After restarting, Ubuntu successfully booted from the virtual hard disk and allowed me to log in.

This suggests a possible virtual CPU scheduling or compatibility issue, although the precise cause has not been confirmed.

### Issue 3: Installation ISO Booted Again

After restarting the virtual machine, the Ubuntu installer appeared again.

### Resolution

I learned that the virtual machine was still booting from its installation ISO.

After the ISO was disconnected, the virtual machine successfully started from its installed operating system.

## 5. Verification and Results

The checks below record the status at the end of **Day 1 (22 November 2026)**. Items marked pending were not yet completed during this session.

| Verification | Result |
|---|---|
| VirtualBox installed | Successful |
| Ubuntu Server installed | Successful |
| Virtual networking configured | Successful |
| SSH Server installed | Successful |
| Linux administrator account created | Successful |
| Successful login | Successful |
| Linux commands executed successfully | Successful |
| Initial recovery snapshot created | Successful |
| System updates installed | Pending |
| SSH connection tested | Pending |
| Network connectivity verified from the terminal | Pending |

**Follow-up:** Package updates were completed and verified on Day 2, 23 November 2026.

## 6. Commands Learned

| Command | Purpose |
|---|---|
| `whoami` | Display the current user |
| `hostname` | Display the hostname |
| `cat /etc/os-release` | Display operating system version information |

**Verified output:** Current user `labadmin`; hostname `ubuntu-server-01`; Ubuntu 26.04.1 LTS.

## 7. Challenges and Lessons Learned

**Virtualisation:** Running virtual computers using the resources of a physical computer.

**Host operating system:** Windows 11, which runs VirtualBox.

**Guest operating system:** Ubuntu Server, which runs inside the virtual machine.

**ISO image:** A file containing operating system installation media.

**DHCP:** Automatically provides IP configuration to network devices.

**NAT:** Allows the virtual machine to access external networks through the host computer.

**SSH:** Enables secure remote administration of Linux servers.

**LVM:** Provides flexible management of Linux storage.

**Snapshots:** Save a virtual machine's state so changes can be reversed.

### Reflection

Today I created and successfully accessed my first virtual Linux server.

I learned how virtual machines use physical computer resources and how to configure an operating system, virtual storage and networking.

The installation encountered several problems, especially CPU soft lockups. Troubleshooting these problems helped me understand the importance of checking logs, changing one configuration at a time and documenting the results.

This was my first practical milestone towards building a physical home lab.

## 8. Outcome

Successfully installed Ubuntu Server 26.04.1 LTS in VirtualBox, configured NAT networking and LVM storage, created the `labadmin` account, installed OpenSSH Server, and logged into the VM.

Created the `Fresh-Ubuntu-Installation` snapshot as a recovery point. The installer and boot issues were documented, and package upgrades remained a task for Day 2.

## 9. Next Steps

*Planned at the end of this session.*

- [ ] Start Ubuntu Server.
- [ ] Refresh package information using `sudo apt update`.
- [ ] Install available system and security updates.
- [ ] Verify server stability.
- [ ] Test network connectivity.
- [ ] Begin learning Linux file management and administrative commands.
