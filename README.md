# MHZ_C1F-VulnHub-Penetration-Testing
End-to-end penetration testing walkthrough of the MHZ_C1F VulnHub machine demonstrating reconnaissance, web enumeration, credential discovery, steganography analysis, Linux privilege escalation, and root compromise.

## Overview 

This repository documents the successful compromise of the **MHZ_C1F** vulnerable virtual machine from VulnHub.

The objective of this lab was to perform a complete penetration testing assessment by discovering vulnerabilities, exploiting exposed services, performing privilege escalation, and obtaining root access.

> **Platform:** VulnHub
>
> **Difficulty:** Beginner to Intermediate
>
> **Attack Machine:** Kali Linux
>
> **Target Machine:** MHZ_C1F Ubuntu VM
>
> **Environment:** VirtualBox (Host-Only Network)


# Objective

Solve the lab using Penetration Testing tools.


# Lab Methodology

```
Reconnaissance
      │
      ▼
Host Discovery
      │
      ▼
Port Scanning
      │
      ▼
Service Enumeration
      │
      ▼
Web Enumeration
      │
      ▼
Credential Discovery
      │
      ▼
SSH Access
      │
      ▼
Image Analysis
      │
      ▼
Steganography
      │
      ▼
Privilege Escalation
      │
      ▼
Root Access
```


# Attack Workflow

## Phase 1 — Network Discovery

- Identified target machine using ARP discovery.
- Verified active hosts inside the local subnet.

Tools:

- ip
- netdiscover

## Phase 2 — Port Scanning

Performed a complete TCP scan to discover all exposed services.

Discovered:

- SSH
- HTTP

Tools:

- Nmap

## Phase 3 — Service Enumeration

Collected service versions and scripts.

Investigated:

- SSH Version
- Apache Web Server

Used:

- Nmap NSE
- Searchsploit

## Phase 4 — Web Enumeration

Performed manual and automated web enumeration.

Checked:

- robots.txt
- hidden files
- web directories

Used:

- Browser
- curl
- Nikto

Nikto revealed a hidden file:

- notes.txt

## Phase 5 — Initial Access

The notes file referenced another file containing credentials.

Successfully authenticated using SSH.

Tools:

- SSH

## Phase 6 — Local Enumeration

Enumerated the user's home directory.

Discovered:

- Paintings directory
- JPEG files

Transferred files to Kali for analysis.

Tools:

- SCP

## Phase 7 — Steganography Analysis

Each image was analyzed using Steghide.

One image contained an embedded text file with another set of credentials.

Tools:

- Steghide

## Phase 8 — Privilege Escalation

Logged into the second user account.

Checked sudo permissions.

The user possessed unrestricted sudo privileges.

Escalated to root using:

sudo /bin/bash

Successfully obtained root access.


# Tools Used

- Kali Linux
- VirtualBox
- Nmap
- Netdiscover
- Searchsploit
- Nikto
- curl
- SSH
- SCP
- Steghide
- Linux Commands


# Skills Demonstrated

- Network Reconnaissance
- Host Discovery
- Port Scanning
- Service Enumeration
- Web Enumeration
- Credential Discovery
- Linux Enumeration
- SSH Authentication
- Secure File Transfer
- Steganography Analysis
- Privilege Escalation
- Root Compromise
- Penetration Testing Methodology
- Vulnerability Assessment


# Learning Outcomes

This lab helped reinforce several real-world penetration testing concepts:

- Understanding the complete penetration testing lifecycle
- Identifying exposed services using Nmap
- Enumerating web servers effectively
- Discovering hidden resources
- Using automated scanners responsibly
- Extracting embedded information from images
- Performing Linux privilege escalation
- Working with SSH authentication
- Investigating Linux file systems
- Chaining multiple vulnerabilities together
- Thinking like an attacker during post-exploitation


# MITRE ATT&CK Mapping

| Technique | Description |
|------------|-------------|
| T1595 | Active Scanning |
| T1046 | Network Service Discovery |
| T1083 | File and Directory Discovery |
| T1005 | Data from Local System |
| T1021.004 | SSH |
| T1003 | Credential Discovery |
| T1548 | Abuse Elevation Control Mechanism |
| T1068 | Privilege Escalation |


# Screenshots

Include screenshots of:

- Network discovery
- Nmap scan
- Nikto scan
- SSH login
- Steghide extraction
- Sudo permissions
- Root shell


# Disclaimer

This project was performed inside a controlled lab environment using an intentionally vulnerable virtual machine from VulnHub.

The techniques demonstrated are intended solely for cybersecurity education, penetration testing practice, and defensive security research.
