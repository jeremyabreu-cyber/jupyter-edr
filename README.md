# 🛰️ JupiterEDR

**A Jupyter-based Endpoint Detection & Response (EDR) Simulation**

---

## 🧭 Overview

**JupiterEDR** is a lightweight Endpoint Detection & Response (EDR) lab built entirely in **Jupyter Notebooks**.
It simulates how modern EDR platforms detect, score, and investigate suspicious Windows process behavior using **behavioral heuristics**, **process lineage**, and **MITRE ATT&CK mapping**.

This project focuses on **how EDRs think**, not how attackers break in.

The goal is to demonstrate detection engineering concepts such as:

* Process ancestry reconstruction
* Living-off-the-Land Binary (LOLBin) abuse detection
* Risk-based scoring
* Alert fatigue reduction
* Case-based investigation workflows
* Automated analyst notification

---

## ⚠️ Disclaimer

All data in this repository is **synthetic and simulated**.

* Hostnames are fictional
* Usernames are fictional
* Process execution data is simulated
* No production or enterprise systems were used
* No personally identifiable information (PII) is present

This repository exists **solely for educational and portfolio demonstration purposes**.

---

## 🧪 What This Lab Simulates

JupiterEDR mirrors internal detection logic commonly found in platforms such as:

* CrowdStrike Falcon
* Microsoft Defender for Endpoint
* SentinelOne
* Elastic Security

This project does **not** replicate these tools.
It demonstrates **core detection and investigation concepts** used by modern EDR platforms.

---

## 🧠 Detection Approach

### Behavioral Signals

Suspicious behavior is identified using signals frequently abused in real-world attacks:

* Living-off-the-Land Binaries (LOLBins)

  * `powershell.exe`
  * `certutil.exe`
  * `mshta.exe`
  * `wscript.exe`
* Office applications spawning script interpreters
* Suspicious command-line indicators

  * Encoded PowerShell (`-enc`)
  * Hidden execution (`-hidden`)
  * URL usage
* Abnormal parent-child process relationships

These signals are combined into **behavioral patterns**, not one-off alerts.

---

### 🧬 Process Lineage Reconstruction

Rather than evaluating events in isolation, JupiterEDR reconstructs **full process execution chains**.

This allows the lab to identify:

* Phishing-delivered payloads
* Script proxy execution
* Initial access vectors
* Living-off-the-land attack paths

Detection is driven by **"how did this start?"**, not just **"what ran?"**

---

## 🎯 Risk Scoring & Severity

Each suspicious execution chain is assigned a **numerical risk score** and mapped to a severity level.

| Severity | Score Range |
| -------- | ----------- |
| Medium   | 40–59       |
| High     | 60–79       |
| Critical | 80–100      |

This approach prioritizes **high-confidence detections** while suppressing low-signal noise.

The system is tuned to surface **complete attack narratives**, not isolated events.

---

## 🗺️ MITRE ATT&CK Mapping

Detected behavior is mapped to **MITRE ATT&CK techniques** based on execution context and lineage.

Examples include:

* `T1059.001` – PowerShell
* `T1059.003` – Windows Command Shell
* `T1105` – Ingress Tool Transfer
* `T1218.005` – Mshta
* `T1566.001` – Phishing Attachment

Mapping is **behavior-driven**, not signature-based.

---

## 📁 Case-Based Output

Detections are grouped into structured case folders, simulating real SOC investigation workflows.

### Example Output Structure

```text
EDR_Labs_Output/
├── CASE-001/
│   ├── critical_alerts.csv
│   ├── high_alerts.csv
│   ├── summary.txt
│   └── hashes.txt
├── CASE-002/
│   └── ...
```

Each case contains:

* Severity-specific alert files
* Executive-style investigation summary
* File integrity hashes (chain-of-custody simulation)

This models how detections move from **signal → case → analyst → response**.

---

## 🔔 Automated Analyst Notification (Slack)

JupiterEDR includes **automated Slack alerting** to simulate real SOC triage workflows.

To prevent alert spam, notifications are only generated for **high-confidence threats**:

* Alerts trigger when a case reaches a **risk score of 70 or higher**
* One message is sent **per case**, not per event
* Messages include:

  * Case ID
  * Severity level
  * Host and user
  * Top suspicious detections
  * MITRE ATT&CK techniques
  * Recommended response actions

This mirrors how modern SOC teams rely on **automation to surface only the threats worth human attention**.

---

## 🧪 Why Jupyter?

Jupyter Notebooks are used intentionally to simulate:

* Detection logic prototyping
* Threat hunting workflows
* Investigation playbook development
* Analyst-driven experimentation

Many detection engineers prototype logic in notebooks before deploying rules into SIEM, EDR, or XDR platforms.

This lab models that **engineering-to-operations pipeline**.

---

## 🚧 Project Status

This project is **actively developed** and designed as a portfolio artifact demonstrating:

* Detection engineering mindset
* Behavioral analysis
* SOC investigation workflows
* Security automation fundamentals

---

## 🖼️ Screenshots

Screenshots illustrating detection logic, case output, MITRE mapping, and Slack alerts can be found in:

```
/screenshots
```

Each screenshot corresponds to a specific stage of the detection and response pipeline.

---

## 👤 Author

Built by **Jeremy Abreu**
Cybersecurity | Incident Response | Detection Engineering

