# Random Wi-Fi Disconnections — Bluetooth Interference After Router Upgrade

**Date:** April 2026
**Environment:** Windows 10 laptop, Intel Wireless AC-9560 adapter,
Bluetooth mouse, recently upgraded home router, remote
troubleshooting via phone

---

## Problem
A user reported their laptop had been randomly disconnecting from
Wi-Fi multiple times daily for approximately one week. Manual
reconnection was required each time. All other devices on the same
network remained connected, ruling out a router issue. Investigation
revealed a combination of a driver fault and a Bluetooth coexistence
setting conflict triggered by a recent router upgrade.

---

## Symptoms
- Random Wi-Fi disconnections multiple times per day for one week
- Manual reconnection required each time
- Notification on disconnect referencing network adapter
- All other devices on same network unaffected
- Bluetooth mouse in regular use on the same laptop
- Router recently upgraded by ISP approximately one week prior

---

## Diagnostic Steps
1. Asked when issue started and whether any notification appeared
   on disconnect — user confirmed issue began approximately one week
   ago and a notification referencing the adapter appeared on each
   disconnect
2. Asked whether anyone else had access to the laptop — confirmed
   12-year-old son uses it occasionally
3. Directed user to Device Manager — located Intel Wireless AC-9560
   under Network Adapters with a yellow warning triangle
4. User opened device Properties — Device Status showed Code 43,
   confirming Windows detected a problem with the adapter
5. Ruled out physical damage as primary cause — no confirmed drop
   or physical incident reported. Proceeded with driver
   reinstallation to rule out software cause first
6. Uninstalled the adapter driver via Device Manager — system
   restarted and Windows automatically reinstalled the driver
7. Yellow triangle cleared after reinstall — Code 43 resolved,
   confirming the issue was driver-related not hardware failure
8. Navigated to Control Panel > Network and Sharing Center >
   Change Adapter Settings — confirmed adapter was active and
   not disabled
9. Opened adapter Properties > Advanced tab to review settings
10. Identified Transmit Power set to Medium (5) — changed to
    Highest to maximize signal strength and reduce drop risk
11. Identified Bluetooth Collaboration set to Enabled — user
    confirmed regular use of a Bluetooth mouse
12. Asked whether disconnections correlated with Bluetooth mouse
    use — user confirmed disconnects appeared more frequent during
    mouse use, connecting Bluetooth interference as a likely cause
13. Changed Bluetooth Collaboration setting to Wi-Fi First to
    prioritize Wi-Fi over Bluetooth on the 2.4GHz band
14. User tested with Bluetooth mouse connected for 25 minutes —
    no disconnections occurred
15. Identified root cause: ISP had upgraded router approximately
    one week prior — new router broadcasting on 2.4GHz created
    direct frequency competition between Wi-Fi and Bluetooth,
    which had not existed on the previous 5GHz-only router

---

## Root Cause
Two contributing factors combined to cause the random disconnections.
First, a driver fault on the Intel wireless adapter caused Code 43
errors — resolved by driver reinstallation. Second, a recent ISP
router upgrade introduced 2.4GHz broadcasting which put Wi-Fi and
Bluetooth in direct frequency competition. With Bluetooth
Collaboration set to Enabled, the adapter was sharing time between
both signals causing intermittent drops whenever the Bluetooth mouse
was in use. Changing the setting to Wi-Fi First resolved the
conflict by prioritizing the Wi-Fi connection.

---

## Resolution
Driver reinstallation cleared the Code 43 fault. Changing Transmit
Power to Highest and Bluetooth Collaboration to Wi-Fi First in the
adapter's advanced settings resolved the random disconnections
entirely. System remained connected for 25 minutes of testing with
the Bluetooth mouse active.

---

## Lessons Learned
Random Wi-Fi disconnections that correlate with Bluetooth peripheral
use are a strong indicator of 2.4GHz frequency interference —
always ask about Bluetooth devices in use when diagnosing wireless
drops. The Advanced tab in adapter Properties contains several
settings that directly affect connection stability including
Transmit Power and Bluetooth Collaboration — these are worth
reviewing on any persistent wireless issue. A router upgrade is a
significant environmental change that can introduce new interference
conflicts that did not previously exist — always ask about recent
network changes during initial intake. Code 43 on a wireless
adapter should be addressed with a driver reinstall before
concluding hardware failure unless physical damage is confirmed.
