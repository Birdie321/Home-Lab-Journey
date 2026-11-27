# Day 2: Ubuntu Server Maintenance and Troubleshooting

**Date:** 23 November 2026  
**Project:** Home Lab Journey  
**Phase:** 1 - Virtualisation  
**Status:** Completed
## 1. Objective

The objective of this session was to learn Linux server maintenance, troubleshoot software repository errors, and successfully update my Ubuntu Server virtual machine.

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

## 3. Tasks Performed

### 3.1 Check for Package Updates

I began by checking for available software updates using:

`sudo apt update`

The command attempted to retrieve package information from Ubuntu's repositories.

However, the update failed because Ubuntu was still referencing the installation CD-ROM.

**Error encountered:**

`E: The repository 'file:/cdrom resolute Release' no longer has a Release file.`

This prevented the package update process from completing successfully.

### 3.2 Install Available Upgrades

After resolving the repository error, I upgraded the installed packages.

**Command:**

`sudo apt upgrade`

Ubuntu downloaded and installed the available package upgrades.

The terminal displayed package configuration messages, service restart information, and system maintenance output.

The command completed and returned to the terminal prompt.

### 3.3 Restart Ubuntu Server

Following the upgrade, I restarted the virtual machine using:

`sudo reboot`

Ubuntu restarted successfully.

I logged back into the server using my existing administrator account.

After restarting, the system reported Linux kernel version `7.0.0-44-generic`.

### 3.4 Verify Package Updates

I performed one final package update check.

**Command:**

`sudo apt update`

**Result:**

`All packages are up to date.`

This confirmed the package lists refreshed successfully and no additional package upgrades were available.

### 3.5 Inspect System Information and Performance

Checked the operating system and kernel:

```bash
hostnamectl
```

Monitored memory, CPU usage and running processes:

```bash
free -h
top
```

Exited `top` using **Q**.

### 3.6 Examine Disk Space and LVM

```bash
df -h
lsblk
sudo vgs
```

The virtual disk was **40 GB**, the root logical volume **19 GB**, and the `ubuntu-vg` volume group reported **19 GB free**. No storage changes were made.

### 3.7 Practise Linux File and Directory Management

Found the working directory and inspected hidden files:

```bash
pwd
ls -la
```

Created a project directory:

```bash
mkdir homelab-projects
cd homelab-projects
pwd
```

Created a text file, wrote a first line, and appended a second line:

```bash
touch notes.txt
echo "My first Ubuntu Server home lab" > notes.txt
echo "Learning Linux server administration" >> notes.txt
cat notes.txt
```

Verified the file contained both lines:

```text
My first Ubuntu Server home lab
Learning Linux server administration
```

Copied, renamed and organised a backup:

```bash
cp notes.txt notes-backup.txt
mv notes-backup.txt notes-original.txt
mkdir backups
mv notes-original.txt backups/
ls -l backups/
```

Final directory structure:

```text
/home/labadmin/
└── homelab-projects/
    ├── notes.txt
    └── backups/
        └── notes-original.txt
```

### 3.8 Inspect and Change File Permissions

Inspected the file metadata:

```bash
stat notes.txt
```

The file was **69 bytes**, owned by `labadmin`, with initial permissions `0664` (`-rw-rw-r--`).

Restricted access to the file owner and verified the change:

```bash
chmod 600 notes.txt
ls -l notes.txt
```

The reported permissions changed to `-rw-------`.

## 4. Troubleshooting

### 4.1 Identify the CD-ROM Repository

I searched the Ubuntu APT configuration directory for references to the installation CD-ROM.

**Command:**

`grep -Rni cdrom /etc/apt/`

**Result:**

`/etc/apt/sources.list.d/cdrom.sources:2:URIs: file:///cdrom`

The command identified the configuration file responsible for the error.

### 4.2 Disable the CD-ROM Repository

I moved the problematic repository configuration file to a backup location.

**Command:**

`sudo mv /etc/apt/sources.list.d/cdrom.sources /etc/apt/cdrom.sources.backup`

This preserved the original configuration while removing the CD-ROM repository from the active APT sources directory.

### 4.3 Verify the Fix

I ran the package update command again.

`sudo apt update`

**Result:**

- Ubuntu successfully contacted the online repositories.
- The CD-ROM repository error disappeared.
- Ubuntu identified 50 available package upgrades.

The repository issue was successfully resolved.

### 4.4 Command Entry and VirtualBox Window Size

During the troubleshooting exercise, incorrect spacing in a `mv` command produced an error. The terminal prompt was also partially hidden because the VirtualBox window was not wide enough.

After expanding the window and correcting the command, file operations worked as expected.

## 5. Verification and Results

### 5.1 Package Maintenance

