# Repeated Blue Screens — Failing Hard Drive Detected via Event Viewer

**Date:** April 2026
**Environment:** Windows 10 desktop, Intel Core i5, 4GB RAM,
HDD storage, remote troubleshooting via phone

---

## Problem
A user reported two blue screen events within one hour, both forcing
an automatic restart. The system functioned normally between crashes
with no error messages visible to the user. Investigation via Event
Viewer identified a failing hard drive as the root cause.

---

## Symptoms
- Two blue screen events within one hour
- System restarted automatically each time
- No error message visible to user before crash
- Normal system operation between blue screen events
- Chrome and Excel open simultaneously prior to crashes

---

## Diagnostic Steps
1. Asked user what they were doing before each blue screen — first
   occurred while browsing Chrome, second while opening Excel
2. Asked user what browser they use — confirmed Google Chrome
3. Opened Task Manager > Performance tab to check system specs —
   Intel Core i5, 4GB RAM total at 67% utilization, identified
   low RAM as a potential contributing factor given Chrome and
   Excel running simultaneously
4. Navigated to Event Viewer via taskbar search > Windows Logs >
   System to review crash logs
5. Filtered by Critical events — found two Event ID 41 Kernel-Power
   entries matching the exact timestamps of both blue screens.
   Event ID 41 Kernel-Power indicates the system shut down without
   a clean shutdown sequence, commonly caused by hardware issues
   such as faulty RAM, failing PSU, or failing storage
6. Filtered by Critical and Error events around the same timestamps
   — found Event ID 7 Disk errors logged immediately before each
   Kernel-Power 41 event. Event ID 7 indicates bad blocks detected
   on the physical drive, a sign of physical drive failure
7. Ran Windows Memory Diagnostic to rule out faulty RAM as a cause
   — system restarted into the diagnostic tool, completed Pass 1
   and Pass 2, returned result of no memory errors detected
8. With RAM ruled out and Event ID 7 Disk errors confirmed,
   identified failing hard drive as the root cause
9. Instructed user to immediately back up all important files to
   OneDrive before any further action
10. User confirmed backup completed successfully
11. Advised user to replace the drive with an SSD and have it
    installed at a local PC repair shop

---

## Root Cause
The hard drive was developing bad sectors — areas of physical damage
on the drive that are permanently unreadable. Unlike file system
corruption which can sometimes be repaired with software tools,
bad sectors are physical damage and cannot be fixed. When the system
attempted to read data from a bad sector it triggered a Kernel-Power
failure event resulting in a blue screen. Event Viewer logs confirmed
the pattern: Disk Event ID 7 bad block error immediately preceding
each Kernel-Power Event ID 41 crash.

---

## Resolution
All important files were backed up to OneDrive before further
action. User was advised to replace the failing HDD with an SSD
to eliminate the risk of mechanical failure entirely.

---

## Additional Notes
User had 4GB of RAM with Chrome and Excel running simultaneously.
While insufficient RAM was not the root cause of the crashes,
it is a contributing performance factor. An SSD upgrade combined
with a RAM upgrade from 4GB to 8GB would significantly improve
overall system stability and performance.

---

## Lessons Learned
Event Viewer is one of the most effective tools for BSOD diagnosis.
The combination of Kernel-Power Event ID 41 and Disk Event ID 7
is a classic failing drive signature — when both appear together
in the logs, physical drive failure should be the primary suspect.
Bad sectors are physical damage and cannot be repaired by software
tools like chkdsk — drive replacement is the only resolution.
Always ask about recent ticket history during initial intake — in
this case the user had a previous ticket involving a failing drive
on another machine. Identifying that pattern earlier would have
accelerated the diagnosis significantly.
