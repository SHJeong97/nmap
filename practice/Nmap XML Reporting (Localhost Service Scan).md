# 🧾 Nmap XML Reporting (Localhost Service Scan)

## 📌 Overview
This project demonstrates how to generate **machine-readable Nmap scan reports** using XML output. Saving scan results to XML is useful for **documentation, audit trails, and automation**, since XML can be parsed by scripts and imported into security tools.

---

## 🎯 Objective
- Scan a locally running service on a specific port
- Export results in **XML format** for structured reporting
- Store the report as an artifact suitable for security assessments and documentation workflows

---

## 🧩 Scenario
During a security review, a team needs to document the exposure of a service running on a known port. Instead of saving results only as terminal output, the scan results are stored in **XML** so they can be:
- archived for compliance/audit
- parsed for automation
- compared over time (baseline vs drift)

This project simulates that workflow in a **controlled local environment**.

---

## 🛠 Tools & Technologies
- Nmap
- XML output reporting (`-oX`)
- Targeted port scanning (`-p`)
- Localhost-based testing (controlled scope)

---

## 🔍 Methodology

### Representative Command Used
```bash
nmap -p 8080 -oX scan_report.xml <target>
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<nmaprun>
  <host>
    <ports>
      <port portid="8080" protocol="tcp">
        <state state="open"/>
        <service name="http"/>
      </port>
    </ports>
  </host>
</nmaprun>
```

## 🧠 Key Findings
XML output provides structured scan results suitable for parsing and long-term documentation


Targeted scanning reduces noise while still producing a clear report artifact


Exporting scan output supports repeatable security workflows and baselining

