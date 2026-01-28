project:
  name: JupiterEDR
  tagline: "A Jupyter-based EDR detection, scoring, and alerting lab"
  type: Security Engineering / Detection Engineering Lab
  author: Jeremy Abreu

disclaimer:
  purpose: Educational and portfolio demonstration only
  data:
    - All hostnames are synthetic
    - All usernames are synthetic
    - All process execution data is simulated
    - No production systems were used
  privacy:
    - No PII present
    - No customer data
    - No enterprise data
  note: >
    This project does not represent real incidents or environments and should
    not be interpreted as operational telemetry.

overview:
  description: >
    JupiterEDR is a lightweight Endpoint Detection & Response (EDR) simulation
    built entirely in Jupyter notebooks. It reconstructs Windows process
    execution lineage, applies behavioral detection heuristics, maps activity
    to MITRE ATT&CK techniques, assigns risk scores, generates case artifacts,
    and delivers automated Slack alerts.
  philosophy:
    - Behavior-based detection over signatures
    - Analyst-first visibility
    - Minimal noise, high signal
    - Automation where it matters
  platforms_mimicked:
    - CrowdStrike Falcon
    - Microsoft Defender for Endpoint
    - SentinelOne
    - Elastic Security

objectives:
  - Reconstruct parent-child process execution chains
  - Detect Living-off-the-Land Binary (LOLBin) abuse
  - Identify Office-spawned scripting behavior
  - Apply risk-based scoring and severity classification
  - Map detections to MITRE ATT&CK techniques
  - Generate investigation-ready case artifacts
  - Notify analysts via Slack without alert fatigue

tools:
  analysis:
    - Python
    - Pandas
  environment:
    - Jupyter Notebook
  frameworks:
    - MITRE ATT&CK
  integrations:
    - Slack Incoming Webhooks
  output_formats:
    - CSV
    - JSON
    - TXT

detection_pipeline:
  steps:
    - name: Process Event Generation
      description: Synthetic Windows process execution events
    - name: Process Lineage Reconstruction
      description: Parent-child execution chains rebuilt from PID/PPID
    - name: Behavioral Detection
      signals:
        - LOLBins (powershell.exe, certutil.exe, mshta.exe, wscript.exe)
        - Suspicious command-line flags (-enc, -nop, URLs)
        - Office spawning script interpreters
    - name: Risk Scoring
      description: Numerical scoring with severity classification
    - name: MITRE Mapping
      description: Technique inference from execution behavior
    - name: Case Creation
      description: Events grouped into structured case folders
    - name: Alerting
      description: High-risk cases summarized and sent to Slack

risk_scoring:
  severity_levels:
    - name: Low
      score_range: "< 40"
    - name: Medium
      score_range: "40 - 59"
    - name: High
      score_range: "60 - 79"
    - name: Critical
      score_range: "80 - 100"

mitre_mapping:
  approach:
    - Binary-based mapping
    - Chain-based behavioral inference
  example_techniques:
    - T1059.001  # PowerShell
    - T1059.003  # Windows Command Shell
    - T1105      # Ingress Tool Transfer
    - T1218.005  # Mshta
    - T1566.001  # Phishing Attachment

output_structure:
  root: EDR_Labs_Output
  cases:
    structure:
      - critical_alerts.csv
      - high_alerts.csv
      - medium_alerts.csv
      - edr_alerts_all.csv
      - edr_alerts.json
      - summary.txt
      - hashes.txt
  purpose:
    - Incident investigation
    - Evidence preservation
    - Severity-based triage
    - Executive reporting
    - Chain-of-custody style integrity

slack_alerting:
  enabled: true
  threshold:
    score_greater_equal: 70
  behavior:
    - One message per execution
    - Top 3 highest-risk cases only
    - No per-event spam
  message_contents:
    - Case ID
    - Run time
    - Severity
    - Host and user
    - Risk score
    - MITRE ATT&CK techniques
    - Detection signals
    - Full process chain
    - Recommended analyst actions

screenshots:
  intent: Analyst-level visibility
  included:
    - Process lineage reconstruction
    - MITRE ATT&CK mapping
    - Risk score distribution
    - Case artifact folders
    - Slack alert output
  note: >
    Screenshots are curated to demonstrate outcomes and analyst context,
    not step-by-step instructions.

career_relevance:
  demonstrates:
    - Detection engineering mindset
    - Behavioral analysis
    - Alert quality over quantity
    - Automation of SOC workflows
    - Clear communication of security findings
  positioning: >
    Bridges the gap between using an EDR and understanding how one works internally.

future_work:
  - Detection tuning and false-positive suppression
  - Time-window correlation
  - MITRE tactic-level aggregation
  - Confidence scoring
  - SOAR-style response actions
