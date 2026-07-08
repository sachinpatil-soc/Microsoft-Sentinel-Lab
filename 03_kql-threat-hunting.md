# 🔍 KQL Threat Hunting Queries

### Query 1 — Top Attacking IPs

- The following KQL queries simulate common investigations performed by Tier 1 SOC Analysts using Microsoft Sentinel.

- These queries focus on authentication monitoring, brute-force detection, suspicious login behaviour, and incident triage.

* SecurityEvent
* | where TimeGenereted > ago(7d)
* | where EventID == 4625
* | summarize FailedAttempts=count() by IpAddress, Computer, AccountType, FailerReason
* | where FailedAttempts >= 10
* | order by FaildAttemts desc

Purpose:
Identify IP addresses generating the highest number of failed authentication attempts.
