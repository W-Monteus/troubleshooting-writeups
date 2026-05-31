# Account Locked Out — Password Expired During Vacation

**Date:** April 2026
**Environment:** Windows 10 desktop, corporate domain environment,
Active Directory, remote troubleshooting via phone

---

## Problem
A user returned from a week of vacation to find their domain account
locked out after multiple failed login attempts. The user was certain
their password was correct but was unable to log in. Investigation
revealed the password had expired during the vacation period,
triggering the lockout after repeated failed attempts.

---

## Symptoms
- Password rejected despite user certainty it was correct
- Account locked out after multiple failed login attempts
- First login attempt after one week away from the office
- No recent password changes made by the user

---

## Diagnostic Steps
1. Asked user if they had recently changed their password —
   confirmed no changes made
2. Asked user what was different about today compared to their
   last successful login — user confirmed they had been on
   vacation for one week and this was their first day back
3. Identified corporate domain environment — account unlocks
   and password resets require IT administrator access via
   Active Directory and cannot be resolved from the user's
   locked workstation
4. Directed user to contact IT administrator to unlock the
   account and issue a temporary password
5. While waiting for IT response, discussed secure password
   management options — recommended Windows Hello biometrics
   (fingerprint or facial recognition) if supported by the
   hardware, and a password manager such as Bitwarden to
   store and autofill complex passwords securely
6. IT administrator confirmed password had expired during the
   vacation period — unlocked the account and issued a
   temporary password requiring reset on next login
7. User logged in with temporary password and created a new
   strong password — advised to use a complex password with
   uppercase, lowercase, numbers, and special characters and
   to avoid personal information
8. User saved new password to password manager — ticket resolved

---

## Root Cause
The user's domain account password expired during a one week
vacation. Corporate password policies enforce expiration on a
set cycle — commonly every 90 days. Because the user was out
of office during the expiration window they did not receive
the standard expiration warning prompts. Repeated failed login
attempts upon return triggered the account lockout threshold
in Active Directory.

---

## Resolution
IT administrator unlocked the account via Active Directory and
issued a temporary password. User created a new strong password
on first login. Password manager and Windows Hello biometrics
recommended to prevent future access issues.

---

## Lessons Learned
A user locked out on their first day back from an extended
absence is a classic password expiration scenario — always
ask about recent time away from the office during initial
intake. In corporate domain environments account lockouts
require IT administrator intervention via Active Directory
and cannot be resolved from the user's workstation. Account
lockouts can also be triggered by connected devices such as
phones or tablets still attempting to authenticate with
cached expired credentials in the background — always ask
about connected devices in future lockout tickets. Recommending
a password manager as a follow-up closes the ticket with a
solution that prevents the same issue from recurring.
