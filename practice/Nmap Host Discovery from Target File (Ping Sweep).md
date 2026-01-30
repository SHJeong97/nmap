# 📡 Nmap Host Discovery from Target File (Ping Sweep)

## 📌 Overview
This project demonstrates how to perform **host discovery (ping sweep)** using Nmap while reading targets from an input file. It also shows how to extract only the **online IP addresses** and save them into a clean evidence file for documentation and follow-up scanning.

This is a common workflow in **network reconnaissance, asset inventory, and security triage**, where you start by identifying live hosts before running deeper scans.

---

## 🎯 Objective
- Read a list of IP addresses from `targets.txt`
- Perform Nmap host discovery (no port scan)
- Extract only online host IPs
- Save results to `online_hosts.txt` (one IP per line)

---

## 🛠 Tools & Technologies
- Nmap (`-sn`, `-iL`)
- Linux shell utilities (`awk`, `sort`)
- File-based target management

---

## 🔍 Methodology

### 1) Prepare Target List
Targets are stored in a file to support scalable scanning and repeatable workflows.

**Example:**
```text
127.0.0.1
127.0.0.2
127.0.0.3
```
### 2) Host Discovery (Ping Sweep)
Use Nmap to identify which targets respond and are considered “up”.
Representative command:
```bash
nmap -sn -n -iL targets.txt
```
-sn = host discovery only (no port scan)


-n = no DNS resolution (clean output + avoids hostnames)


-iL = read targets from a file



### 3) Extract Online Hosts 
Parse Nmap results and write only the IP addresses of online hosts into online_hosts.txt.
Portfolio-safe extraction command:
```bash
nmap -sn -n -iL targets.txt \
| awk '/Nmap scan report for/{ip=$NF; gsub(/[()]/,"",ip)} /Host is up/{print ip}' \
| sort -u > online_hosts.txt
```
Result file format (online_hosts.txt):
```bash
127.0.0.1
127.0.0.2
```

### 🧠 Key Takeaways
File-based targets (-iL) make scanning scalable and repeatable


A ping sweep helps reduce noise by identifying live hosts before deeper scans


Producing a clean host list supports automation and follow-on port/service enumeration

