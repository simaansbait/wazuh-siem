# Persistence – Registry Run Key

## Summary

This scenario demonstrates persistence through modification of the Windows Registry Run key.

A Run key was created under the current user hive in order to execute a program at system startup.

---

## Objective

To validate that Wazuh and Sysmon can detect registry-based persistence activity.

---

## Command Used

```powershell
New-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "Dont-delete." -Value "notepad.exe" -Force
