# 🧪 Nmap Lab – Practical Verification

This document verifies hands-on experience using **Nmap** in a sandboxed lab environment.  
Screenshots included in this repository serve as **evidence of execution and analysis**, not copied solutions or proprietary lab content.

---

## 📌 Learning Outcomes

| Topic | Description |
|------|------------|
| Host Discovery | Discovered live hosts on a network using Nmap host discovery techniques |
| Port Scanning | Explored common TCP and UDP port scanning methods |
| Service Enumeration | Identified running services and service version numbers |
| Privilege Awareness | Compared Nmap behavior when run with sudo vs local user privileges |
| Scan Performance | Controlled scan speed and timing to balance stealth and efficiency |
| Reporting | Saved scan results in multiple output formats for documentation and review |

---

## 🔐 Privilege Context

| Execution Mode | Behavior |
|--------------|----------|
| `sudo nmap` | Enables advanced scans such as TCP SYN scan (`-sS`) and raw packet crafting |
| Local user | Defaults to TCP connect scan (`-sT`) with limited feature availability |
| Explanation | Crafting raw packets (e.g., TCP SYN) requires root privileges |

---

## 🔍 Nmap Options Reference

### Host Discovery

| Option | Explanation |
|------|-------------|
| `-sL` | List scan – list targets without scanning |
| `-sn` | Ping scan – host discovery only |

---

### Port Scanning

| Option | Explanation |
|------|-------------|
| `-sT` | TCP connect scan – completes full three-way handshake |
| `-sS` | TCP SYN scan – first step of handshake (requires sudo) |
| `-sU` | UDP scan |
| `-F` | Fast mode – scans top 100 common ports |
| `-p [range]` | Specify port range (`-p-` scans all ports) |
| `-Pn` | Treat all hosts as online (skip host discovery) |

---

### Service & OS Detection

| Option | Explanation |
|------|-------------|
| `-O` | Operating system detection |
| `-sV` | Service version detection |
| `-A` | Enables OS detection, version detection, script scanning, and traceroute |

---

### Timing & Performance Control

| Option | Explanation |
|------|-------------|
| `-T0`–`-T5` | Timing templates from paranoid (0) to insane (5) |
| `--min-parallelism` / `--max-parallelism` | Control number of parallel probes |
| `--min-rate` / `--max-rate` | Control packets per second |
| `--host-timeout` | Maximum time to wait for a target host |

---

### Real-Time Output

| Option | Explanation |
|------|-------------|
| `-v` | Verbose output (`-vv`, `-v4`) |
| `-d` | Debug output (`-d`, `-d9`) |

---

### Output & Reporting Formats

| Option | Explanation |
|------|-------------|
| `-oN <file>` | Normal output |
| `-oX <file>` | XML output |
| `-oG <file>` | Grep-able output |
| `-oA <basename>` | Output in all major formats |

---

## 📸 Screenshot Verification Notice

Screenshots included in this repository:
- Were captured from **authorized, sandboxed lab environments**
- Demonstrate **commands executed and results analyzed**
- Are **sanitized** to remove sensitive information
- Support written findings and technical interpretation

---

## 📘 Educational Disclaimer

All scans and analyses documented here were performed in **controlled lab environments** using simulated or test systems for **educational and professional development purposes only**.
