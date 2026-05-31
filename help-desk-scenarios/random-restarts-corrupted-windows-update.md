# Random Restarts Without BSOD — Corrupted Windows Update Files

**Date:** May 2026
**Environment:** Windows 10 desktop, 2-year-old system, home
environment, remote troubleshooting via phone

---

## Problem
A user reported their desktop PC was restarting randomly without
warning three times in one day. No blue screen appeared before
each restart — the system simply rebooted without notice causing
loss of unsaved work. Investigation via Event Viewer identified
corrupted Windows update files as the root cause.

---

## Symptoms
- Three unexpected restarts in one day with no BSOD
- Restarts occurred during different activities — browsing,
  Excel, and YouTube — ruling out a single application as cause
- No dust buildup and no recent hardware access
- Windows update installed the previous night before restarts began
- Event Viewer showing Event ID 7031 Windows Update service
  termination immediately before each Kernel-Power 41 event

---

## Diagnostic Steps
1. Asked about system history, when issue started, and what
   user was doing during each restart — confirmed 2-year-old
   system with restarts beginning today across varied activities
2. Inspected case for dust — confirmed clean, ruled out thermal
   cause
3. Confirmed no other users had access to the workstation
4. User recalled installing a Windows update the previous night
   before restarts began — identified update as likely cause
5. Opened Event Viewer > Windows Logs > System, filtered by
   Critical — found Kernel-Power Event ID 41 matching each
   restart timestamp
6. Filtered by Critical and Error — identified Event ID 7031
   logged immediately before each Kernel-Power 41 event.
   Event ID 7031 indicates the Windows Update service terminated
   unexpectedly, consistent with corrupted update files or
   driver conflicts introduced by the update
7. Opened Command Prompt as Administrator — ran sfc /scannow
8. SFC scan completed — found and repaired corrupt system files
9. Restarted system to finalize SFC repairs
10. Ran DISM.exe /Online /Cleanup-Image /RestoreHealth to repair
    the Windows component store — optimal order is DISM first
    then SFC, DISM run as a follow up to ensure component store
    integrity after SFC had already completed
11. Ran sfc /scannow again after DISM — returned no integrity
    violations, confirming full repair
12. Restarted system — monitored for 20 minutes with Event
    Viewer open alongside normal work
13. No restarts and no new errors in Event Viewer during
    monitoring period — issue confirmed resolved

---

## Root Cause
The Windows update installed the previous night contained
corrupted files that caused the Windows Update service to
terminate unexpectedly. Each service termination triggered
an unclean system shutdown logged as Kernel-Power Event ID 41.
SFC identified and repaired the corrupted system files.
DISM confirmed component store integrity after repair.

---

## Resolution
Running SFC followed by DISM fully repaired the corrupted
system files introduced by the Windows update. System ran
stably for 20 minutes of monitored use with no further
restarts or Event Viewer errors.

---

## Additional Recommendations
- For quick system file health checks in the future run
  sfc /scannow in Command Prompt as Administrator — it takes
  a few minutes and immediately identifies any corruption
- Optimal repair order when both tools are needed:
  DISM first to repair the component store, then SFC to
  repair individual system files using the restored store
- To check Windows Update history and identify problematic
  updates navigate to Settings > Update & Security >
  Windows Update > View Update History — Microsoft sometimes
  provides a direct uninstall option for known problematic
  updates from this screen

---

## Lessons Learned
Random restarts without a BSOD following a Windows update
should immediately flag the update as a suspect. Event ID
7031 for the Windows Update service terminating unexpectedly
is a strong indicator of corrupted update files or driver
conflicts. Always run DISM before SFC — DISM repairs the
Windows component store that SFC relies on, and running SFC
on a corrupted store can produce incomplete repairs. Running
SFC a second time after DISM confirms whether all corruption
was fully addressed. Monitoring with Event Viewer open after
repairs provides real time confirmation that the fix was
successful before closing the ticket.
