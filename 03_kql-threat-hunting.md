### Query 1 — Top Attacking IPs

SecurityEvent
| where EventID == 4625
| summarize FailedAttempts=count() by IpAddress
| top 10 by FailedAttempts desc

Purpose:
Identify IP addresses generating the highest number of failed authentication attempts.
