# No Display on Boot — Unseated RAM Causing POST Failure

**Date:** April 2026
**Environment:** Windows 10 desktop, dedicated GPU, 2-year-old
system, remote troubleshooting via phone

---

## Problem
A user reported their desktop PC powered on — fans spinning, lights
active — but produced no display output. The screen remained black
on every boot attempt. The system had been working normally the
previous day with no changes made by the user.

---

## Symptoms
- PC powers on — fans and indicator lights active
- No display output — screen completely black
- Monitor confirmed powered on and showing correct input
- Issue appeared overnight with no user-reported changes
- Red DRAM fault indicator light illuminated on motherboard

---

## Diagnostic Steps
1. Asked user whether the system had worked previously or was a
   new build — confirmed working system of approximately 2 years
   with no recent changes, ruling out new build assembly errors
2. Checked display cable connections at both monitor and GPU ends —
   confirmed firmly seated
3. Confirmed display cable was connected to GPU output port, not
   the motherboard integrated graphics port
4. Confirmed monitor was powered on and set to correct input source
5. Swapped display cable for a known working replacement — issue
   persisted, ruling out cable fault
6. Directed user to open the case and inspect the motherboard for
   indicator lights
7. User identified a solid red DRAM fault indicator light near the
   RAM slots — confirmed POST failure due to memory detection issue
8. Instructed user to visually inspect RAM sticks for proper seating
   — user identified one stick showing gold contacts (partially
   unseated) with one end slightly raised
9. Instructed user to power off and unplug the system before
   touching internal components to prevent static damage
10. User pressed the unseated RAM stick firmly until it clicked into
    place — DRAM fault light extinguished immediately
11. While case was open, inspected for dust — found significant
    buildup on fans and CPU heatsink
12. Cleaned fans (holding blades still during spray) and heatsink
    using compressed air
13. Advised user to schedule thermal paste replacement — system is
    approximately 2 years old with visible dust buildup, indicating
    thermal paste may be degraded
14. User reassembled and powered on — system booted successfully
    into Windows

---

## Root Cause
One RAM stick had become partially unseated, preventing the system
from completing POST (Power-On Self-Test). Without successfully
detecting memory, the system could not initialize and produced no
display output. The DRAM fault indicator light on the motherboard
confirmed the memory detection failure. The RAM likely worked loose
over time through minor vibration or thermal expansion and
contraction cycles.

---

## Resolution
Reseating the RAM stick fully resolved the POST failure and restored
normal boot. Dust cleaning performed as preventative maintenance
while the case was open. Thermal paste replacement recommended as
a follow-up given system age and dust buildup history.

---

## Additional Recommendations
- Clean PC every 3 months — more frequently in households with
  pets due to accelerated dust and hair accumulation
- Replace thermal paste — remove CPU heatsink, clean old paste
  with 90% isopropyl alcohol, apply a pea-sized dot of fresh
  paste to the center of the CPU before reseating the heatsink
- Thermal paste can be purchased at local computer shops or online

---

## Lessons Learned
A solid red DRAM fault indicator light on a motherboard is one of
the most recognizable POST failure signatures — it almost always
points to a RAM seating issue or failed RAM stick and should be
checked immediately when present. Always instruct the user to
power off and fully unplug the system before touching internal
components — static discharge or contact with live components can
cause damage. Use an open case as an opportunity for preventative
maintenance — cleaning dust and checking thermal paste costs
little time and prevents future issues. POST failures on a
previously working system that appeared overnight with no user
changes are commonly caused by RAM, GPU, or power delivery issues
rather than software.
