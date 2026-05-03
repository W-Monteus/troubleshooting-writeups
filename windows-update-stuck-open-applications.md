# Windows Update Stuck at 35% — Open Applications Causing Installation Conflict

**Date:** April 2026
**Environment:** Windows 10 desktop, Intel Core i5, 8GB RAM,
HDD storage, 4-year-old system, remote troubleshooting via phone

---

## Problem
A user reported their computer was stuck on the Windows update
installation screen at 35% for over two hours with no progress.
The user was hesitant to force restart fearing data loss or system
damage. Investigation revealed open applications during installation
were causing the conflict.

---

## Symptoms
- Windows update installation frozen at 35% for 2+ hours
- No visible progress on screen
- User had been actively using the computer when update started
- Multiple applications open during installation attempt
- System approximately 4 years old with HDD storage

---

## Diagnostic Steps
1. Confirmed update was in the installation phase not download phase
   — network connectivity was not the primary concern
2. Advised user that a force restart during a failed update is safe
   — Windows has automatic rollback protection that reverts the
   system to its pre-update state if installation fails
3. Removed USB hub with flash drive and webcam connected — external
   devices can cause installation conflicts
4. Toggled ethernet connection to refresh network state
5. Asked about system age and how the update was initiated —
   confirmed 4-year-old system and update launched while Excel
   and multiple Chrome tabs were open
6. Identified open applications as likely cause — active processes
   can lock files the update needs to modify, stalling installation
7. With no progress after additional 10 minutes, instructed user
   to force restart by holding power button until shutdown, waiting
   30 seconds, then powering back on
8. System displayed "Restoring your previous version of Windows"
   confirming automatic rollback executed successfully
9. System returned to normal desktop — user saved and closed Excel,
   closed all Chrome tabs, unplugged USB hub
10. Opened Task Manager > Performance tab — confirmed CPU at 8%,
    memory at 42%, no high resource processes running
11. Noted system has HDD storage — advised update would take longer
    than on an SSD due to mechanical read/write limitations, set
    expectation of 30 minutes to 1 hour
12. User initiated update with all applications closed and USB
    devices removed — update progressed immediately and completed
    successfully without intervention

---

## Root Cause
Open applications including Excel and multiple Chrome tabs during
the initial update attempt caused file locking conflicts that
stalled the installation. The system's HDD storage contributed
to slower write speeds, extending the update window and making
the conflict more likely to manifest as a complete stall rather
than a slowdown.

---

## Resolution
Force restarting triggered Windows automatic rollback to the
pre-update state. Closing all open applications, removing external
USB devices, and verifying low resource utilization before the
second attempt allowed the update to complete successfully.

---

## Additional Recommendations
- Enable automatic updates via Settings > Update & Security >
  Windows Update > Advanced Options to ensure updates install
  on a schedule rather than during active work sessions
- Keep Windows updated regularly — delayed updates introduce
  security vulnerabilities and increase the risk of larger
  more complex updates accumulating
- Consider SSD upgrade — SSDs have no moving parts and write
  data significantly faster than HDDs, reducing update times
  and improving overall system performance
- For future stuck updates: run Windows Update Troubleshooter
  via Settings > Update & Security > Troubleshoot before
  attempting a force restart — it catches common issues like
  corrupted update cache automatically

---

## Lessons Learned
Always close all open applications before running a Windows
update — active processes can lock system files the update
needs to modify causing installation to stall. A force restart
during a failed Windows update is safe — Windows rollback
protection automatically reverts the system to its pre-update
state. Setting realistic time expectations based on storage
type before an update attempt prevents user panic if the
process takes longer than expected. HDD systems take
significantly longer to process large updates than SSD systems
due to mechanical read/write limitations. If an update fails
repeatedly after clean attempts, clearing the SoftwareDistribution
folder or running Windows Update Troubleshooter are the next
diagnostic steps.
