# PowerShell Encoded Command

## Summary

This scenario demonstrates execution of a PowerShell command using the `-EncodedCommand` parameter.

---

## Objective

To validate detection of obfuscated PowerShell activity.

---

## Detection Source

- Sysmon Process Creation  
- Wazuh event collection  
- Command-line logging  

---

## Evidence

![Encoded PowerShell](screenshots/powershell-encoded.png)

---

## Analysis

The command line included the `-EncodedCommand` parameter, which is commonly used to obfuscate commands.

This technique is frequently associated with malicious activity because it hides the actual content of the command.

The activity was captured through Sysmon and forwarded to Wazuh for analysis.

---

## Conclusion

The monitoring environment successfully detected encoded PowerShell execution.
