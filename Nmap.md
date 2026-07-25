# Nmap

Nmap (Network Mapper) is an open-source network scanning tool used to discover hosts, scan ports, detect running services, and gather information about a target machine.

It is one of the most popular reconnaissance tools used by Network Engineers, System Administrators, and Penetration Testers.

---

# Why Do We Need Nmap?

Suppose someone gives you an IP address.

```
192.168.1.10
```

You don't know:

- Is the machine online?
- Which ports are open?
- Which services are running?
- What operating system is it using?
- What versions of those services are installed?

Nmap helps answer all these questions.

---

# What Can Nmap Do?

Nmap can:

- Discover live hosts
- Scan open ports
- Detect running services
- Detect service versions
- Detect the operating system
- Run NSE (Nmap Scripting Engine) scripts
- Save scan results for later analysis

---

# How Nmap Fits Into Networking

Remember what we learned earlier:

```
IP Address
        │
        ▼
Host
        │
        ▼
Ports
        │
        ▼
Services
```

Example:

| Port | Service |
|------|---------|
| 21 | FTP |
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |

Nmap checks these ports and tells us which services are running.

Example:

```
22/tcp open  ssh

80/tcp open  http

443/tcp open https
```

---

# Nmap vs TCPDump

These two tools are often confused.

| TCPDump | Nmap |
|---------|------|
| Watches existing traffic | Creates its own traffic |
| Packet Analysis | Network Scanning |
| Passive | Active |
| Shows packets | Finds hosts, ports and services |

Think of it like this:

TCPDump:

> "I'll watch what is happening."

Nmap:

> "I'll ask the target machine some questions."

---

# How Nmap Works

A typical scan follows this order:

```
Target IP
     │
     ▼
Host Discovery
     │
     ▼
Port Scan
     │
     ▼
Service Detection
     │
     ▼
Version Detection
     │
     ▼
Operating System Detection
```

Not every scan performs every step.

It depends on the options you choose.

---

# Understanding Ports

A computer can run multiple services at the same time.

Each service listens on a different port.

Example:

```
SSH      → Port 22

HTTP     → Port 80

HTTPS    → Port 443

FTP      → Port 21
```

If a port is open, it usually means a service is running there.

---

# Port States

While scanning, Nmap mainly reports three states.

## Open

A service is actively listening.

Example:

```
22/tcp open ssh
```

---

## Closed

Nothing is listening on that port.

The host is reachable, but the service is not running.

---

## Filtered

Nmap cannot determine whether the port is open or closed.

Usually because a firewall is blocking the traffic.

---

# Common Scan Types

## Host Discovery

Checks whether a machine is online.

---

## TCP SYN Scan

The most commonly used scan.

Fast and relatively stealthy.

---

## TCP Connect Scan

Performs a complete TCP connection.

Used when SYN Scan isn't possible.

---

## UDP Scan

Scans UDP services like DNS, DHCP, and SNMP.

Usually slower than TCP scanning.

---

# Enumeration

Once open ports are found, Nmap can gather more information.

Examples:

- Service Name
- Service Version
- Operating System
- Additional information using NSE scripts

---

# Typical Workflow

```
Target
   │
   ▼
Host Discovery
   │
   ▼
Port Scan
   │
   ▼
Service Detection
   │
   ▼
Version Detection
   │
   ▼
OS Detection
   │
   ▼
Further Enumeration
```

This is the workflow commonly followed during network reconnaissance.

---

# Where is Nmap Used?

- Network Troubleshooting
- Security Audits
- Penetration Testing
- Vulnerability Assessment
- CTF Challenges
- Home Lab Practice
- Asset Discovery

---

# Advantages

- Fast
- Free and Open Source
- Supports TCP and UDP scanning
- Detects services and versions
- Supports scripting with NSE
- Works on Windows, Linux, and macOS

---

# Limitations

- Firewalls may block scans.
- Some scans require root/administrator privileges.
- UDP scans can be slow.
- Scanning systems without permission may be illegal.

---

# Interview Questions

### What is Nmap?

An open-source network scanning tool used for host discovery, port scanning, and service enumeration.

---

### What does Nmap stand for?

Network Mapper.

---

### Why is Nmap used?

To discover live hosts, identify open ports, detect running services, and gather information about target systems.

---

### What is the difference between TCPDump and Nmap?

TCPDump captures and analyzes existing network traffic.

Nmap actively sends packets to discover hosts, ports, and services.

---

### What are the common port states in Nmap?

- Open
- Closed
- Filtered

---

### What is Enumeration?

Enumeration is the process of collecting additional information about a target after discovering open ports, such as service versions, operating system details, and other useful information.

---

# Memory Hook

```
Target
   │
   ▼
Host Discovery
   │
   ▼
Port Scan
   │
   ▼
Service Detection
   │
   ▼
Version Detection
   │
   ▼
OS Detection
```

**Remember:**

> **TCPDump watches traffic. Nmap creates traffic.**
