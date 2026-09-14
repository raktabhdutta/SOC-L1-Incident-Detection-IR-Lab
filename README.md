# SOC L1 Incident Detection & Incident Response Lab

A controlled SOC Level 1 incident detection and incident response laboratory demonstrating practical security monitoring, alert triage, Windows event-log analysis, PowerShell investigation, Sysmon telemetry analysis, IOC identification, incident timeline reconstruction, severity assessment, containment recommendations and escalation decision-making.

## Project Overview

This project simulates a suspected workstation compromise within a controlled virtual laboratory environment.

The investigation uses a Kali Linux analyst workstation and a Windows 10 victim endpoint to generate and analyse security telemetry associated with:

- Failed authentication
- Successful authentication
- PowerShell execution
- Process creation
- Network connections

The investigation correlates multiple telemetry sources to determine what occurred, assess whether compromise was confirmed, identify investigation indicators and recommend an appropriate SOC response.

> **Important:** All security activity in this repository was intentionally generated within an isolated laboratory environment. The identified IP addresses, commands and other artefacts are laboratory-generated investigation indicators and should not be interpreted as confirmed malicious IOCs.

## Lab Architecture

The laboratory consists of two virtual machines connected through an isolated VirtualBox Host-only network.

| Component | Role | IP Address | Operating System |
|-----------|------|------------|------------------|
| Kali Linux | SOC Analyst Workstation | 192.168.56.102 | Kali Linux 2025.3 |
| Windows 10-Lab | Victim Endpoint | 192.168.56.101 | Windows 10 Pro |

### Network Design

```text
                 VirtualBox Host-only Network
                       192.168.56.0/24
                              |
             +----------------+----------------+
             |                                 |
             |                                 |
      Kali Linux 2025.3                 Windows 10 Pro
      SOC Analyst VM                    Victim Endpoint
      192.168.56.102                    192.168.56.101
             |                                 |
             +----------- Investigation -------+
```

## Detection & Investigation

The investigation follows a SOC L1 workflow from initial detection through evidence correlation and incident classification.

### Telemetry Sources

The investigation uses the following Windows telemetry sources:

- Windows Security Event Log
- PowerShell Operational Event Log
- Sysmon Operational Event Log

### Key Security Events

| Event ID | Telemetry | Investigation Purpose |
|----------|-----------|-----------------------|
| 4625 | Failed Authentication | Identify unsuccessful authentication attempts |
| 4624 | Successful Authentication | Validate successful account authentication |
| 4104 | PowerShell Script Block | Identify and analyse PowerShell activity |
| Sysmon 1 | Process Creation | Identify processes and command-line activity |
| Sysmon 3 | Network Connection | Identify network connections associated with processes |

### Investigation Flow

```text
Initial Alert
     |
     v
Authentication Analysis
     |
     v
PowerShell Investigation
     |
     v
Process Creation Analysis
     |
     v
Network Connection Analysis
     |
     v
IOC Identification
     |
     v
Incident Timeline Reconstruction
     |
     v
Severity & Impact Assessment
     |
     v
Containment Recommendations
     |
     v
Escalation Decision
```

## Investigation Findings

The controlled investigation produced the following findings:

- A failed authentication attempt was observed against the Windows endpoint.
- A subsequent successful authentication from the Kali analyst workstation was observed.
- PowerShell Script Block Logging captured the controlled PowerShell test activity.
- Sysmon Event ID 1 recorded the associated PowerShell process creation.
- Sysmon Event ID 3 recorded controlled network activity between the laboratory endpoints.
- The observed activity was correlated across multiple telemetry sources.
- No confirmed malicious payload execution was identified.
- No persistence, lateral movement or data exfiltration was identified.
- No confirmed system compromise or business impact was identified.

### Final Classification

**Classification:** Suspicious Activity – Controlled Security Simulation

**Severity:** Medium

**Compromise Confirmed:** No

**Business Impact:** None identified

**Lab Status:** Closed – Controlled Laboratory Exercise

## Evidence & Documentation

The repository contains supporting evidence and documentation for the investigation.

### Evidence

Key investigation evidence includes:

- Windows Event ID 4625 — Failed Authentication
- Windows Event ID 4624 — Successful Authentication
- PowerShell Event ID 4104 — Script Block Logging
- Sysmon Event ID 1 — PowerShell Process Creation
- Sysmon Event ID 3 — Network Connection
- Sysmon Active Rules Verification

### Investigation Report

The complete investigation report is available in:

`Incident-Report/SOC-L1-Incident-Investigation-Report.docx`

### Supporting Documentation

Additional project documentation includes:

- Lab environment configuration
- Sysmon configuration
- Windows investigation queries
- Incident timeline and IOC summary
- Investigation evidence and screenshots

## Repository Structure

```text
SOC-L1-Incident-Detection-IR-Lab/
│
├── README.md
│
├── Incident-Report/
│   └── SOC-L1-Incident-Investigation-Report.docx
│
├── Evidence/
│   ├── Kali-to-Windows-Failed-Logon-4625.png
│   ├── Kali-to-Windows-Successful-Logon-Event-4624.png
│   ├── PowerShell-Script-Block-Event-4104.png
│   ├── Sysmon-PowerShell-Process-Creation-Event-ID-1.png
│   ├── Sysmon-NetworkConnect-Event3.png
│   └── Sysmon-Active-Rules-Verified.png
│
├── Screenshots/
│
├── Queries/
│   └── windows-event-queries.txt
│
├── Configuration/
│   └── sysmon-lab.xml
│
└── Documentation/
    └── lab-environment.txt
```

## Skills Demonstrated

This project demonstrates practical SOC L1 and incident response capabilities, including:

- Security event monitoring and log analysis
- Windows authentication event investigation
- PowerShell activity investigation
- Sysmon telemetry analysis
- Process creation analysis
- Network connection analysis
- IOC identification
- Incident timeline reconstruction
- Incident classification and severity assessment
- Impact assessment
- Containment recommendations
- Escalation decision-making
- Evidence collection and documentation
- Security investigation using Windows Event Logs and Sysmon
- Controlled security simulation and validation

## Disclaimer

This project was developed strictly for educational, portfolio and cybersecurity skills-development purposes.

All security testing and simulated incident activity was performed within an isolated VirtualBox Host-only laboratory environment controlled by the author.

The IP addresses, usernames, commands, authentication attempts and other artefacts documented in this repository are laboratory-generated data.

No production systems, third-party systems or unauthorised networks were targeted during this exercise.
