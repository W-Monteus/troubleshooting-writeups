# Cannot Print — Stuck Print Queue and Hung Print Spooler

**Date:** May 2026
**Environment:** Windows 10 desktop, shared network printer
(HP), office environment, remote troubleshooting via phone

---

## Problem
A user was unable to print to a shared office printer. Other
users could print to the same printer without issue. The user
had clicked print five times with no output, and the printer
showed as Offline on her workstation. Investigation revealed
a stuck print queue and a hung print spooler service.

---

## Symptoms
- Single user unable to print
- Printer working normally for all other office users
- User clicked print five times with no output
- Printer showing Offline status on the affected workstation
- Five identical print jobs stuck in the queue

---

## Diagnostic Steps
1. Noted other users could print to the same printer — isolated
   the issue to the affected workstation rather than the printer
   or network
2. Directed user to Settings > Devices > Printers & Scanners —
   located the shared printer showing Offline status
3. Opened the print queue — found five identical stuck print
   jobs from the repeated print attempts
4. Instructed user to cancel all jobs — four cleared but one
   hung on "Deleting..." status indicating a hung print spooler
5. Restarted the Print Spooler service via Win + R > services.msc
   > Print Spooler > right click > Restart
6. Returned to print queue — stuck job cleared, queue empty,
   printer status changed from Offline to Ready
7. User retried printing — document printed successfully

---

## Root Cause
The user clicked print five times when the first job did not
output immediately. The accumulating print jobs overwhelmed
and hung the print spooler service, which caused the printer
to show as Offline and prevented any jobs from processing.
The stuck queue and Offline status were the same underlying
problem rather than two separate issues. Restarting the print
spooler cleared the hung jobs and restored normal printing.

---

## Resolution
Clearing the print queue and restarting the Print Spooler
service resolved the hung spooler, cleared the Offline status,
and restored printing immediately.

---

## Additional Recommendations
- Avoid clicking print repeatedly when a job does not output —
  each click adds another job to the queue and accumulating
  jobs can hang the spooler
- Check the printer queue and status before resending a job
- For stubborn cases where the queue is clear but printing
  still fails: check Printer Properties > Ports tab to confirm
  the printer is mapped to the correct IP or Standard TCP/IP
  port rather than a stale local port
- Use vendor-specific drivers (e.g., HP Universal Print Driver)
  rather than generic Windows drivers to prevent driver-related
  print issues

---

## Lessons Learned
When others can print to a shared printer but one user cannot
the issue is isolated to that workstation — check the print
queue first. A print job hung on "Deleting..." is the classic
sign of a hung print spooler — restarting the Print Spooler
service via services.msc clears it. An Offline printer status
combined with a stuck queue is often the same underlying
problem and resolves together once the spooler is restarted.
Repeated print clicks are a common root cause of stuck queues —
educating the user to avoid this prevents recurrence.
