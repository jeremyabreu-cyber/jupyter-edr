# Jupyter-EDR – Behavioral Detection & Slack Alerting

## Overview

Jupyter-EDR is a lightweight, behavior-based detection pipeline inspired by modern Endpoint Detection and Response (EDR) platforms.

The project simulates endpoint process execution telemetry, reconstructs parent-child process lineage, applies heuristic risk scoring, maps activity to MITRE ATT&CK techniques, and delivers analyst-ready alerts to Slack.

This project focuses on **how detections are reasoned about, prioritized, and communicated**, rather than signature matching or endpoint enforcement.

---

## What This Is Not

This project is **not** a full EDR agent.

It does not perform kernel-level monitoring, real-time blocking, memory inspection, or endpoint isolation. The goal is to demonstrate how behavioral signals, process ancestry, and heuristic scoring can approximate EDR-style detections and SOC workflows.

---

## Tools & Platforms

- **Python** – Detection logic, enrichment, scoring, and automation
- **Jupyter Notebook** – Interactive detection engineering and analysis workspace, similar to how analysts prototype detections and hunt hypotheses
- **Pandas** – Event processing, correlation, and enrichment
- **MITRE ATT&CK** – Technique classification for detected behaviors
- **Slack Webhooks** – SOC-style alert delivery and analyst notification

---

## Detection Capabilities

The pipeline identifies suspicious activity using lightweight behavioral heuristics, including:

- LOLBin abuse (PowerShell, certutil, mshta, wscript)
- Suspicious parent-child process relationships
- Command-line keyword analysis (encoded commands, URL downloads)
- Multi-generation process lineage reconstruction
- Heuristic risk scoring to prioritize analyst attention
- MITRE ATT&CK technique mapping

---

## Alerting & Slack Integration

To simulate a real SOC workflow, detections above a defined risk threshold generate **a single consolidated Slack alert per execution**.

This mirrors how analysts often receive actionable alerts through collaboration platforms rather than continuously monitoring dashboards.

Each alert includes:
- Case ID and execution timestamp
- Severity and risk score
- Host and user context
- MITRE ATT&CK techniques
- Detection reasons
- Full process execution chain
- Recommended analyst actions

![Slack Alert Example](screenshots/slack_alert.png)

---

## Findings Summary

During execution, the pipeline identified multiple high-confidence suspicious behaviors, including:

- PowerShell execution launched from Microsoft Word with encoded command-line arguments, consistent with phishing attachment tradecraft
- certutil usage to retrieve external resources over HTTP, indicative of ingress tool transfer
- mshta execution spawned from scripting engines, a common signed binary proxy execution pattern

Heuristic risk scoring successfully differentiated isolated LOLBin usage from multi-signal attack chains requiring analyst attention.

---

## MITRE ATT&CK Techniques Observed

- **T1059.001** – Command and Scripting Interpreter: PowerShell  
- **T1059.003** – Command and Scripting Interpreter: Windows Command Shell  
- **T1105** – Ingress Tool Transfer  
- **T1218.005** – Signed Binary Proxy Execution: Mshta  
- **T1566.001** – Phishing Attachment  

---

## Output Artifacts

The pipeline exports structured alert data in CSV and JSON formats to support analyst review, reporting, and incident documentation.

Example artifacts are included for reference.

---

## Why This Matters

This project demonstrates how behavioral telemetry, process lineage, and heuristic scoring can approximate EDR-style detection logic without relying on signatures or heavyweight agents.

It reflects how detections are **built, evaluated, and communicated** in real-world blue team environments.
