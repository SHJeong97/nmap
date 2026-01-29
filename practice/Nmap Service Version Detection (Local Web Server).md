# 🌐 Nmap Service Version Detection (Local Web Server)

## 📌 Overview
This project demonstrates how **Nmap service version detection (`-sV`)** can be used to identify the characteristics of a running web service.

Service version enumeration is a core reconnaissance technique used in **vulnerability assessment, asset inventory, and attack surface analysis**, as exposed service metadata often correlates with known security risks.

---

## 🎯 Objective
- Identify a locally running web service on a non-standard port
- Use Nmap’s version detection to fingerprint the service
- Interpret service detection results from a defensive security perspective

---

## 🧩 Scenario
A web server is running locally on port **8080**, but its software details are unknown.

In real-world security operations, identifying exposed service versions is critical for:
- Vulnerability assessment
- Patch verification
- Asset inventory accuracy
- Reducing unnecessary attack surface

This project simulates a **controlled, local reconnaissance task** commonly performed during internal security reviews.

---

## 🛠 Tools & Technologies
- Nmap
- TCP/IP networking fundamentals
- Service fingerprinting (`-sV`)
- Localhost-based testing (controlled scope)

---

## 🔍 Methodology

### Representative Command Used
```bash
nmap -sV -p <port> <target>

PORT     STATE   SERVICE   VERSION
8080/tcp open    http      Python-based HTTP service

```
## 🧠 Key Findings
Service version detection reveals meaningful metadata beyond simple port status


Services running on non-standard ports are still easily identifiable


Exposed version information can significantly increase attack surface if not properly managed

