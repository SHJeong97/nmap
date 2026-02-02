# 🛡️ Rogue UDP Service Detection (Nmap UDP Scan + Parsing Evidence)

## 📌 Overview
This project demonstrates how to detect a **potential rogue UDP service** by performing a targeted UDP scan with Nmap and then parsing results with classic Linux text-processing tools. UDP scanning is a common SOC / IR task because rogue services may appear without obvious TCP exposure.

This workflow focuses on:
- scanning a **specific UDP port range** (9990–10000)
- saving scan output for documentation (`udp_scan_results.txt`)
- extracting the **smallest open UDP port** and storing it in an environment variable (`OPEN_UDP_PORT`)

---

## 🎯 Objective
- Run an Nmap UDP scan against `localhost` for ports `9990-10000`
- Save results to `udp_scan_results.txt`
- Parse results to identify the smallest open UDP port
- Export the value to `OPEN_UDP_PORT`
- If none are found, set `OPEN_UDP_PORT=NONE`

---

## 🛠 Tools & Technologies
- Nmap UDP scanning (`-sU`)
- Linux CLI parsing (`grep`, `awk`, `cut`, `sort`, `head`)
- Evidence artifact creation via output redirection

---

## 🔍 Methodology

### 1) Run Targeted UDP Scan (Save Evidence)
```bash
sudo nmap -sU -p9990-10000 -n localhost > udp_scan_results.txt
```
## Why this matters
-sU performs UDP scanning (often requires elevated privileges)


-p9990-10000 limits scope (faster + focused investigation)


-n prevents DNS resolution noise


Output is saved as an evidence artifact (udp_scan_results.txt)

### 2) Extract the Smallest Open UDP Port 

```bash
OPEN_UDP_PORT="$(
  grep ”open” \ 
  | grep "udp" udp_scan_results.txt \
  | awk '{print $1}' \
  | cut -d/ -f1 \
)"


```

## ✅ Output Behavior
If an open UDP port is found, OPEN_UDP_PORT will be set to the smallest one (example):


9995

If no open UDP ports are found in the range:


NONE

## 🧠 Key Takeaways
UDP services can be harder to detect than TCP, making targeted UDP scans important


Saving scan output supports repeatability and evidence-based reporting


Combining Nmap with grep/awk enables lightweight triage even without SIEM tooling

