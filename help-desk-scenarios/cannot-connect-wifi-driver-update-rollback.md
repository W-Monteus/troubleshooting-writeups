# Cannot Connect to Office Wi-Fi — Driver Update Pushed by Windows Update

**Date:** May 2026
**Environment:** Windows 10 work laptop, Intel Wi-Fi 6 AX201
adapter, corporate environment, remote troubleshooting via phone

---

## Problem
A user reported their work laptop could not connect to the
office Wi-Fi network with the error "Can't connect to this
network." The user's personal phone connected to the same
network normally. A restart had already been attempted with
no improvement. IT had pushed out updates to all work laptops
the previous day. Investigation revealed a problematic Wi-Fi
adapter driver pushed by the update.

---

## Symptoms
- Cannot connect to office Wi-Fi
- Error message: "Can't connect to this network"
- Phone connects to same network normally
- Restart already attempted with no improvement
- IT pushed updates to work laptops the previous day
- Coworker received same update with no Wi-Fi issue

---

## Diagnostic Steps
1. Confirmed capslock off and correct network selected — ruled
   out fast-fail user error causes
2. Asked about recent changes — confirmed IT-pushed update
   the previous day, no other changes
3. Confirmed the update was workstation only and did not touch
   the phone — ruled out a network side change
4. Asked the user to check with a coworker who received the
   same update — coworker connecting normally, narrowing the
   issue to how the update interacted with this specific machine
5. Ran the built in network troubleshooter via Settings >
   System > Troubleshoot > Other Troubleshooters > Network
   and Internet — completed without identifying or fixing
   the issue
6. Identified driver rollback as the next step — matched the
   suspected cause (update) most directly compared to network
   stack reset
7. Navigated to Device Manager via Win + X > D, expanded
   Network Adapters, located Intel Wi-Fi 6 AX201
8. Properties > Driver tab > Roll Back Driver — button was
   available, indicating a previous driver version existed
   to roll back to
9. Selected "Previous version of the driver performed better"
   as the reason
10. Restarted to finalize the rollback
11. User selected the office Wi-Fi network and connected
    successfully — internet confirmed working

---

## Root Cause
The IT-pushed Windows update installed a new Wi-Fi adapter
driver that was incompatible with the specific hardware or
configuration on this user's laptop. Other workstations with
the same update were unaffected, suggesting the issue was
isolated to a specific hardware variant or pre-existing
configuration on this machine. Rolling back the driver to
the previous working version restored Wi-Fi connectivity
immediately.

---

## Resolution
Rolling back the Wi-Fi adapter driver to the previous version
via Device Manager and restarting restored full network
connectivity. User advised to escalate to IT to consider
blocklisting the problematic driver version on her machine
to prevent recurrence on the next update cycle.

---

## Additional Recommendations
- In a corporate environment driver blocklisting should be
  handled by IT rather than configured by the user — IT can
  prevent the problematic driver from reinstalling across
  any affected machines centrally
- If driver rollback fails or the Roll Back Driver button is
  greyed out on a stubborn case — uninstall the driver entirely
  via Device Manager (check "Delete the driver software for
  this device" if available), restart to allow Windows to
  reinstall the default driver, then assess whether further
  rollback is needed

---

## Lessons Learned
When a single workstation cannot connect to a network after
an IT-pushed update but coworkers with the same update are
fine the issue is workstation specific not update wide —
network driver compatibility is the most common cause. Always
check the obvious fast-fail causes first (capslock, correct
network) before deeper diagnosis. The built in network
troubleshooter is a low cost first step but rarely fixes
driver-level issues — use it to rule out the simple things
and move on quickly. Driver rollback is the right move when
the suspected cause is a recent update — match the fix to
the suspected cause rather than running every tool available.
In a corporate environment escalate driver blocklisting to
IT rather than configuring it on the user's machine.
