# Process Chain Analysis

## Summary

This scenario analyzes parent-child relationships between processes observed on Windows endpoints.

---

## Objective

To understand process execution flow and identify how commands were launched.

---

## Detection Source

- Sysmon Event ID 1 (Process Creation)  
- Wazuh event collection  

---

## Evidence

### PowerShell (High Integrity)
![PowerShell High](screenshots/powershell-high.png)

### PowerShell (Medium Integrity)
![PowerShell Medium](screenshots/powershell-med.png)

### CMD (High Integrity)
![CMD High](screenshots/cmd-high.png)

### CMD (Medium Integrity)
![CMD Medium](screenshots/cmd-med.png)

### Notepad (High Integrity)
![Notepad High](screenshots/notepad-high.png)

### Notepad (Medium Integrity)
![Notepad Medium](screenshots/notepad-med.png)

---

## Analysis

The collected logs show parent-child relationships between processes such as:

- PowerShell spawning CMD  
- PowerShell spawning Notepad  
- Explorer spawning processes  

Analyzing process chains is important because it provides context around execution behavior and helps identify suspicious activity.

---

## Conclusion

The environment provides visibility into process relationships, allowing deeper understanding of how commands are executed on endpoints.
