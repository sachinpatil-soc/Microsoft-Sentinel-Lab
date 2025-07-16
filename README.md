# Microsoft Sentinel Lab

### 🔐 Azure Honeypot Deployment & SIEM Integration (Microsoft Sentinel)
A cloud-based honeypot deployment designed to capture, analyze, and visualize real-world RDP brute-force attacks using Azure Sentinel.

## 🛠️ Project Overview

### 🚀 Deployed a live honeypot in Microsoft Azure to emulate vulnerable infrastructure and attract malicious activity.

### 🔐 Configured Network Security Groups (NSGs) and host-level firewalls to control access while maximizing log capture.

### 📊 Set up an integrated SIEM pipeline by forwarding logs to Azure Log Analytics Workspace, connected to Microsoft Sentinel for real-time threat monitoring.

### 🕵️‍♂️ Queried security logs using KQL (Kusto Query Language) to detect patterns in failed RDP logins (Event ID 4625) and investigate anomalous login behavior.
### 🌍 Enriched log data with Geo-IP context using ipgeolocation.io APIs, identifying the origin of attack traffic.
![image alt](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/7749a3e6b786b367bc53243fa22d9e5fcb4013d5/microsoft-sentinel4.png)
### 📈 Built a custom Sentinel Workbook to visualize attack sources on a world map and assist in threat hunting and incident response.


## ⚙️ Tools & Technologies
- Languages: PowerShell
- Utilities & APIs:
- ipgeolocation.io – for attacker geolocation data
- Azure Log Analytics
- Microsoft Sentinel
- Security IDs Monitored:
- Event ID 4625 – Failed RDP login attempts


## 🧪 Features & Outputs
- 🔄 PowerShell Script: Parses Windows Event Viewer logs for failed RDP attempts and queries IP geolocation data.
- 🌐 Geolocation Visualization: Plots attackers’ origin on a world map using enriched custom logs in Sentinel.

### 📌 Observations:
#### Live attack data shows repeated brute-force attempts from countries like USA, Europ, Pakistan and Australia all plotted in near real-time.
![image alt](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/7749a3e6b786b367bc53243fa22d9e5fcb4013d5/microsoft-sentinel3.png)


