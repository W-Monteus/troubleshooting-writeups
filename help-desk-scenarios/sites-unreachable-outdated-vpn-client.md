# Specific Sites Unreachable — Outdated VPN Client Causing Limited Network Access

**Date:** May 2026
**Environment:** Windows 10 desktop, corporate VPN client,
office network, remote troubleshooting via phone

---

## Problem
A user reported being unable to access specific websites including
the company internal portal despite having normal internet
connectivity on other sites. All other office devices could access
the affected sites without issue. The user was connected to the
corporate VPN but experiencing limited traffic flow.

---

## Symptoms
- General internet browsing working normally
- Specific sites unreachable — company internal portal affected
- Other office devices accessing same sites without issue
- VPN showing as connected with green status indicator
- "Limited network access" warning visible in VPN client
- Issue appeared overnight — worked normally the previous afternoon

---

## Diagnostic Steps
1. Asked how the user normally accesses the internal portal —
   confirmed VPN is required for company internal sites
2. Asked when the site last worked — confirmed working the
   previous afternoon with no changes made since
3. Directed user to open VPN client and review status —
   client showed Connected with green indicator but displayed
   a "Limited network access" warning at the bottom of the
   interface
4. Limited network access warning confirmed VPN was connected
   at the authentication level but traffic was not flowing
   through the tunnel correctly
5. Checked VPN client version — confirmed running version 4.2.1
   with version 4.3.0 available as a pending update
6. Instructed user to update the VPN client — client updated
   and reconnected automatically
7. Confirmed "Limited network access" warning cleared after
   update and reconnection
8. User tested internal portal — loaded successfully
9. User tested four additional previously unreachable sites —
   all loaded successfully

---

## Root Cause
The VPN client was running an outdated version that caused
instability in the network tunnel. While the client authenticated
successfully and showed as connected, the outdated version was
unable to maintain stable traffic flow through the tunnel,
resulting in the "Limited network access" state. Updating to
the current version resolved the tunnel stability issue.

---

## Resolution
Updating the VPN client from version 4.2.1 to 4.3.0 restored
full tunnel connectivity. All previously unreachable sites
became accessible immediately after the update and reconnection.
Automatic updates enabled in VPN client settings to prevent
recurrence.

---

## Additional Recommendations
- Enable automatic updates in VPN client settings to ensure
  the client stays current without manual intervention
- If automatic updates are unavailable set a weekly reminder
  to check for VPN client updates manually

---

## Lessons Learned
When a user reports specific sites unreachable while general
internet works normally always ask about VPN requirements
first — internal company portals almost always require VPN
access. A VPN showing as connected does not guarantee traffic
is flowing correctly — always check for warning messages within
the client interface. "Limited network access" on a VPN client
indicates authentication succeeded but tunnel stability has
failed. For future VPN connectivity issues try disconnect and
reconnect before updating — it costs seconds and sometimes
resolves stuck connections without further steps. If an update
does not resolve limited access the next diagnostic step is
checking for DNS conflicts using ipconfig /flushdns followed
by ipconfig /renew.
