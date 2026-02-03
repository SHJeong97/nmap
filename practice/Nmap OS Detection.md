# 🧠 Nmap OS Detection (Localhost Fingerprinting)

## 📌 Overview
This project demonstrates how to use **Nmap OS detection** to fingerprint the operating system of a host. OS fingerprinting is useful during **asset identification, vulnerability assessment, and incident triage**, since accurate OS context helps analysts prioritize checks and patch validation.

This lab uses a **local, controlled target (`localhost`)** and saves scan output as a report artifact.

---

## 🎯 Objective
- Run Nmap with **OS detection enabled** (`-O`)
- Scan the target `localhost`
- Save output to `target_os.txt`
- Review the file to identify OS details (e.g., Linux kernel family/version)

---

## 🛠 Tools & Technologies
- Nmap OS fingerprinting (`-O`)
- Linux shell output redirection (`>`)
- Report review using `cat`

---

## 🔍 Methodology

### 1) Run OS Detection Scan (Save Evidence)
```bash
sudo nmap -O -n localhost > target_os.txt
```
##  🧠 Key Takeaways
OS fingerprinting helps analysts understand a host’s baseline and potential exposure


Saving scan output improves repeatability and supports audit-style documentation


OS detection is an estimate and should be validated with additional signals when needed

