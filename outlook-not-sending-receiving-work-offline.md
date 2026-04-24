# Emails Not Sending or Receiving — Outlook Set to Work Offline

**Date:** April 2026
**Environment:** Windows 10 laptop, Microsoft Outlook, remote
troubleshooting via phone

---

## Problem
A user reported being unable to send or receive emails through Microsoft
Outlook for two days. Emails were stuck in the outbox and no new
emails were arriving despite confirmed attempts from other people
to reach her.

---

## Symptoms
- Outgoing emails stuck in outbox and not sending
- No new emails received for two days
- Outlook application opened and functioned normally otherwise
- Internet connectivity confirmed working on same device

---

## Diagnostic Steps
1. Asked user to verify internet connection — confirmed browsing was
   working normally on the same device, ruling out a connectivity issue
2. Asked user if Outlook had been fully restarted — user had only been
   closing and reopening the laptop lid, not fully closing the
   application. Instructed user to close Outlook completely from the
   taskbar and reopen it
3. User reopened Outlook — issue persisted
4. Directed user to check the status bar at the bottom right of the
   Outlook window for any status indicators
5. User confirmed the status bar displayed "Working Offline"
6. Instructed user to navigate to the Send/Receive tab in the ribbon
   and toggle the Work Offline button to disable offline mode
7. User toggled the setting — "Working Offline" indicator disappeared
   from the status bar immediately
8. Outlook reconnected and 47 pending emails downloaded instantly —
   stuck outbox emails sent successfully

---

## Root Cause
Outlook had been set to Work Offline mode, which prevents the
application from connecting to the mail server regardless of internet
connectivity. The user was unaware the setting had been toggled,
likely accidentally. Because the rest of the application functioned
normally, the user had no indication beyond missing emails that
anything was wrong.

---

## Resolution
Disabling Work Offline mode via the Send/Receive tab restored full
Outlook connectivity immediately. All pending inbound and outbound
emails processed within seconds.

---

## Lessons Learned
When a user reports Outlook not sending or receiving but the
application otherwise opens and functions normally, always check
the Work Offline status before investigating deeper. It is one of
the most common Outlook issues and one of the fastest to resolve.
The status bar at the bottom right of the Outlook window is the
fastest way to identify this — "Working Offline" displays clearly
when the mode is active. Always verify internet connectivity first
to rule out a broader network issue before investigating the
application itself.