| Check | Verified result |
|---|---|
| APT CD-ROM repository error | Resolved |
| Available upgrades after repository fix | 50 |
| `sudo apt upgrade` | Finished successfully |
| Ubuntu reboot and login | Successful |
| Linux kernel after reboot | `7.0.0-44-generic` |
| Final `sudo apt update` | `All packages are up to date.` |

### 5.2 Operating System and Resource Monitoring

| Measurement | Observed result |
|---|---|
| Operating system | Ubuntu Server 26.04.1 LTS |
| Hostname | `ubuntu-server-01` |
| Architecture | x86-64 |
| Virtualisation | Oracle VirtualBox |
| Total RAM | 3.3 GiB |
| RAM used | Approximately 474 MiB |
| RAM available | Approximately 2.9 GiB |
| Swap used | 0 B |
| CPU idle during `top` observation | 100% |
| Tasks | 99 total; 1 running; 98 sleeping |
| Zombie processes | 0 |

Resource figures were measured during the session and can change over time.

### 5.3 Filesystem and LVM Storage

| Measurement | Observed result |
|---|---|
| Virtual disk (`sda`) | 40 GB |
| Boot partition (`sda2`) | 2 GB |
| LVM partition (`sda3`) | 38 GB |
| Root logical volume | 19 GB |
| Root filesystem used | 7.2 GB |
| Root filesystem available | 11 GB |
| Root filesystem usage | 41% |
| Volume group (`ubuntu-vg`) | About 38 GB |
| Free capacity in volume group | 19 GB |

### 5.4 File Management and Permissions

- [x] Created and entered `~/homelab-projects`.
- [x] Created `notes.txt` and wrote two lines of text.
- [x] Verified `>` overwrites content while `>>` appends.
- [x] Copied, renamed and moved a backup into `backups/`.
- [x] Confirmed original file contents remained in `notes.txt`.
- [x] Inspected file ownership and permissions using `stat`.
- [x] Changed `notes.txt` permissions from `0664` to `0600`.

## 6. Commands Learned

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh package information |
| `sudo apt upgrade` | Install available package upgrades |
| `grep -Rni cdrom /etc/apt/` | Find CD-ROM repository references |
| `sudo mv` | Move system files with administrator privileges |
| `sudo reboot` | Restart Ubuntu Server |
| `clear` | Clear the terminal display |
| `hostnamectl` | Inspect system identity and operating system |
| `free -h` | Check RAM and swap usage |
| `top` | Monitor running processes and CPU usage |
| `df -h` | Show filesystem capacity and usage |
| `lsblk` | List disks, partitions and logical volumes |
| `sudo vgs` | Inspect LVM volume group size and free capacity |
| `pwd` | Show the current directory |
| `ls -la` | List files, including hidden files and permission details |
| `mkdir` | Create a directory |
| `cd` | Change directories |
| `touch` | Create an empty file |
| `echo` | Output text |
| `>` | Write command output to a file, replacing existing text |
| `>>` | Append command output to a file |
| `cat` | Display file contents |
| `cp` | Copy a file |
| `mv` | Move or rename a file |
| `stat` | Inspect file details and permissions |
| `chmod 600` | Allow only the owner to read and write a file |

## 7. Challenges and Lessons Learned

During this session, I encountered my first Linux package repository error.

I learned how to investigate the error message, identify the relevant configuration file, and resolve the problem without reinstalling Ubuntu.

I also gained experience using the Linux terminal and learned how command syntax and spaces affect command execution.

**Key lessons:**

- Repository configuration errors can prevent software updates.
- Linux commands require accurate syntax.
- Configuration files can be backed up before making changes.
- System upgrades should be followed by verification.
- Terminal output helps identify and troubleshoot problems.

- I learned to inspect a Linux server with `hostnamectl`, `free -h`, `top`, `df -h`, `lsblk` and `vgs`.
- The 40 GB virtual disk and 19 GB root logical volume have different sizes because LVM manages allocation.
- I practised organizing directories, backing up files and using `>` versus `>>`.
- I learned how permissions such as `0664` and `0600` control file access.

## 8. Outcome

Successfully completed Ubuntu Server maintenance and resolved the package repository error.

The Ubuntu Server virtual machine is operational and up to date.

Also completed the first Linux administration exercises: inspected system resources, investigated LVM, created and organised practice files, and changed file permissions to restrict access.

## 9. Next Steps

1. Inspect Linux network interfaces and learn IP addressing.
2. Confirm OpenSSH is running.
3. Configure VirtualBox NAT port forwarding for SSH.
4. Connect to Ubuntu Server from Windows PowerShell.
5. Continue practising Linux administration and begin Python monitoring automation.
6. Test configurations in VirtualBox before installing Ubuntu Server fresh on the Acer laptop.

**Documentation workflow:** Record verified results throughout the session and update GitHub at the end.
