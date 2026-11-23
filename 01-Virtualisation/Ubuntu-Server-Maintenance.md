# Ubuntu Server Maintenance and Troubleshooting

**Date:** 23 November 2026  
**Project:** Home Lab Journey  
**Phase:** 1 - Virtualisation  
**Status:** Completed

## 1. Objective

The objective of this session was to learn basic Linux server maintenance, troubleshoot software repository errors, and successfully update my Ubuntu Server virtual machine.

This forms part of my long-term goal of building a physical, self-hosted family media server while developing practical skills in Linux administration, networking, virtualisation, and automation.

## 2. Environment

| Component | Configuration |
|---|---|
| Virtualisation Software | Oracle VirtualBox 7.2.22 |
| Operating System | Ubuntu Server 26.04.1 LTS |
| Virtual Machine | Ubuntu-Server-01 |
| Hostname | ubuntu-server-01 |
| Username | labadmin |
| Networking | NAT |
| IP Address | 10.0.2.15 |

## 3. Initial Server Update

I began by checking for available software updates using:

`sudo apt update`

The command attempted to retrieve package information from Ubuntu's repositories.

However, the update failed because Ubuntu was still referencing the installation CD-ROM.

**Error encountered:**

`E: The repository 'file:/cdrom resolute Release' no longer has a Release file.`

This prevented the package update process from completing successfully.

## 4. Troubleshooting the Repository Error

### Step 1: Identify the Repository

I searched the Ubuntu APT configuration directory for references to the installation CD-ROM.

**Command:**

`grep -Rni cdrom /etc/apt/`

**Result:**

`/etc/apt/sources.list.d/cdrom.sources:2:URIs: file:///cdrom`

The command identified the configuration file responsible for the error.

### Step 2: Disable the CD-ROM Repository

I moved the problematic repository configuration file to a backup location.

**Command:**

`sudo mv /etc/apt/sources.list.d/cdrom.sources /etc/apt/cdrom.sources.backup`

This preserved the original configuration while removing the CD-ROM repository from the active APT sources directory.

### Step 3: Verify the Solution

I ran the package update command again.

`sudo apt update`

**Result:**

- Ubuntu successfully contacted the online repositories.
- The CD-ROM repository error disappeared.
- Ubuntu identified 50 available package upgrades.

The repository issue was successfully resolved.

## 5. Installing Software Updates

After resolving the repository error, I upgraded the installed packages.

**Command:**

`sudo apt upgrade`

Ubuntu downloaded and installed the available package upgrades.

The terminal displayed package configuration messages, service restart information, and system maintenance output.

The command completed and returned to the terminal prompt.

## 6. Restarting Ubuntu Server

Following the upgrade, I restarted the virtual machine using:

`sudo reboot`

Ubuntu restarted successfully.

I logged back into the server using my existing administrator account.

After restarting, the system reported Linux kernel version `7.0.0-44-generic`.

## 7. Final Verification

I performed one final package update check.

**Command:**

`sudo apt update`

**Result:**

`All packages are up to date.`

This confirmed the package lists refreshed successfully and no additional package upgrades were available.

## 8. Commands Learned

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh available package information |
| `sudo apt upgrade` | Install available package upgrades |
| `grep -Rni` | Search files recursively for matching text |
| `sudo mv` | Move or rename files using administrator permissions |
| `sudo reboot` | Restart the operating system |
| `clear` | Clear the terminal display |

## 9. Challenges and Lessons Learned

During this session, I encountered my first Linux package repository error.

I learned how to investigate the error message, identify the relevant configuration file, and resolve the problem without reinstalling Ubuntu.

I also gained experience using the Linux terminal and learned how command syntax and spaces affect command execution.

**Key lessons:**

- Repository configuration errors can prevent software updates.
- Linux commands require accurate syntax.
- Configuration files can be backed up before making changes.
- System upgrades should be followed by verification.
- Terminal output helps identify and troubleshoot problems.

## 10. Outcome

Successfully completed Ubuntu Server maintenance and resolved the package repository error.

The Ubuntu Server virtual machine is operational and up to date.

## 11. Next Steps

- Learn essential Linux terminal commands.
- Configure SSH remote administration.
- Understand IP addresses and networking.
- Practise Linux server monitoring.
- Begin developing Python automation scripts.
- Progress towards deploying a self-hosted media server on physical hardware.
