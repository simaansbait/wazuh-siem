# Brute Force – Failed Logon Attempts

## Summary

This scenario documents multiple failed login attempts observed in Windows Security logs.

---

## Objective

To validate detection of failed authentication attempts using Wazuh.

---

## Detection Source

- Windows Event ID 4625  
- Wazuh event collection  

---

## Evidence

![Brute Force](screenshots/brute-force.png)

---

## Analysis

The logs show repeated failed login attempts with "unknown user" and "bad password".

This type of activity is important because it may indicate brute-force attacks or unauthorized access attempts.

The events were successfully collected and visible in Wazuh.

---

## Conclusion

The monitoring environment successfully detected failed login attempts and provided visibility into authentication-related activity.
