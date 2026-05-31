# Outlook Repeatedly Prompting for Password — Misconfigured Account on New Laptop

**Date:** May 2026
**Environment:** Windows 10 laptop, Microsoft Outlook desktop
application, Microsoft 365 work account, IT-provisioned device,
remote troubleshooting via phone

---

## Problem
A user reported Outlook repeatedly prompting for their password
on a newly provisioned work laptop. Entering the correct password
had no effect — the prompt immediately reappeared. The same
account worked correctly in Outlook on the user's previous
desktop and via the browser on the new laptop.

---

## Symptoms
- Outlook desktop app repeatedly prompting for password
- Correct password entered but prompt reappears immediately
- Outlook accessible via browser on the same laptop
- Outlook working normally on previous work desktop
- Laptop provisioned by IT the previous day

---

## Diagnostic Steps
1. Asked what device the user was migrating from and how the
   laptop was configured — confirmed IT provisioned the device
   and installed Outlook the previous day
2. Asked whether the account was personal or work — confirmed
   Microsoft 365 corporate account
3. Asked whether the user could access email via browser —
   confirmed browser access working normally, isolating the
   issue to the Outlook desktop application configuration
4. Checked for Outlook updates via File > Office Account >
   Update Options — confirmed Office was fully up to date
5. Navigated to Settings > Accounts > Email & Accounts —
   located work email account in the list
6. Removed the account and re-added it with work email
   credentials
7. Multi-factor authentication prompt appeared during
   re-authentication — user approved sign-in on phone,
   confirming MFA was functioning correctly
8. Account added successfully — Outlook opened without
   password prompt and emails loaded normally
9. Navigated to File > Account Settings > Change to review
   sync settings — offline mail sync was set to 1 month
10. Changed offline sync to All to ensure full mailbox
    availability on the device

---

## Root Cause
The Outlook profile on the new laptop was misconfigured during
the IT provisioning process. The account credentials were not
properly authenticated for the device resulting in a continuous
password loop. Re-adding the account with proper MFA
authentication established a valid connection between the
Outlook application and the Microsoft 365 account.

---

## Resolution
Removing and re-adding the work account in Settings > Accounts
with MFA approval resolved the password loop immediately.
Offline sync adjusted to All to ensure full mailbox availability.

---

## Additional Recommendations
- If removing and re-adding the account does not resolve a
  persistent password loop — check Windows Credential Manager
  for outdated or corrupted Microsoft Office credentials.
  Search Credential Manager in taskbar > Windows Credentials >
  remove any entries related to Microsoft Office or Outlook
  then re-add the account

---

## Lessons Learned
When Outlook repeatedly prompts for a password on a newly
provisioned device, removing and re-adding the account is
the most effective first step — IT setup processes occasionally
miss completing the full authentication handshake for Microsoft
365 accounts. Always confirm whether the issue is isolated to
the desktop app or affects web access as well — web access
working narrows the issue to application configuration rather
than account or network problems. Multi-factor authentication
prompts during account re-addition are expected and normal for
Microsoft 365 corporate accounts. If removing and re-adding
fails, Windows Credential Manager may be storing corrupted
credentials that prevent successful authentication even with
correct login details.
