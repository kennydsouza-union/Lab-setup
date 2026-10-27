# Kali Linux Lab Setup

A documented Kali Linux environment for learning penetration testing, CTFs, and security fundamentals. This repo covers how the lab is built, what tools it includes, and how I use it.

![Kali Linux Setup](images/kali-screenshot.png)

## Table of Contents

- [Overview](#overview)
- [Environment](#environment)
- [Installation](#installation)
- [Post-Install Configuration](#post-install-configuration)
- [Tools](#tools)
- [Basic Workflow](#basic-workflow)
- [Practice Platforms](#practice-platforms)
- [Disclaimer](#disclaimer)

## Overview

I'm a second-year BCA Cyber Security student. This lab gives me a safe, isolated space to practice offensive security skills such as reconnaissance, web testing, forensics, and exploitation. I keep these notes so the setup is repeatable and so I can track what I learn.

## Environment

| Component | Details |
|---|---|
| OS | Kali Linux ___ |
| Install type | VirtualBox / VMware / Dual boot |
| RAM | ___ GB |
| Storage | ___ GB |
| CPU cores | ___ |
| Network mode | NAT / Bridged / Host-only |
| Host OS | Windows / Linux / macOS |

## Installation

1. Download Kali from the official site: https://www.kali.org/get-kali/
2. Verify the file integrity:
   ```bash
   sha256sum kali-linux-*.iso
   ```
   Compare the output with the checksum on the download page.
3. Create a new VM (or a bootable USB for dual boot) and run the installer.
4. Install the guest additions or VMware tools for better display and clipboard support.
5. Take a snapshot of the clean install.

## Post-Install Configuration

**Update the system**
```bash
sudo apt update && sudo apt full-upgrade -y
```

**Install common extras**
```bash
sudo apt install -y neofetch git curl wget python3-pip
```

**Networking**
- NAT: internet access for updates and tool downloads
- Host-only / internal: isolated network for local practice targets

**Hack The Box VPN**
```bash
sudo openvpn your-profile.ovpn
```

**Snapshots**
I take a snapshot after the clean install and again after tool setup, so I can restore a working state quickly.

## Tools

| Category | Tool | Purpose |
|---|---|---|
| Recon | Nmap | Port and service scanning |
| Recon | subfinder, httpx | Subdomain discovery and probing |
| Web | Burp Suite | Intercepting and testing web requests |
| Web | ffuf | Directory and parameter fuzzing |
| Web | sqlmap | SQL injection testing |
| Exploitation | Metasploit | Exploit framework |
| Network | Wireshark | Packet capture and analysis |
| Forensics | binwalk, exiftool, zsteg | File analysis and steganography |
| Passwords | John the Ripper, Hashcat | Hash cracking |
| Passwords | Hydra | Login brute-force testing |

## Basic Workflow

A typical lab session looks like this:

1. **Recon:** scan the target.
   ```bash
   nmap -sC -sV -oN scan.txt <target-ip>
   ```
2. **Enumerate:** check web content and services.
   ```bash
   ffuf -u http://<target-ip>/FUZZ -w /usr/share/wordlists/dirb/common.txt
   ```
3. **Analyze:** review results, identify weaknesses.
4. **Exploit:** test the finding in the lab only.
5. **Document:** write notes and a walkthrough.

## Practice Platforms

- [Hack The Box](https://www.hackthebox.com/): machines and challenges
- CTF competitions
- OWASP Juice Shop: intentionally vulnerable web app


## Disclaimer

This repository is for educational purposes only. All testing is done on my own lab machines or on platforms that explicitly allow it, such as Hack The Box and CTFs. Do not test systems without written permission.



