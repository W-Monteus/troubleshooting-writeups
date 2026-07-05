# No Audio Output — Default Playback Device Stuck on Disconnected Headphones

**Date:** May 2026
**Environment:** Windows 10 laptop, Realtek audio, urgent
ticket with 30 minute time window, remote troubleshooting
via phone

---

## Problem
A user reported total audio loss on her laptop with a red X
on the speaker icon in the system tray. The user had a video
call in 30 minutes creating urgency on the ticket. Investigation
revealed the default playback device was stuck on disconnected
headphones with the laptop speakers disabled — likely caused by
a Zoom session crashing while holding exclusive audio control
the previous day.

---

## Symptoms
- No audio output from any application or system source
- Red X overlay on speaker icon in system tray
- Built in audio troubleshooter reported "No speakers or
  headphones are plugged in"
- Default playback device showing "Headphones - Realtek Audio"
  despite headphones being unplugged
- Speakers and Realtek Digital Output devices both showing as
  Disabled when hidden devices made visible

---

## Diagnostic Steps
1. Ran built in audio troubleshooter via Settings while gathering
   history simultaneously — troubleshooter reported no output
   devices detected and could not auto-fix
2. Asked about recent changes — user disclosed unplugging
   headphones that morning and using Zoom the previous afternoon
3. Identified the audio service or playback configuration as
   likely affected rather than a driver corruption — chose the
   faster fix path given the 30 minute window
4. Opened Settings > System > Sound — confirmed default output
   set to Headphones with no other devices listed in the dropdown
5. Opened Sound Control Panel via the Sound settings link
6. On the Playback tab right-clicked in empty space and selected
   both "Show Disabled Devices" and "Show Disconnected Devices"
7. Identified Speakers - Realtek Audio and Realtek Digital Output
   both marked as Disabled
8. Right-clicked Speakers > Enable, then right-clicked again
   and selected Set as Default Device, clicked Apply
9. Green checkmark moved from Headphones to Speakers confirming
   the change
10. Tested audio playback via YouTube — confirmed working
    through laptop speakers
11. Tested headphone switching — plugged in headphones, audio
    switched automatically, unplugged and audio returned to
    speakers automatically
12. To prevent recurrence — right-clicked Speakers > Properties
    > Advanced tab, unchecked "Allow applications to take
    exclusive control of this device", clicked Apply

---

## Root Cause
A Zoom session the previous afternoon likely crashed or exited
uncleanly while holding exclusive control over the audio device.
When applications hold exclusive control and crash they can
leave Windows audio devices in a disabled state. When the user
unplugged her headphones that morning Windows had no enabled
output device to fall back to since the speakers were still
disabled from the prior Zoom session — resulting in total audio
loss with the red X system tray icon.

---

## Resolution
Enabling the laptop speakers in Sound Control Panel and setting
them as the default device restored audio immediately. Disabling
exclusive application control prevents future application crashes
from leaving the audio device in a disabled state.

---

## Additional Recommendations
- For stubborn audio issues that resist playback device changes —
  restart the Windows Audio service via services.msc (similar
  pattern to the Print Spooler restart for printer issues)
- Read troubleshooter output carefully — error messages like
  "No speakers or headphones are plugged in" are literal clues
  pointing at the playback device configuration rather than
  hardware or driver issues

---

## Lessons Learned
When the built in troubleshooter reports an output device error
the playback device configuration should be checked first before
assuming a driver or hardware issue — the error message is often
a direct clue. Always show Disabled and Disconnected Devices in
Sound Control Panel when diagnosing audio loss — the missing
playback device is frequently disabled rather than absent.
Applications holding exclusive audio control can leave devices
disabled when they crash — disabling exclusive control on the
default device prevents this class of issue. Under time pressure
choose the fastest fix that matches the suspected cause rather
than running every diagnostic tool available. Test both the
immediate fix and any related behaviors (like headphone switching)
before closing to confirm full resolution.
