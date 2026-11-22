# Ubuntu Server Installation Using VirtualBox

**Date:** 22 November 2026  
**Project:** Home Lab Journey  
**Phase:** 1 - Virtualisation  
**Status:** Installation completed, system updates pending

## 1. Objective

The objective of this project was to create my first virtual Linux server using Oracle VirtualBox.

This project is part of my long-term goal of transitioning from a virtual home lab to dedicated physical infrastructure while developing practical skills in networking, Linux administration, virtualisation and cloud computing.

## 2. Hardware and Software

### Physical Computer

| Component | Specification |
|---|---|
| Processor | AMD Ryzen 7 9800X3D |
| CPU Cores | 8 |
| Logical Processors | 16 |
| RAM | 32GB |
| Storage | 2 NVMe SSDs |
| Operating System | Windows 11 |
| Virtualisation | Enabled |

### Virtual Machine

| Component | Configuration |
|---|---|
| Virtualisation Software | Oracle VirtualBox 7.2.22 |
| Virtual Machine Name | Ubuntu-Server-01 |
| Guest Operating System | Ubuntu Server 26.04.1 LTS |
| Allocated RAM | 4096MB |
| Virtual CPUs | Initially 2, changed to 1 |
| Virtual Hard Disk | 40GB |
| Network Adapter | NAT |
| IPv4 Address | 10.0.2.15 |
| SSH | OpenSSH Server installed |

## 3. Installation Process

I completed the following tasks:

1. Installed Oracle VirtualBox on Windows 11.
2. Downloaded the Ubuntu Server 26.04.1 LTS ISO.
3. Created a virtual machine named Ubuntu-Server-01.
4. Allocated virtual CPU, memory and disk resources.
5. Booted the virtual machine using the Ubuntu ISO.
6. Configured networking using DHCP and NAT.
7. Selected the default Australian Ubuntu package mirror.
8. Configured storage using LVM.
9. Created a Linux administrator account.
10. Installed OpenSSH Server.
11. Completed the Ubuntu Server installation.
12. Removed the installation ISO and booted from the virtual hard disk.
13. Successfully logged into Ubuntu.
14. Created a VirtualBox snapshot named Fresh-Ubuntu-Installation.

## 4. Problems Encountered

### Problem 1: Ubuntu Installer Freezing

During the initial boot, Ubuntu appeared to stop progressing at:

`Loading essential drivers...`

I attempted to pause and resume the virtual machine.

The installer eventually progressed to the language selection screen.

### Problem 2: CPU Soft Lockups

During the installation's security update stage, Ubuntu displayed warnings similar to:

`watchdog: BUG: soft lockup - CPU#0 stuck for 24s!`

I changed the virtual CPU allocation from two processors to one.

After restarting, Ubuntu successfully booted from the virtual hard disk and allowed me to log in.

This suggests a possible virtual CPU scheduling or compatibility issue, although the precise cause has not been confirmed.

### Problem 3: Installation ISO Booting Again

After restarting the virtual machine, the Ubuntu installer appeared again.

I learned that the virtual machine was still booting from its installation ISO.

After the ISO was disconnected, the virtual machine successfully started from its installed operating system.

## 5. Linux Commands Learned

I executed three commands to verify my Linux installation.

### Check Current User

```bash
whoami
```

Output:

```text
labadmin
```

### Check Hostname

```bash
hostname
```

Output:

```text
ubuntu-server-01
```

### Check Ubuntu Version

```bash
cat /etc/os-release
```

Result: Ubuntu 26.04.1 LTS.

## 6. Concepts Learned

**Virtualisation:** Running virtual computers using the resources of a physical computer.

**Host operating system:** Windows 11, which runs VirtualBox.

**Guest operating system:** Ubuntu Server, which runs inside the virtual machine.

**ISO image:** A file containing operating system installation media.

**DHCP:** Automatically provides IP configuration to network devices.

**NAT:** Allows the virtual machine to access external networks through the host computer.

**SSH:** Enables secure remote administration of Linux servers.

**LVM:** Provides flexible management of Linux storage.

**Snapshots:** Save a virtual machine's state so changes can be reversed.

## 7. Verification Results

- [x] VirtualBox installed
- [x] Ubuntu Server installed
- [x] Virtual networking configured
- [x] SSH Server installed
- [x] Linux administrator account created
- [x] Successful login
- [x] Linux commands executed successfully
- [x] Initial recovery snapshot created
- [ ] System updates installed
- [ ] SSH connection tested
- [ ] Network connectivity verified from the terminal

## 8. Next Steps

During my next home lab session, I plan to:

1. Start Ubuntu Server.
2. Refresh package information using `sudo apt update`.
3. Install available system and security updates.
4. Verify server stability.
5. Test network connectivity.
6. Begin learning Linux file management and administrative commands.

## 9. Reflection

Today I created and successfully accessed my first virtual Linux server.

I learned how virtual machines use physical computer resources and how to configure an operating system, virtual storage and networking.

The installation encountered several problems, especially CPU soft lockups. Troubleshooting these problems helped me understand the importance of checking logs, changing one configuration at a time and documenting the results.

This was my first practical milestone towards building a physical home lab.
