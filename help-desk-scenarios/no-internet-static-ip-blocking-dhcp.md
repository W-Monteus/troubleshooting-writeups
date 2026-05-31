# No Internet Access — Static IP Preventing DHCP Lease

**Date:** April 2026
**Environment:** Windows 10 desktop, wired ethernet connection,
office network, remote troubleshooting via phone

---

## Problem
A user reported being unable to access the internet while every
other device in the office was connected normally. No recent changes
had been made by the user. Investigation revealed the network adapter
was configured with a static IP address, preventing the DHCP server
from assigning a valid lease.

---

## Symptoms
- No internet access on a single workstation
- All other office devices connected normally
- No recent user-side changes reported
- Physical ethernet cable seated and link light active

---

## Diagnostic Steps
1. Instructed user to open Command Prompt via the taskbar search
2. Ran ipconfig — returned an APIPA address (169.254.43.17),
   subnet mask of 255.255.0.0, and a blank default gateway,
   confirming the device had failed to obtain a DHCP lease
3. Confirmed physical ethernet cable was seated at both the PC
   and wall jack — link light was active, ruling out a physical
   connection issue
4. Ran ipconfig /release followed by ipconfig /renew — system
   still returned an APIPA address, confirming the issue was
   not a simple lease expiration
5. Navigated to Settings > Network & Internet > Change Adapter
   Options > Ethernet Properties > IPv4 — discovered IP
   assignment was configured with a manually entered static IP
   address rather than automatic
6. Asked user if IT had recently worked on the machine — user
   confirmed an IT technician had accessed the device two weeks
   prior for an unrelated issue, likely leaving the static
   assignment in place after the session
7. Switched IPv4 settings to Obtain an IP address automatically
   and Obtain DNS server address automatically
8. Instructed user to restart the system
9. After restart ran ipconfig — returned a valid 192.168.x.x
   address with a populated default gateway, confirming a
   successful DHCP lease
10. User confirmed full internet access restored

---

## Root Cause
The workstation's IPv4 adapter settings had been manually
configured with a static IP address during a previous IT session
and never reverted to automatic. With a static IP set, the device
could not communicate with the DHCP server to obtain a valid
lease. Each time it failed it defaulted to an APIPA address
(169.254.x.x) which blocks internet access entirely.

---

## Resolution
Switching the IPv4 configuration back to automatic assignment
and restarting the system allowed the DHCP server to issue a
valid lease and restored full internet connectivity immediately.

---

## Lessons Learned
An APIPA address (169.254.x.x) is always the starting point
when diagnosing a DHCP failure — it immediately confirms the
device cannot reach the DHCP server. Before assuming the DHCP
server or network infrastructure is at fault, always check
whether the adapter is set to a static IP. If ipconfig /renew
fails twice in a row, go straight to the adapter settings and
check for a static assignment before running any stack-level
commands. When closing any network troubleshooting ticket,
always confirm IP settings are returned to automatic if they
were changed during the session to avoid creating the same
issue for the user down the line.
