# Nmap Cheat Sheet

---

# Basic Syntax

```bash
nmap [options] <target>
```

---

# Target Specification

Single Host

```bash
nmap 192.168.1.10
```

Multiple Hosts

```bash
nmap 192.168.1.10 192.168.1.20
```

Subnet

```bash
nmap 192.168.1.0/24
```

Hostname

```bash
nmap example.com
```

---

# Host Discovery

Discover Live Hosts

```bash
sudo nmap -sn TARGET
```

List Targets Only

```bash
sudo nmap -sL TARGET
```

Skip Host Discovery

```bash
sudo nmap -Pn TARGET
```

---

# Port Scanning

Default Scan

```bash
nmap TARGET
```

TCP SYN Scan

```bash
sudo nmap -sS TARGET
```

TCP Connect Scan

```bash
nmap -sT TARGET
```

UDP Scan

```bash
sudo nmap -sU TARGET
```

---

# Port Selection

Fast Scan (Top 100 Ports)

```bash
nmap -F TARGET
```

Specific Port

```bash
nmap -p 80 TARGET
```

Multiple Ports

```bash
nmap -p 22,80,443 TARGET
```

Port Range

```bash
nmap -p 1-1024 TARGET
```

All TCP Ports

```bash
nmap -p- TARGET
```

---

# Enumeration

Service Version Detection

```bash
sudo nmap -sV TARGET
```

Operating System Detection

```bash
sudo nmap -O TARGET
```

Aggressive Scan

```bash
sudo nmap -A TARGET
```

---

# Timing Templates

```text
-T0   Paranoid
-T1   Sneaky
-T2   Polite
-T3   Normal (Default)
-T4   Aggressive
-T5   Insane
```

---

# Verbose & Debug

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

Debug

```bash
-d
```

Maximum Debug

```bash
-d9
```

---

# Save Results

Normal Output

```bash
-oN scan.txt
```

XML Output

```bash
-oX scan.xml
```

Grepable Output

```bash
-oG scan.gnmap
```

All Formats

```bash
-oA scan
```

---

# Most Used Commands

Basic Scan

```bash
nmap TARGET
```

Host Discovery

```bash
sudo nmap -sn TARGET
```

TCP SYN Scan

```bash
sudo nmap -sS TARGET
```

Scan All Ports

```bash
sudo nmap -p- TARGET
```

Service Detection

```bash
sudo nmap -sV TARGET
```

OS Detection

```bash
sudo nmap -O TARGET
```

Aggressive Scan

```bash
sudo nmap -A TARGET
```

Full Enumeration

```bash
sudo nmap -sS -sV -O -p- -T4 -v -oA scan TARGET
```

---

# Typical Workflow

```text
Target
   │
   ▼
Host Discovery (-sn)
   │
   ▼
Port Scan (-sS)
   │
   ▼
Scan All Ports (-p-)
   │
   ▼
Service Detection (-sV)
   │
   ▼
OS Detection (-O)
   │
   ▼
Further Enumeration
```

---

# Memory Hook

```text
Find Host
    ↓
Find Ports
    ↓
Find Services
    ↓
Find Versions
    ↓
Find OS
    ↓
Save Results
```
