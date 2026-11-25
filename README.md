# Home Lab Journey

## Project Overview

This repository documents my journey from building a virtual home lab to developing dedicated physical IT infrastructure.

My goal is to develop practical technical skills in preparation for a Bachelor of Information and Communications Technology, majoring in Networking and Cloud Computing.

The current project focuses on deploying a self-hosted family media server using repurposed hardware, Linux, secure networking and remote administration.

## Learning Objectives

- Linux administration
- Computer networking
- Virtualisation
- Server administration
- Python automation
- Cybersecurity
- Cloud computing
- Infrastructure troubleshooting
- Technical documentation

## Current Hardware

### Desktop Workstation

| Component | Specification |
|---|---|
| Processor | AMD Ryzen 7 9800X3D |
| CPU Cores | 8 |
| CPU Threads | 16 |
| RAM | 32GB |
| Storage | 2 NVMe SSDs |
| Host OS | Windows 11 |
| Virtualisation | Enabled |

### Physical Server

| Component | Specification |
|---|---|
| Laptop | Acer Aspire S5-371T |
| Processor | Intel Core i7-6500U |
| CPU Cores | 2 |
| CPU Threads | 4 |
| RAM | 8GB |
| Storage | Samsung 512GB SSD |
| Operating System | Ubuntu Server 24.04.5 LTS |
| Hostname | media-server |
| Firmware | UEFI |
| Secure Boot | Enabled |

## Project Roadmap

- [x] Phase 1: Virtual Home Lab
- [x] Phase 2: Physical Server Installation
- [ ] Phase 3: Networking Infrastructure
- [ ] Phase 4: Remote Server Administration
- [ ] Phase 5: Security Hardening
- [ ] Phase 6: Headless Server Configuration
- [ ] Phase 7: Self-Hosted Media Server
- [ ] Phase 8: Secure Remote Access with Tailscale
- [ ] Phase 9: Python Automation
- [ ] Phase 10: Cloud Infrastructure

## Project Documentation

### 01 - Virtualisation

| Session | Documentation | Status |
|---|---|---|
| Day 1 | [Ubuntu Server Installation](01-Virtualisation/Ubuntu-Server-Installation.md) | Completed |
| Day 2 | [Ubuntu Server Maintenance](01-Virtualisation/Ubuntu-Server-Maintenance.md) | Completed |

### 02 - Physical Server Deployment

| Session | Documentation | Status |
|---|---|---|
| Day 3 | [Physical Server Installation and Troubleshooting](02-Physical-Server-Deployment/Physical-Server-Installation.md) | Completed |

## Progress Log

### 22 November 2026 - Day 1

- Assessed existing computer hardware.
- Confirmed hardware virtualisation support.
- Installed Oracle VirtualBox 7.2.22.
- Created the GitHub repository.
- Installed Ubuntu Server in a virtual machine.

### 23 November 2026 - Day 2

- Continued developing Linux administration skills.
- Performed Ubuntu Server maintenance exercises.
- Updated project documentation.

### 25 November 2026 - Day 3

- Diagnosed SQUASHFS and input/output errors.
- Verified Ubuntu Server ISO integrity using SHA256.
- Created replacement bootable installation media.
- Installed Ubuntu Server on physical hardware.
- Configured SSD partitions.
- Installed OpenSSH Server.
- Resolved a UEFI bootloader registration issue.
- Retained Secure Boot.
- Verified successful authentication and automatic boot.
- Documented troubleshooting with photographic evidence.

## Technical Skills Developed

| Skill | Practical Application |
|---|---|
| Virtualisation | VirtualBox and virtual machines |
| Linux Administration | Ubuntu Server installation and maintenance |
| Storage Management | Disk partitioning and file systems |
| File Integrity | SHA256 checksum verification |
| Firmware Configuration | BIOS and UEFI configuration |
| Bootloader Management | Manual EFI bootloader registration |
| Technical Troubleshooting | Kernel log analysis and fault diagnosis |
| Version Control | GitHub documentation and commit history |

## Current Milestone

Physical Ubuntu Server installation completed successfully.

The next milestone is establishing Ethernet connectivity and secure remote administration through SSH.

## Learning Approach

This project involves independent practical exercises, technical research and AI-assisted guidance.

I perform configurations, execute commands, investigate errors and verify results on virtual and physical infrastructure.

## Project Status

**In Progress**

The long-term objective is to develop a secure, reliable and remotely accessible self-hosted media server while building practical networking and infrastructure administration skills.
