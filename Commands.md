# Nmap Commands

This file contains the most commonly used Nmap commands for host discovery, port scanning, service enumeration, and result saving.

---

# Basic Syntax

```bash
nmap [options] <target>
```

Example:

```bash
nmap 192.168.1.10
```

---

# Target Specification

## Scan a Single Host

```bash
nmap 192.168.1.10
```

---

## Scan Multiple Hosts

```bash
nmap 192.168.1.10 192.168.1.20
```

---

## Scan a Subnet

```bash
nmap 192.168.1.0/24
```

---

## Scan a Hostname

```bash
nmap example.com
```

---

# Host Discovery

## Discover Live Hosts

```bash
sudo nmap -sn TARGET
```

Example:

```bash
sudo nmap -sn 192.168.1.0/24
```

---

## List Targets Only

```bash
sudo nmap -sL TARGET
```

---

## Skip Host Discovery (Treat Host as Online)

```bash
sudo nmap -Pn TARGET
```

Useful when ICMP (Ping) is blocked.

---

# Port Scanning

## Default Scan

```bash
nmap TARGET
```

---

## TCP SYN Scan (Recommended)

```bash
sudo nmap -sS TARGET
```

---

## TCP Connect Scan

```bash
nmap -sT TARGET
```

---

## UDP Scan

```bash
sudo nmap -sU TARGET
```

---

# Port Selection

## Fast Scan (Top 100 Ports)

```bash
nmap -F TARGET
```

---

## Scan a Specific Port

```bash
nmap -p 80 TARGET
```

---

## Scan Multiple Ports

```bash
nmap -p 22,80,443 TARGET
```

---

## Scan a Port Range

```bash
nmap -p 1-1024 TARGET
```

---

## Scan All TCP Ports

```bash
nmap -p- TARGET
```

---

# Enumeration

## Detect Service Versions

```bash
sudo nmap -sV TARGET
```

---

## Detect Operating System

```bash
sudo nmap -O TARGET
```

---

## Aggressive Scan

Includes:

- OS Detection
- Version Detection
- Default NSE Scripts
- Traceroute

```bash
sudo nmap -A TARGET
```

---

# Timing Templates

## Paranoid

```bash
-T0
```

---

## Sneaky

```bash
-T1
```

---

## Polite

```bash
-T2
```

---

## Normal (Default)

```bash
-T3
```

---

## Aggressive (Recommended for Labs)

```bash
-T4
```

---

## Insane

```bash
-T5
```

---

# Verbose Output

Verbose

```bash
-v
```

More Verbose

```bash
-vv
```

Maximum Verbose

```bash
-vvv
```

---

# Debug Mode

```bash
-d
```

Maximum Debugging

```bash
-d9
```

---

# Save Scan Results

## Normal Output

```bash
-oN scan.txt
```

---

## XML Output

```bash
-oX scan.xml
```

---

## Grepable Output

```bash
-oG scan.gnmap
```

---

## Save in All Formats

```bash
-oA initial
```

---

# Common Commands

## Host Discovery

```bash
sudo nmap -sn 192.168.1.0/24
```

---

## Basic SYN Scan

```bash
sudo nmap -sS TARGET
```

---

## Scan All Ports

```bash
sudo nmap -sS -p- TARGET
```

---

## Service Version Detection

```bash
sudo nmap -sS -sV TARGET
```

---

## OS Detection

```bash
sudo nmap -sS -O TARGET
```

---

## Full Enumeration

```bash
sudo nmap -sS -sV -O -T4 -v -oA scan TARGET
```

---

# Understanding a Scan Command

Example:

```bash
sudo nmap -sS -sV -O -p- -T4 -v -oA initial 192.168.1.10
```

| Option | Purpose |
|---------|---------|
| `sudo` | Run with root privileges |
| `-sS` | TCP SYN Scan |
| `-sV` | Detect service versions |
| `-O` | Detect operating system |
| `-p-` | Scan all TCP ports |
| `-T4` | Faster timing |
| `-v` | Show scan progress |
| `-oA initial` | Save output in all formats |
| `192.168.1.10` | Target IP |

---

# Notes

- `-sS` is the most commonly used TCP scan.
- Use `-Pn` when the host blocks ICMP (Ping).
- Use `-p-` to scan all 65535 TCP ports.
- `-sV` identifies service versions.
- `-O` attempts to detect the operating system.
- `-A` performs aggressive enumeration.
- `-oA` saves scan results for future analysis.
