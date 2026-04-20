# wazuh-siem
SOC Lite implementation using Wazuh SIEM with real-world endpoint monitoring, detection, and analysis



# Wazuh SIEM – SOC Lite Implementation

## Overview

This project demonstrates the implementation of a SOC Lite monitoring environment using Wazuh SIEM in a real organizational setup.

The environment includes a centralized Wazuh manager and multiple Windows endpoints, enabling real-time log collection, detection, and analysis of security events.

The project focuses not only on deployment, but also on practical SOC activities such as alert monitoring, event investigation, and identification of suspicious behavior.

---

## Architecture

- Ubuntu-based server hosting:
  - Wazuh Manager
  - Wazuh API
  - Wazuh Dashboard
- 6 Windows endpoints (organizational workstations)
- Wazuh agents installed on all endpoints
- Sysmon deployed for enhanced visibility

### Data Flow

1. Events generated on Windows endpoints
2. Logs collected via Wazuh agents
3. Forwarded securely to Wazuh Manager
4. Processed and visualized in Wazuh Dashboard

---

## Key Capabilities

- Centralized log collection
- Real-time monitoring and alerting
- Endpoint visibility using Sysmon:
  - Process creation
  - Command-line execution
  - Registry changes
  - Network connections
- Detection of suspicious activity
- Security event investigation and documentation

---

## MITRE ATT&CK Mapping

The following techniques were simulated and analyzed:

- **T1547** – Persistence via Registry Run Key  
- **T1110** – Brute Force  
- **T1059** – Command Execution (PowerShell / CMD)  
- **T1087 / T1033** – Discovery (user and system information)  
- **T1105** – Living-off-the-Land (certutil file download)  

---

## Scenarios

### 1. Persistence – Registry Run Key
- Registry key created for persistence  
- Detected via Sysmon Event ID 13  

👉 [View Scenario](scenarios/persistence/explanation.md)

---

### 2. Living-off-the-Land (Certutil)
- Used built-in Windows binary to download file  
- Demonstrates abuse of legitimate tools  

👉 [View Scenario](scenarios/living-off-the-land/explanation.md)

---

### 3. PowerShell Encoded Command
- Executed obfuscated PowerShell command  
- Detected via command-line logging  

👉 [View Scenario](scenarios/powershell-encoded/explanation.md)

---

### 4. Discovery Commands
- Executed:
  - whoami  
  - net user  
- Simulates attacker reconnaissance  

👉 [View Scenario](scenarios/discovery/explanation.md)

---

### 5. Process Chain Analysis
- Observed parent-child relationships:
  - PowerShell → CMD  
  - PowerShell → Notepad  
- Analyzed process execution flow  

👉 [View Scenario](scenarios/process-chain/explanation.md)

---

### 6. Brute Force Attack
- Multiple failed login attempts  
- Detected via Event ID 4625  

👉 [View Scenario](scenarios/brute-force/explanation.md)

---

## Detection Methodology

Each event was analyzed using a structured SOC workflow:

1. Alert triggered in Wazuh
2. Identification of log source (Sysmon / Windows Event Logs)
3. Event analysis:
   - Process name
   - Command line
   - Parent process
   - User context
   - Timestamp
4. Identification of suspicious behavior
5. Documentation of findings and evidence

---


## Configurations

Custom configurations used in this project:

- Sysmon configuration  
  → `configs/sysmon-config.xml`

- Wazuh agent configuration  
  → `configs/ossec-agent-config.xml`

---

## Documentation

Detailed documentation is available under the `docs/` directory:

- Architecture → `docs/architecture.md`
- Setup → `docs/setup.md`
- Configuration → `docs/configuration.md`
- Detections → `docs/detections.md`
- Troubleshooting → `docs/troubleshooting.md`

---

## Key Achievements

- Successfully deployed Wazuh SIEM in a real environment  
- Connected multiple endpoints and verified log ingestion  
- Detected and analyzed multiple attack scenarios  
- Validated visibility into endpoint activity  
- Performed security event investigation using real logs  

---

## Notes

- The environment is based on real endpoint activity  
- Sensitive data has been removed or anonymized  
- The project focuses on detection and analysis rather than offensive execution  

---

## Future Improvements

- Add more advanced attack scenarios  
- Improve detection rules and correlation  
- Expand monitoring to additional endpoints  
- Integrate threat intelligence sources  
