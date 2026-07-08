# 📌 Executive Summary

## 🚀 Project Overview

- This project demonstrates a complete Tier 1 Security Operations Center (SOC) investigation using Microsoft Sentinel.

- A Windows Server deployed in Microsoft Azure was intentionally exposed to the Internet as a controlled honeypot to capture real-world Remote Desktop Protocol (RDP) brute-force attacks.

- Using Microsoft Sentinel and Kusto Query Language (KQL), authentication logs were collected, investigated, and documented following a structured enterprise SOC workflow.

---

## 🏢 Business Problem

- Internet-facing Windows servers are continuously targeted by automated credential attacks.

- Without centralized monitoring and structured investigation procedures, organizations may fail to detect malicious authentication activity before compromise occurs.

- This project demonstrates how Microsoft Sentinel assists SOC analysts in detecting, investigating, documenting, and escalating authentication-related security incidents.

---

## 🛠️ Skills Demonstrated

- Microsoft Sentinel
- Kusto Query Language (KQL)
- Security Monitoring
- Alert Triage
- Threat Hunting
- Incident Investigation
- Incident Documentation
- Incident Escalation
- Geo-IP Enrichment
- Security Reporting

---

## 📈 Key Outcome

- The investigation identified over 1,200 failed authentication attempts originating from multiple countries.

- No successful compromise was detected.

- The investigation concluded with documented findings, response recommendations, and a Tier 1 escalation workflow representative of enterprise SOC operations.
