# Switch Uplink Down — Incorrectly Terminated RJ45 Causing Full Segment Outage

**Date:** May 2026
**Environment:** Commercial office network, IDF/MDF architecture,
managed switch recently relocated to new rack, Cat5e/Cat6 cabling,
10 affected users

---

## Problem
Ten users on the same network segment simultaneously lost internet
connectivity and began pulling APIPA addresses (169.254.x.x)
following a switch relocation to a new rack the previous week.
Users on other segments were unaffected. Investigation revealed
a faulty RJ45 termination on the switch uplink cable had broken
the transmit pair causing complete uplink failure.

---

## Symptoms
- 10 users simultaneously pulling APIPA addresses
- Limited connectivity warnings on all affected workstations
- Users on opposite side of office unaffected
- All affected users connected through the same switch
- Switch had been physically relocated to a new rack the previous week
- DHCP server confirmed functioning — other segments unaffected

---

## Diagnostic Steps
1. Identified all affected users connecting through the same switch —
   isolated issue to that switch or its uplink rather than DHCP
   server or broader network
2. Physically inspected the switch in the rack — all 10 user ports
   showing green link lights confirming user connections intact
3. Identified uplink port connecting switch to IDF patch panel
   showing no link light — confirmed uplink failure
4. Noted uplink cable had been reinstalled during the rack relocation
   the previous week — flagged as likely cause
5. Ran cable tester on uplink cable — wires 3 and 6 showing open
   circuit. Wires 3 and 6 are the transmit pair (White/Green and
   Green in 568B standard) — confirmed faulty termination as cause
   of dead uplink
6. Visually inspected both RJ45 connectors — patch panel end showed
   one wire not fully seated in the connector. Switch end appeared
   correctly terminated
7. Cut the damaged RJ45 connector off the patch panel end of the cable
8. Stripped approximately 1.5 inches of outer jacket
9. Untwisted and arranged wires in 568B order:
   White/Orange, Orange, White/Green, Blue, White/Blue, Green,
   White/Brown, Brown
10. Trimmed wires to uniform length, inserted into new RJ45 connector
    ensuring all wires fully seated and jacket inside strain relief
11. Crimped connector with crimping tool
12. Tested reterminated cable — all 8 wires passing, correct pin order
13. Plugged cable back into patch panel and switch uplink port —
    green link light appeared immediately
14. Confirmed with affected users — all 10 workstations now showing
    valid 192.168.1.x DHCP addresses with populated gateway and DNS

---

## Root Cause
During the switch relocation the uplink cable was reterminated at
the patch panel end. Wires 3 and 6 — the transmit pair — were not
fully seated into the RJ45 connector during termination. Without
the transmit pair the switch could not establish a physical link
with the upstream IDF equipment. Because the DHCP server lives
upstream of the IDF the 10 affected users could not send DHCP
discover packets through the dead uplink and defaulted to APIPA
addressing. Users on other segments were unaffected because they
connect through different switches with intact uplinks.

---

## Resolution
Reterminating the patch panel end of the uplink cable in correct
568B wiring order and verifying with a cable tester restored the
uplink immediately. All 10 users received valid DHCP leases within
seconds of the uplink coming online.

---

## Lessons Learned
Always test cables with a cable tester before and after any
equipment move — a marginal or incorrectly terminated connection
may not be obvious visually but will fail immediately under
real network traffic. A dark uplink port after a move should
always be investigated before assuming a configuration issue —
check the physical cable first. When an entire switch segment
loses DHCP simultaneously with other segments unaffected the
uplink is almost always the failure point. Users connected to
an isolated switch can still communicate with each other at
Layer 2 but cannot reach upstream services like DHCP, DNS,
or the internet. For future equipment moves: label all cables
before unplugging, photograph rack and patch panel port
assignments, test all cables before and after, and verify
all link lights immediately after the move before leaving
the site.

---

## Additional Notes
On Cisco and most managed switches verify uplink port state
via CLI before pulling cables — a port can be administratively
shut down producing the same dark link light as a physical
failure. Run show interface status or show interfaces to
confirm port state before assuming a cable fault.
