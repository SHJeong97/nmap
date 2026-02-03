# 🛰️ Nmap Host Discovery (Basic + Advanced Techniques)

## 🎯 Objective
Learn and practice **host discovery** with Nmap to identify which hosts are online *before* doing deeper scans. This lab series covers:

- Ping scan discovery with `-sn` (no port scanning)
- TCP discovery probes with `-PS` (SYN ping) and `-PA` (ACK ping)
- Advanced discovery using:
  - TCP pings on specific ports (`-PS<ports>`)
  - UDP pings (`-PU<port>`)
  - Skipping discovery (`-Pn`)
  - Combining multiple probe types for reliability
- Saving results for documentation using `-oN`

> All actions were performed in a controlled lab environment using localhost and sample ranges.

---

## 🧩 Why This Matters (Security Context)
Host discovery is the first phase of reconnaissance and security assessments. Different networks treat probes differently:
- ICMP often gets blocked
- TCP/UDP probes may still work
- Combining discovery methods helps detect systems behind filtering

---

## 🛠 Tools Used
- Nmap
- Linux shell utilities (redirects, `cat`, `history`)

---

## 🔍 Part 1 — Basic Host Discovery

### 1) Ping Scan (No Port Scan)
Scan a /24 range without port scanning:
```bash
sudo nmap -sn -n 192.168.1.0/24
```
### 2) TCP SYN Ping (-PS)
Unreachable example:
```bash
sudo nmap -PS -n 192.168.1.1
```
Localhost example:
```bash
sudo nmap -PS -n 127.0.0.1
```

### 3) TCP ACK Ping (-PA)
Unreachable example:
```bash
sudo nmap -PA -n 192.168.1.1
```
Localhost example:
```bash
sudo nmap -PA -n 127.0.0.1
```

### 4) Combine Discovery Probes (-PS -PA)
Range example:
```bash
sudo nmap -PS -PA -n 192.168.1.0/24
```
Localhost example:
```bash
sudo nmap -PS -PA -n 127.0.0.1
```


## 🔬 Part 2 — Advanced Host Discovery Techniques
### 1) TCP Ping on Specific Ports (-PS<ports>)
Probe only selected ports (example: 2222 and 8080):
```bash
nmap -PS2222,8080 -n 127.0.0.1

```
### 2) UDP Ping (-PU<port>)
UDP probes require elevated privileges:
```bash
sudo nmap -PU5353 -n 127.0.0.1
```

### 3) Skip Host Discovery (-Pn)
Force Nmap to assume the host is up and proceed:
```bash
nmap -Pn -n 127.0.0.1
```

### 4) Combine TCP + UDP Discovery
More reliable discovery in filtered environments:
```bash
sudo nmap -PS2222 -PU5353 -n 127.0.0.1
```

### 5) Save Results to a File (Documentation)
Save scan output in normal format:
```bash
nmap -Pn -oN hosts.txt -n 127.0.0.1
cat hosts.txt
```

## ✅ Key Takeaways
-sn is best for fast discovery-only scans.


-PS and -PA help discover hosts when ICMP is blocked.


-PU is useful when UDP behavior reveals host presence.


-Pn is useful when probes are blocked (but increases scan time at scale).


Combining probes improves reliability in real networks.


Saving results (-oN) supports reporting and reproducibility.

