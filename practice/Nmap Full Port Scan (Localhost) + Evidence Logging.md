# 🔎 Nmap Full Port Scan (Localhost) + Evidence Logging

## 📌 Overview
This project demonstrates how to run a **full TCP port scan** using Nmap and record results to a file for documentation and review. This is a foundational workflow for **network troubleshooting, asset validation, and security triage**.

---

## 🎯 Objective
- Perform a full port scan against a controlled local target (`localhost`)
- Identify open ports reliably
- Save scan results to a report file for repeatable documentation

---

## 🧩 Scenario
A critical internal server is suspected to have an unexpected service running. As a junior network/security engineer, the goal is to scan the host, identify open ports, and record findings in a report for escalation or remediation.

---

## 🛠 Tools & Technologies
- Nmap (port scanning)
- Netcat (controlled local test service)
- Linux shell (output redirection / report saving)

---

## 🔍 Methodology

### Test Setup (Controlled Environment)
A local listener was started on a known port to simulate a service in a safe environment.

**Representative setup command:**
```bash
while true; do nc -n -lvp <port>; done &


nmap -p- -oN <output_file> <target>

PORT     STATE SERVICE
7777/tcp  open  unknown
```



## 🧠 Key Findings
Full port scanning (-p-) ensures unexpected services are not missed


Saving output to a file supports repeatability, reporting, and incident documentation


Even on localhost, enumeration reveals exposure that should be validated and controlled

