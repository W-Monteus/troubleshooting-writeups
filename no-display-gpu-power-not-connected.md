# No Display Output on New PC Build — GPU Not Connected to Power Supply

**Date:** April 2026
**Environment:** Custom-built PC (new build), dedicated GPU, modular
power supply, Windows OS

---

## Problem
A friend reported their newly built PC powered on but produced no display
output. The screen remained black and no keyboard or mouse inputs were
registering. The system appeared to be running but was completely
unresponsive.

---

## Symptoms
- PC powered on — fans spinning, lights active
- No display output — screen remained black
- No keyboard or mouse response
- System appeared to POST but could not be confirmed without display

---

## Diagnostic Steps
1. Confirmed the monitor was functioning — tested with a separate device
2. Checked the display cable connection at both the monitor and GPU ends —
   cable was seated properly
3. Checked power connections from the wall to the surge protector and from
   the surge protector to the PC — all secure
4. Asked the user about the history of the PC — confirmed it was a brand
   new build that had never successfully posted
5. Opened the case to visually inspect internal connections
6. Identified that the GPU had no PCIe power cables connected from the
   power supply — the GPU was seated in the slot but receiving no dedicated
   power
7. Connected the appropriate PCIe power cables from the power supply to
   the GPU
8. Powered the system back on — display output appeared immediately

---

## Root Cause
The GPU was physically installed in the PCIe slot but had not been
connected to the power supply via the required PCIe power cables. Without
dedicated power, the GPU could not produce a display signal. This is a
common oversight in first-time builds — the PCIe slot provides some power
passively, but dedicated GPUs require additional power connectors to
operate. The system powered on because the other components were connected
correctly, but the GPU remained non-functional.

---

## Resolution
Connecting the PCIe power cables from the power supply to the GPU restored
full display output and normal system operation immediately.

---

## Lessons Learned
On new builds with no display output, always open the case and verify all
power connections before assuming a hardware failure. GPUs require both a
PCIe slot connection and dedicated power cable connections from the PSU —
seating the card alone is not sufficient. Modular power supplies require
every cable to be manually connected, which increases the chance of a
missed connection compared to non-modular units.
