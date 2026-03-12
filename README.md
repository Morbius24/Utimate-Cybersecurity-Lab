# Utimate-Cybersecurity-Lab


[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![VMware](https://img.shields.io/badge/VMware-Workstation%20Pro-green)]()
[![pfSense](https://img.shields.io/badge/pfSense-2.6-blue)]()
[![Kali](https://img.shields.io/badge/Kali-Linux-blue)]()

## 🎯 Overview

This repository contains the complete configuration, scripts, and documentation for my enterprise-grade cybersecurity homelab, built following Gerrard O'Brien's "Ultimate Cybersecurity Lab" course on YouTube. This lab simulates a real-world corporate network environment for practicing penetration testing, red teaming, and defensive security techniques.

![Network Diagram] [(docs/architecture/network-diagram.png)]

## 🏗️ Lab Architecture

### Network Segmentation
| Segment | Subnet | Purpose | Key VMs |
|---------|--------|---------|---------|
| WAN | 192.168.2.0/24 | External connectivity | pfSense (WAN) |
| LAB Core | 10.0.2.0/24 | Management & Infrastructure | pfSense (LAN), DC-01, Kali |
| DMZ | 10.0.3.0/24 | Public-facing services | DVWA, Metasploitable |
| Clients | 10.0.4.0/24 | User workstations | WIN10-Client |
| Restricted | 10.0.5.0/24 | Sensitive data | SQL-Server |

### Virtual Machine Inventory
| VM Name | OS | IP Address | Purpose |
|---------|-----|------------|---------|
| pfSense | FreeBSD | 10.0.2.1 | Firewall/Router |
| DC-01 | Windows Server 2022 | 10.0.2.10 | Domain Controller |
| Kali | Kali Linux | 10.0.2.100 | Attack Platform |
| WIN10-Client | Windows 10 | 10.0.4.50 | Domain Workstation |
| DVWA | Ubuntu 20.04 | 10.0.3.10 | Vulnerable Web App |
| Metasploitable | Linux | 10.0.3.20 | Vulnerable Target |

## ✨ Features

- ✅ **Fully Isolated Environment** - Host-only networking ensures lab activities never leave your machine
- ✅ **Enterprise Network Design** - Segmented network with DMZ, internal, and restricted zones
- ✅ **Active Directory Domain** - Complete Windows domain with users, groups, and OUs
- ✅ **Professional Firewall** - pfSense with custom rules controlling inter-segment traffic
- ✅ **Attack Platform** - Kali Linux pre-configured with essential tools
- ✅ **Vulnerable Targets** - Multiple intentionally vulnerable systems for practice
- ✅ **Comprehensive Documentation** - Step-by-step guides and troubleshooting

## 🚀 Quick Start

### Prerequisites
- VMware Workstation Pro/Fusion (or VirtualBox)
- 16GB+ RAM
- 100GB+ free disk space
- ISOs: pfSense, Kali Linux, Windows Server 2022, Windows 10

### Basic Setup (1-2 Hours)
1. Clone this repository
2. Follow the setup guides in `/docs/setup-guides/` in order:
   - [01-pfsense-setup.md](docs/setup-guides/01-pfsense-setup.md)
   - [02-kali-setup.md](docs/setup-guides/02-kali-setup.md)
   - [03-windows-server-setup.md](docs/setup-guides/03-windows-server-setup.md)
   - [04-active-directory-config.md](docs/setup-guides/04-active-directory-config.md)
3. Use the scripts in `/scripts/` to automate configurations

## 📚 Learning Path

### Week 1-2: Foundation
- [ ] Set up pfSense and basic networking
- [ ] Install Kali Linux and verify connectivity
- [ ] Deploy Windows Server and promote to Domain Controller
- [ ] Create initial AD structure

### Week 3-4: Expansion
- [ ] Add network segmentation (DMZ, Clients, Restricted)
- [ ] Deploy Windows 10 client and join to domain
- [ ] Install vulnerable targets in DMZ
- [ ] Configure firewall rules

### Week 5-8: Practice
- [ ] Complete reconnaissance scenarios
- [ ] Practice exploitation techniques
- [ ] Execute lateral movement exercises
- [ ] Achieve domain dominance

## 🛠️ Automation Scripts

### Windows PowerShell Scripts
```powershell
# Create Organizational Units
.\scripts\windows\Create-OUs.ps1

# Bulk create users from CSV
.\scripts\windows\Create-ADUsers.ps1 -CSVPath .\scripts\windows\Bulk-User-Creation.csv

# Enable WinRM for remote management
.\scripts\windows\Enable-WinRM.ps1
