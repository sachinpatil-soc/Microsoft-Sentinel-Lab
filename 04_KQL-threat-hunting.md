
# 🔍 KQL Threat Hunting Queries

- The following KQL queries simulate common investigations performed by Tier 1 SOC Analysts using Microsoft Sentinel.

- These queries focus on authentication monitoring, brute-force detection, suspicious login behavior, and incident triage.

## Query 1 — Top Attacking IP Addresses

### Objective

Identify IP addresses responsible for the highest number of failed RDP authentication attempts.

### KQL Query

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by IpAddress, Computer, AccountType, FailureReason
| where FailedAttempts >= 10
| order by FailedAttempts desc
```

### Investigation Result

![Top Attacking IPs](screenshots/query1-top-attacking-ip.png)

### Analyst Observation

Two external IP addresses generated a significant number of failed authentication attempts against the Azure honeypot. This activity is consistent with automated brute-force or password spraying attacks and would require further investigation in a production SOC environment.
---

## Query 2 — Most Targeted User Accounts

### Objective

Identify which user accounts received the highest number of failed authentication attempts.

### KQL Query

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by TargetAccount
| sort by FailedAttempts desc
```

### Investigation Result

![Most Targeted Accounts](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/40487555fa41c51901286153ca2896effe97d6a5/screenshots/query2-Most%20Targeted%20Usernames.png)

### Analyst Observation

The investigation identified the accounts most frequently targeted during the brute-force activity. The built-in **Administrator** account received the highest number of failed login attempts, which is consistent with common attacker behavior targeting privileged accounts.

---

## Query 3 — Failed Authentication Activity Over Time

### Objective

Visualize failed authentication attempts over time to identify attack spikes and periods of increased malicious activity.

### KQL Query

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by bin(TimeGenerated, 1h)
| render timechart
```

### Investigation Result

![Failed Authentication over time](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/2e4df078eec0700771b59b9ac7edb960726ad639/screenshots/query3-Failed%20Authentication%20Over%20Time.png)

### Analyst Observation

The time-series visualization highlights periods of increased brute-force activity against the Internet-facing Windows server. Monitoring authentication trends helps analysts correlate attack activity with other security events during an investigation.

---

## Query 4 — Successful Logons

### Objective

Identify successful authentication events during the monitoring period.

### KQL Query

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4624
| summarize SuccessfulLogons = count() by Account, IpAddress
| sort by SuccessfulLogons desc
```

### Investigation Result

![Successful Logons](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/4e6b632bd673cf7bb842ea1666b064ea36bbd792/screenshots/query4-Successful%20Logins%20(4624).png)

### Analyst Observation

The investigation verified whether any successful authentication events occurred during the monitoring period. Correlating successful logons with previous authentication failures is an important Tier 1 SOC investigation step.

---
## Query 5 - Top Targeted Computers

### Objective 

Identify which systems received the highest volume of failed authentication attempts.

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by Computer
| order by FailedAttempts desc
```

### Investigation Results 

![Top Targeted Computer](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/a69984099e7b58a3aba700599545808ab55d74a4/screenshots/query5-Top%20Targeted%20Computers.png)

### Analyst Observation

The investigation identified the computers that received the highest volume of failed authentication attempts during the monitoring period. This helps the analyst spot likely targeted systems and investigate repeated Event ID 4625 activity for possible brute-force attempts, credential issues, or misconfigured services

---
## Query 6 Logon Type

### Objective

Determine which Windows logon types attackers attempted to use.

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by LogonType
| order by FailedAttempts desc
```
### Investigation Results 

![logon type](https://github.com/sachinpatil-soc/Microsoft-Sentinel-Lab/blob/de5f6652443d0e4bbd81f564020ef2745ea8810e/screenshots/query6-Logon%20Types.png)

### Analyst Observation

Identified authentication patterns by logon type to detect abnormal access methods. Unusual remote or privileged logons may indicate credential misuse or unauthorized access attempts.

---

## Query 7 Failed Logins by Hour 

### Objective
 Identify peak attack hours.

```kql
SecurityEvent
| where TimeGenerated > ago(7d)
| where EventID == 4625
| summarize FailedAttempts = count() by LogonType
| order by FailedAttempts desc
```


Analyst Observation:
Analyzed failed login activity by time to identify brute-force or password-spraying patterns. Login spikes during unusual hours require further investigation.

















