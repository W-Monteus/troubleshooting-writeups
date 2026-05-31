# Progressive Slowdown and Clicking Noise — Failing HDD Diagnosed

**Date:** April 2026
**Environment:** Windows 10 desktop, HDD storage, OneDrive backup,
remote troubleshooting via phone

---

## Problem
A user reported their desktop PC had been getting progressively slower
over several weeks and was producing a loud clicking noise from inside
the case. The user had important files on the device that had not been
backed up. Symptoms indicated potential imminent hard drive failure.

---

## Symptoms
- Loud clicking noise coming from inside the case
- Progressive system slowdown over several weeks
- Storage health warning visible in Windows Security health report
- chkdsk found and repaired errors on the drive
- Clicking noise persisted after chkdsk repair

---

## Diagnostic Steps
1. Identified clicking noise combined with progressive slowdown as
   indicators of potential mechanical hard drive failure — prioritized
   data backup before any diagnostic or repair steps
2. Directed user to back up files via Windows Backup to OneDrive —
   user had insufficient free storage so upgraded to 100GB OneDrive
   plan at $1.99/month to accommodate 30-40GB of files
3. While backup ran, directed user to Windows Security > Device
   Performance and Health — health report showed a storage capacity
   warning, confirming a drive-related issue
4. Once backup completed successfully, ran Disk Cleanup — removed
   approximately 8GB of temporary files, update files, and recycle
   bin contents
5. Ran chkdsk /r /f via Command Prompt — scheduled to run on next
   restart as drive was in active use
6. System restarted and chkdsk completed — found and repaired errors
   on the drive
7. Clicking noise persisted after chkdsk repair — confirmed issue
   was physical mechanical failure rather than a software or
   filesystem error
8. Diagnosed drive as physically failing — clicking noise is a known
   indicator of mechanical component failure in HDDs, commonly
   referred to as the click of death
9. Advised user to replace the drive with an SSD to eliminate the
   risk of mechanical failure entirely
10. Advised user to take the laptop to a local PC repair shop for
    SSD installation if not comfortable performing the swap
    themselves

---

## Root Cause
The hard drive was experiencing mechanical failure. The clicking noise
indicated the drive's read/write heads were failing to locate data
correctly — a physical failure that cannot be resolved through software
repair. chkdsk repaired filesystem errors but had no effect on the
underlying mechanical issue, confirming physical drive failure as the
root cause.

---

## Resolution
All important files were successfully backed up to OneDrive before
any diagnostic steps were taken. User was advised to purchase an SSD
replacement and have it installed at a local PC repair shop. Data is
secure and recoverable from OneDrive onto the new drive once installed.

---

## Lessons Learned
A clicking hard drive combined with progressive slowdown is a data
loss emergency first and a troubleshooting ticket second. Always
secure a backup before running any diagnostic or repair tools on a
potentially failing drive. chkdsk is effective for filesystem errors
but cannot repair physical mechanical failure — if symptoms persist
after chkdsk, physical drive replacement is the only resolution.
Recommending an SSD over a direct HDD replacement eliminates
mechanical failure as a future risk entirely. For future tickets,
CrystalDiskInfo is a useful free tool that reads SMART data directly
from the drive and provides a definitive health status faster than
built-in Windows tools.
