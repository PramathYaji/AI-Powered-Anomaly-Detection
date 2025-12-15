# AI-Powered-Anomaly-Detection

## Overview

This project implements an **AI-driven anomaly detection pipeline** for cybersecurity monitoring.  
The system learns **normal endpoint and network behavior** and detects **unknown, previously unseen attacks** without relying on static signatures or predefined rules.

The project simulates the work of a **Detection Engineer / SOC Automation Engineer** by combining:
- Security telemetry (logs, processes, network)
- Feature engineering grounded in cybersecurity
- Machine learning–based anomaly detection
- Explainable alerts mapped to **MITRE ATT&CK**

---

## Problem Statement

Traditional security systems rely heavily on:
- Signature-based detection
- Static correlation rules
- Known attack patterns

These approaches fail against:
- Zero-day attacks
- Living-off-the-land techniques
- Low-and-slow intrusions

### Solution

This project builds an **AI-based anomaly detection engine** that:
- Learns baseline behavior automatically
- Flags deviations indicative of malicious activity
- Detects attacks without explicit attack signatures

---

## System Architecture

[[]]


---

## Data Sources

### Authentication Logs
- SSH login attempts
- Successful vs failed logins
- Login time patterns
- Source IP diversity

### Process Execution
- New process creation
- Command-line arguments
- Parent–child process relationships
- Privilege escalation attempts

### Network Activity
- Outbound connections
- New destination IPs/domains
- Unusual ports
- DNS query patterns

Logs are collected from Linux systems and optionally Windows Event Logs (4624, 4625).

---

## Feature Engineering (Security-Driven)

Feature engineering is **security-focused**, not generic ML.

### Example Features

| Category | Feature |
|--------|--------|
| Auth | Login attempts per hour |
| Auth | Failed / successful ratio |
| Auth | New IP addresses |
| Process | New binaries executed |
| Process | Rare parent-child pairs |
| Network | New outbound destinations |
| Network | Unusual port usage |
| Temporal | Time-of-day deviation |

These features capture **behavioral patterns**, not static indicators.

---

## Machine Learning Approach

### Primary Model: Isolation Forest
- Unsupervised learning
- Learns normal behavior
- Efficient on high-dimensional security data
- Commonly used in UEBA / XDR platforms

### Optional Advanced Model
- Autoencoder neural network
- Reconstruction error used as anomaly score

---

## Detection & Alerting

The system generates alerts when anomaly scores exceed a defined threshold.

### Example Alert
[[]]


---

## Attack Simulations

The following attacks are simulated to evaluate detection capability:
- SSH brute-force attack
- Reverse shell execution
- Privilege escalation attempts
- Persistence via cron jobs
- DNS tunneling
- Suspicious outbound network activity

Attacks are **not explicitly labeled during training** to preserve realism.

---

## Evaluation Metrics

- True Positive Rate
- False Positive Rate
- Detection latency
- Alert explainability
- Comparison against rule-based detection

### Results Summary
- Detected previously unseen attacks
- Identified behavioral anomalies missed by static rules
- Reduced dependency on signature-based detection

---
## Threat Model

| Threat | Technique | Mitigation |
|------|----------|-----------|
| Credential Abuse | Brute-force | Behavioral detection |
| Malware Execution | Reverse shell | Process anomaly |
| Persistence | Cron abuse | Temporal deviation |
| C2 Communication | DNS tunneling | Network anomalies |

Threats are mapped to **MITRE ATT&CK** for analyst usability.

---

## How to Run

1. Deploy a Linux VM (Ubuntu recommended)
2. Enable authentication, process, and network logging
3. Collect baseline (normal) activity data
4. Run feature extraction scripts
5. Train the anomaly detection model
6. Launch attack simulations
7. Observe alerts and dashboard output

---

## Key Skills Demonstrated

- Cybersecurity telemetry analysis
- Feature engineering for security data
- Machine learning for anomaly detection
- SOC alert design and explainability
- MITRE ATT&CK mapping
- Adversarial testing and validation

---

## Future Enhancements

- Real-time streaming with Kafka
- LLM-based alert summarization
- Endpoint process tree visualization
- SIEM integration
- Online learning for adaptive baselines

---

## ⚠️ Disclaimer

This project is intended **for educational and research purposes only**.  
All attack simulations are conducted in a controlled lab environment.
