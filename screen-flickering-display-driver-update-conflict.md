# Screen Flickering — Windows Update Introduced Incompatible Display Driver

**Date:** May 2026
**Environment:** Windows 10 laptop, Intel UHD Graphics,
Microsoft Basic Display Adapter, remote troubleshooting
via phone

---

## Problem
A user reported their laptop screen had been flickering
intermittently since the morning. The flickering varied
between constant and occasional pauses. A Windows update
had installed the previous night. Investigation revealed
the update pushed an incompatible Intel display driver
that caused instability between both display adapters.

---

## Symptoms
- Intermittent screen flickering starting the morning after
  a Windows update
- No other system issues reported
- Two Display Adapter entries in Device Manager — Intel UHD
  Graphics and Microsoft Basic Display Adapter
- Yellow warning triangle on Intel UHD Graphics entry

---

## Diagnostic Steps
1. Asked about recent changes and system history — confirmed
   Windows update installed the previous night, flickering
   began the following morning
2. Opened Device Manager — identified yellow warning triangle
   on Intel UHD Graphics under Display Adapters
3. Noted two Display Adapter entries — Intel UHD Graphics and
   Microsoft Basic Display Adapter — abnormal configuration
   indicating a driver conflict
4. Attempted driver rollback via right click > Properties >
   Driver tab > Roll Back Driver on Intel UHD Graphics —
   button greyed out, no previous version stored
5. Attempted same on Microsoft Basic Display Adapter —
   Roll Back Driver also greyed out
6. Navigated to Update Driver > Browse my computer for drivers
   on Intel UHD Graphics — found two previous versions, selected
   most recent prior version from previous month
7. Checked Microsoft Basic Display Adapter for manual version
   selection — only one version available, no older version
   to revert to
8. Theorized the Windows update forced an Intel UHD Graphics
   driver update incompatible with the Microsoft Basic Display
   Adapter — rolling back Intel driver alone may resolve
   incompatibility between both adapters
9. Restarted system to apply Intel driver rollback
10. After restart — screen flickering stopped completely
11. Confirmed Device Manager — yellow triangle on Intel UHD
    Graphics cleared, Microsoft Basic Display Adapter also
    showing no warning triangle

---

## Root Cause
The Windows update pushed a new Intel UHD Graphics driver
version that was incompatible with the Microsoft Basic Display
Adapter driver. The incompatibility between the two display
adapters caused the intermittent screen flickering. Rolling
back the Intel driver to the previous version restored
compatibility between both adapters and resolved the flickering.

---

## Resolution
Manually selecting the previous Intel UHD Graphics driver
version via Device Manager resolved the display driver
incompatibility. Single restart applied the change and
confirmed full resolution.

---

## Lessons Learned
Screen flickering following a Windows update almost always
points to a display driver incompatibility introduced by
the update. Two Display Adapter entries in Device Manager
with warning triangles confirms a driver conflict rather
than a hardware issue. When Roll Back Driver is greyed out
use Browse my computer for drivers to manually select a
previous version. Rolling back one driver in a conflicting
pair can resolve warning indicators on both — the
incompatibility may only originate from one side. Always
make incremental changes and restart between each to isolate
which change produced the fix. Check display refresh rate
and resolution settings first before going into Device
Manager — driver updates sometimes reset display settings
to incompatible values causing flickering that resembles
a driver fault.
