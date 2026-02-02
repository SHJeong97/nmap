# 🔍 Nmapmap Verbosity Levels (0 / -v / -vv) for Clearer Scan Insight

## 📌 Overview
This project demonstrates how **Nmap verbosity levels** change the amount of detail shown during a scan. Verbosity is valuable in real security work because it helps you:
- keep output minimal for quick checks (default)
- see scan stages and discovery events for troubleshooting (`-v`)
- capture deeper timing/debug detail for investigation (`-vv`)

All activity is performed in a **local, controlled environment** using a simple local HTTP server as a scan target.

---

## 🎯 Objective
- Start a local HTTP service on port **8080**
- Scan the service at different verbosity levels
- Save outputs to files for documentation and comparison
- Understand when to use each verbosity level in real workflows

---

## 🛠 Tools & Technologies
- Nmap (verbosity: default, `-v`, `-vv`)
- Python HTTP server (local test service)
- Linux utilities (`cat`, `diff`)
- Output redirection for evidence files

---

## 🔍 Methodology

### 1) Start a Local Test Service
A local HTTP server is used as a safe target for scanning.

```bash
python3 -m http.server --bind localhost 8080 &
```
### 2) Scan with Default Verbosity (Level 0)
Minimal output — best for quick confirmation that a port is open.
```bash
nmap -p 8080 localhost > verbosity-0.txt
```

### 3) Scan with Verbosity Level 1 (-v)
Adds scan-stage detail such as discovery events (helpful for troubleshooting).
```bash
nmap -p 8080 localhost -v > verbosity-1.txt

```
### 4) Scan with Verbosity Level 2 (-vv)
Even more detail — useful for deeper analysis and debugging.
```bash
nmap -p 8080 localhost -vv > verbosity-2.txt


```
### 5) Compare Outputs
Use diff to see exactly how verbosity changes the scan story.
```bash
diff verbosity-0.txt verbosity-1.txt

```

## 🧠 Key Takeaways
Default (0): quickest signal (open/closed + basic service label)


-v: adds clarity on how Nmap reached the result (scan stages + discovery)


-vv: best for deeper troubleshooting and audit-style documentation


Saving outputs supports repeatability and evidence-based reporting

