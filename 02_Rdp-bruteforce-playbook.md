# 📘 RDP Brute Force Response Playbook

## 🎯 Purpose

Provide a standardized investigation workflow for repeated RDP authentication failures.

---

## 🚨 Detection

Alert Trigger:

📉 Excessive Windows Event ID 4625 events.

---

## 🔢 Initial Triage

✔ 🔔 Review Alert

✔ 🖥️ Verify affected host

✔ ⏱️ Check attack timeline

✔ 🌐 Identify source IP

✔ 👥 Review targeted usernames

---

## 🕵️ Investigation

Review:

• 📊 Login frequency

• 🗺️ Geo-IP

• 📜 Authentication history

• 🔓 Successful logins

• 🔗 Related alerts

---

## ⚡ Escalate if

- 🔓 Successful authentication occurs

- 👑 Privileged account targeted

- 🕸️ Multiple hosts affected

- 🦠 Malware activity observed

---

## 🛡️ Containment

• 🚫 Block malicious IP

• 🔌 Disable exposed RDP

• 🔑 Enable MFA

• 🔄 Reset compromised credentials

---

## 🩹 Recovery

- 🔄 Confirm attack has stopped.

- 🔍 Verify system integrity.

- 👁️ Continue monitoring.

---

## 📁 Closure

- 📝 Document findings.

- ✍️ Update incident notes.

- 🧠 Record lessons learned.
