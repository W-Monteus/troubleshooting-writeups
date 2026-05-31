# No Operating System Found on First Boot — New PC Build

**Date:** April 2026  
**Environment:** Custom-built PC (new build), Windows 11, SSD (primary storage),
USB flash drive, BIOS/UEFI firmware  

---

## Problem
A first-time PC builder completed their first custom build and powered it on.
The system successfully posted and entered BIOS but displayed an error stating
no bootable operating system could be found. The machine could not proceed past
this screen.

---

## Symptoms
- System posted successfully — hardware was recognized by BIOS
- BIOS displayed "No bootable device found" or equivalent error
- SSD was visible in BIOS storage devices list
- No operating system present on the drive

---

## Diagnostic Steps
1. Confirmed system posted and entered BIOS successfully — ruled out hardware
   failure as the cause
2. Asked the user whether an operating system had been installed onto the SSD
   prior to building — confirmed no OS had been installed
3. Identified root cause immediately: blank SSD with no OS, nothing to boot into
4. Downloaded Windows 11 ISO from Microsoft's official website onto a separate
   machine
5. Used Rufus (free tool) to flash the Windows ISO onto a USB flash drive,
   creating a bootable installation drive
6. Inserted USB flash drive into the new PC
7. Rebooted and entered BIOS boot menu
8. Confirmed BIOS recognized the USB flash drive as a bootable device
9. Adjusted boot order to prioritize the USB flash drive above the SSD
10. Saved BIOS settings and rebooted
11. System successfully booted into Windows installation media
12. Proceeded through Windows setup and installed OS onto the SSD

---

## Root Cause
New SSDs ship blank with no operating system. First-time builders often assume
the OS comes pre-installed or is included with the hardware. The SSD needed a
fresh Windows installation before the system could boot into an operating system.
BIOS was functioning correctly — it simply had no bootable media to load.

---

## Resolution
Created a bootable Windows 11 USB installation drive using Rufus, modified the
BIOS boot order to prioritize the USB drive, and successfully installed Windows
onto the SSD. System booted into Windows on the next restart after installation
completed.

---

## Lessons Learned
- A system that posts and enters BIOS successfully is not broken — missing OS
  and hardware failure produce similar symptoms but have very different causes
- Always verify whether an OS has been installed before assuming a boot failure
  is hardware-related
- APIPA addresses and "no bootable device" errors are both examples of a system
  working correctly but missing a required component
- Rufus is the fastest and most reliable free tool for creating bootable Windows
  USB drives — keep it bookmarked
- Boot order in BIOS must be set to prioritize installation media when performing
  a fresh OS install — defaults typically prioritize the primary drive which has
  nothing on it yet
