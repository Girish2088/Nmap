# Nmap

## Overview

`Nmap` (Network Mapper) is an open-source network scanning tool used to discover live hosts, identify open ports, detect running services, and gather information about target systems. It is one of the most widely used reconnaissance tools in cybersecurity.

---

# Basic Syntax

```bash
nmap [options] <target>
```

Example:

```bash
sudo nmap -sS 10.10.10.10
```

---

# Target Specification

Scan a single host:

```bash
nmap 10.10.10.10
```

Scan multiple hosts:

```bash
nmap 10.10.10.10 10.10.10.20
```

Scan a subnet:

```bash
nmap 10.10.10.0/24
```

Scan using hostname:

```bash
nmap example.com
```

---

# Host Discovery

Discover live hosts only:

```bash
sudo nmap -sn TARGET
```

List targets without scanning:

```bash
sudo nmap -sL TARGET
```

---

# Port Scanning

### TCP SYN Scan (Recommended)

```bash
sudo nmap -sS TARGET
```

### TCP Connect Scan

```bash
nmap -sT TARGET
```

### UDP Scan

```bash
sudo nmap -sU TARGET
```

---

# Port Selection

Fast scan (Top 100 ports):

```bash
nmap -F TARGET
```

Specific port:

```bash
nmap -p 80 TARGET
```

Multiple ports:

```bash
nmap -p 22,80,443 TARGET
```

Port range:

```bash
nmap -p 1-1024 TARGET
```

All TCP ports:

```bash
nmap -p- TARGET
```

---

# Enumeration

Detect service versions:

```bash
sudo nmap -sV TARGET
```

Detect operating system:

```bash
sudo nmap -O TARGET
```

Aggressive scan:

```bash
sudo nmap -A TARGET
```

---

# Skip Host Discovery

Treat the host as online:

```bash
sudo nmap -Pn TARGET
```

Useful when ICMP (ping) is blocked.

---

# Timing Templates

| Option | Description |
|---------|-------------|
| `-T0` | Paranoid |
| `-T1` | Sneaky |
| `-T2` | Polite |
| `-T3` | Normal (Default) |
| `-T4` | Aggressive |
| `-T5` | Insane |

For labs and CTFs:

```bash
-T4
```

---

# Verbose Output

```bash
-v
```

More verbose:

```bash
-vv
```

Maximum verbose:

```bash
-vvv
```

Debug mode:

```bash
-d
```

Maximum debugging:

```bash
-d9
```

---

# Saving Scan Results

Normal output:

```bash
-oN scan.txt
```

XML:

```bash
-oX scan.xml
```

Grepable:

```bash
-oG scan.gnmap
```

All formats:

```bash
-oA initial
```

---

# Common Commands

Host discovery:

```bash
sudo nmap -sn 10.10.10.0/24
```

Basic SYN scan:

```bash
sudo nmap -sS TARGET
```

Scan all ports:

```bash
sudo nmap -sS -p- TARGET
```

Service detection:

```bash
sudo nmap -sS -sV TARGET
```

OS detection:

```bash
sudo nmap -sS -O TARGET
```

Full enumeration:

```bash
sudo nmap -sS -sV -O -T4 -v -oA scan TARGET
```

---

# Practical Workflow

```text
Target
   │
   ▼
Host Discovery
(-sn)
   │
   ▼
Port Scan
(-sS)
   │
   ▼
Scan All Ports
(-p-)
   │
   ▼
Service Detection
(-sV)
   │
   ▼
OS Detection
(-O)
   │
   ▼
Service Enumeration
(HTTP, SSH, FTP, SMB...)
```

---

# Understanding a Scan Command

Example:

```bash
sudo nmap -sS -sV -O -p- -T4 -v -oA initial 10.10.10.10
```

| Option | Purpose |
|---------|---------|
| `sudo` | Run with root privileges |
| `-sS` | TCP SYN scan |
| `-sV` | Detect service versions |
| `-O` | Detect operating system |
| `-p-` | Scan all TCP ports |
| `-T4` | Faster scan |
| `-v` | Show progress |
| `-oA initial` | Save output in all formats |
| `10.10.10.10` | Target IP |

---

# Command Cheat Sheet

| Option | Purpose |
|---------|---------|
| `-sn` | Host discovery only |
| `-sL` | List targets |
| `-sS` | TCP SYN scan |
| `-sT` | TCP Connect scan |
| `-sU` | UDP scan |
| `-F` | Fast scan |
| `-p` | Select ports |
| `-p-` | Scan all ports |
| `-sV` | Service version detection |
| `-O` | OS detection |
| `-A` | Aggressive scan |
| `-Pn` | Skip ping |
| `-T4` | Aggressive timing |
| `-v` | Verbose output |
| `-oN` | Save normal output |
| `-oX` | Save XML output |
| `-oG` | Save grepable output |
| `-oA` | Save all output formats |

---

# Key Takeaways

- Nmap is primarily used for reconnaissance.
- Start with host discovery before scanning ports.
- Use `-sS` for fast and stealthier TCP scans.
- Use `-p-` when you need to scan every TCP port.
- Combine `-sV` and `-O` to identify services and operating systems.
- Save scan results using `-oA` for future analysis.
