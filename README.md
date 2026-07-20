[README_Ransomware_Triage_Cerber.md](https://github.com/user-attachments/files/30203366/README_Ransomware_Triage_Cerber.md)
# Incident Response Triage: Multi-Stage Ransomware Intrusion (Cerber)

![Status](https://img.shields.io/badge/Status-Completed-success) ![Tools](https://img.shields.io/badge/Tools-Splunk%20%7C%20Sysmon-blue) ![MITRE](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-red)

## 📌 Executive Summary

This project reconstructs a full ransomware intrusion timeline, from the attacker's first external reconnaissance to the final encryption of victim files. Using Splunk to correlate Sysmon and file-share telemetry, I traced how a single unnoticed entry point escalated into a 401-file encryption event over nearly two weeks of undetected attacker dwell time.

👉 **[Read the Full Technical Breakdown Here]()** *(add your write-up link if you have one)*

---

## 🛠 Technical Environment

- **SIEM:** Splunk
- **Telemetry Sources:** Sysmon, Windows file-share logs
- **Malware:** Cerber ransomware, delivered via a steganographic payload and malicious VBScript dropper
- **Framework:** MITRE ATT&CK

---

## 🚀 Key Findings

- Reconstructed a **13-day, 19-hour** attacker dwell time — from initial brute-force compromise to ransomware execution.
- Identified the delivery mechanism as a **steganographic payload** hiding a malicious VBScript dropper, which evaded basic detection.
- Confirmed **401 files encrypted** across a workstation and network file share through Sysmon and file-share telemetry correlation.

---

## 🧠 Attack Chain (MITRE ATT&CK)

I mapped the full intrusion, from first contact to impact, across 6 confirmed techniques:

| Stage | MITRE Technique | Evidence |
|---|---|---|
| **Initial Access** | Brute Force | Repeated failed logins traced to a single external IP |
| **Execution** | Malicious VBScript Dropper | Steganographic payload analysis confirmed the delivery method |
| **Persistence / Evasion** | Living-off-the-land execution | Sysmon process trees showing dropper-to-payload handoff |
| **Impact** | Data Encrypted for Impact (Cerber) | 401 files confirmed encrypted via file-share telemetry |

---

## 📈 Final Results

By the end of this investigation, I achieved:

1. **Full Timeline Reconstruction:** Traced the intrusion from first recon to final impact across a 13-day, 19-hour window.
2. **Root Cause Identification:** Pinpointed the brute-force entry point and the steganographic delivery method that let it go unnoticed.
3. **Actionable Recommendations:** Proposed MFA enforcement and script-execution restrictions specifically targeting the gaps this intrusion exploited.
