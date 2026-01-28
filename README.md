🚨 JupiterEDR
An EDR-Style Detection & Alerting Lab Built in Jupyter

JupiterEDR is a lightweight, analyst-driven Endpoint Detection & Response (EDR) simulation built using Jupyter notebooks.

It reconstructs Windows process lineage, applies behavioral detection logic, maps activity to MITRE ATT&CK techniques, scores risk, and automatically generates case artifacts and Slack alerts — mimicking how modern EDR platforms operate behind the scenes.

⚠️ Disclaimer

All data shown in this repository is synthetic or lab-generated.

Hostnames and usernames are not real

Process events are simulated

No production systems were used

No real customer or organizational data is present

This project exists solely for learning, demonstration, and portfolio purposes.

🧠 What This Project Demonstrates

This lab focuses on how detection systems think, not how attackers operate.

Specifically, it demonstrates:

Process lineage reconstruction (parent → child chains)

Living-off-the-Land Binary (LOLBin) detection

Office-spawned script execution (real phishing tradecraft)

Risk scoring based on behavior, not signatures

MITRE ATT&CK technique mapping

Case-based alerting and artifact generation

Automated analyst notifications via Slack

This mirrors workflows found in platforms like:

CrowdStrike Falcon

Microsoft Defender for Endpoint

SentinelOne

Elastic Security

🧰 Tools & Technologies Used

Jupyter Notebook – interactive analysis and detection logic

Python – data processing, scoring, alerting

Pandas – event correlation and enrichment

MITRE ATT&CK – behavioral technique mapping

Slack Webhooks – automated analyst alerting

CSV / JSON – case artifacts & reporting output

🧪 Detection Pipeline (High-Level)

Process Events Generated

Simulated Windows process execution data

Process Lineage Reconstruction

Builds full parent-child chains (e.g.
powershell.exe ← winword.exe ← explorer.exe)

Behavioral Detection

LOLBins (PowerShell, certutil, mshta, wscript)

Suspicious command-line flags (-enc, -nop, URLs)

Office → script execution chains

Risk Scoring

Each event receives a weighted score

Severity assigned (Low / Medium / High / Critical)

MITRE ATT&CK Mapping

Techniques inferred from behavior and chain context

Case Creation

Events grouped into case folders (CASE-001, CASE-002, …)

Per-severity CSVs generated

Executive summary written

File hashes created (chain-of-custody style)

Slack Alerting

Top high-risk cases sent as a single Slack message

One message per run (not noisy, not spammy)

📁 Output Structure

Each run produces structured case artifacts:

EDR_Labs_Output/
└── CASE-001/
    ├── critical_alerts.csv
    ├── high_alerts.csv
    ├── medium_alerts.csv
    ├── edr_alerts_all.csv
    ├── edr_alerts.json
    ├── summary.txt
    └── hashes.txt


This mirrors how real IR teams preserve evidence and document findings.

🔔 Slack Alerting (For the “Busy Analyst”)

This lab includes optional Slack automation.

If an analyst defines a webhook:

Any event scoring ≥ 70 triggers an alert

Only the top 3 highest-risk cases are sent

One clean message per run

Each Slack alert includes:

Case ID

Severity

Host + User

Risk Score

MITRE Techniques

Key detections

Full process chain

Recommended actions

This simulates how detection platforms reduce noise while still escalating real risk.

📸 Screenshots

Screenshots in this repository illustrate:

Process lineage reconstruction

MITRE ATT&CK mapping logic

Risk score distribution

Case artifact generation

Slack alert output

Screenshots are intentionally curated to demonstrate analyst-level visibility, not step-by-step instructions.

(See /screenshots directory.)

🎯 Why This Matters

This project shows:

You understand how EDR detections are built

You can reason about behavior, not just tools

You think in terms of cases, alerts, and response

You can automate analyst workflows

You can explain security concepts clearly

This is the difference between:

“I used an EDR”
and
“I understand how an EDR works.”

🚀 Future Enhancements

Planned or easily extendable:

Rule tuning & false-positive suppression

Time-window correlation

ATT&CK tactic rollups

Detection confidence scoring

SOAR-style response hooks
