# Random System Freezes — Dust Buildup Causing CPU Overheating

**Date:** April 2026
**Environment:** Windows 10 desktop, air-cooled system, remote
troubleshooting via phone

---

## Problem
A user reported their desktop PC was randomly freezing and becoming
completely unresponsive. The issue required a hard reboot each time
and had been worsening over the course of a week. No error messages
appeared before or during the freeze.

---

## Symptoms
- Random complete system freezes with no error message
- Occurred during both active use and idle periods
- Required hard reboot via power button each time
- Progressively worsening over approximately one week
- No recent software installations or system changes reported

---

## Diagnostic Steps
1. Asked user about recent changes — confirmed nothing new was installed
   or changed prior to the issue starting
2. Asked user to inspect the vents for dust buildup — user confirmed
   significant dust accumulation on side and rear vents
3. Instructed user to power down the system before cleaning
4. Instructed user to remove the side panel to access internal components
   directly rather than spraying through exterior vents — spraying
   through vents risks blowing dust deeper into the system
5. User confirmed heavy dust buildup on both case fans and the CPU
   heatsink
6. Instructed user to hold each fan still while spraying compressed air —
   allowing fans to spin freely during cleaning can damage the bearings
7. User cleaned both fans and cleared packed dust from the CPU heatsink
8. Instructed user to reassemble and boot the system before proceeding
   to thermal paste replacement — to confirm whether cleaning alone
   resolved the issue
9. User booted successfully and opened multiple applications including
   Chrome and Word — system ran stably for 15+ minutes with no freeze
10. Instructed user to open Task Manager and check Performance tab —
    CPU usage at 45%, memory at 60%, CPU temperature reading at 78
    degrees Celsius
11. Confirmed 78C is within normal operating range under load —
    issue considered resolved

---

## Root Cause
Excessive dust buildup on the case fans and CPU heatsink was restricting
airflow and preventing heat from dissipating efficiently. This caused
the CPU to overheat under normal operating conditions, triggering
system freezes as a thermal protection response. The issue worsened
over time as dust accumulation increased.

---

## Resolution
Cleaning the case fans and CPU heatsink with compressed air restored
normal airflow and brought CPU temperatures back to a healthy range.
System ran stably with no freezes following the cleaning.

---

## Additional Recommendations
Advised the user to clean their PC every 3 months. Due to the user
having two cats, pet hair and dander accelerate dust buildup
significantly and may warrant more frequent cleaning closer to every
6-8 weeks.

---

## Lessons Learned
Random freezes with no error message and no recent software changes
should prompt an immediate check of thermals. Dust buildup is one of
the most common and most overlooked causes of system instability,
particularly in households with pets. Always have the user inspect
for dust early in the diagnostic process when troubleshooting
intermittent freezes — it costs nothing and frequently identifies
the issue immediately. When cleaning remotely, instruct the user
to hold fans still during compressed air cleaning to avoid bearing
damage.
