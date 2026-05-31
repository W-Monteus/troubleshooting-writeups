# User Cannot Access Shared Drives — Machine Not Joined to Domain After Reimage

**Date:** May 2026
**Environment:** Windows 10 workstation, corporate Active Directory
domain, Wi-Fi connected, machine recently reimaged by IT department,
marketing department

---

## Problem
A marketing department user could browse the internet normally
but could not access shared drives or internal applications after
their workstation was reimaged the previous Friday. All other
marketing users were unaffected. Investigation revealed the
machine had not been rejoined to the Active Directory domain
after the reimage and DNS was incorrectly pointed at a public
resolver instead of the Domain Controller.

---

## Symptoms
- Internet access working normally
- Shared drives not mapping
- Internal applications not accessible
- All other marketing users unaffected
- Machine reimaged by IT the previous Friday
- Issue began immediately after reimage

---

## Diagnostic Steps
1. Identified reimage as the likely root cause — reimaged machines
   require domain rejoin and DNS reconfiguration to restore access
   to internal resources
2. Directed user to Settings > System > About > Advanced System
   Settings > Computer Name tab — confirmed machine showing
   Workgroup: WORKGROUP instead of company domain, confirming
   machine was not domain joined
3. Ran ipconfig /all — DNS server showing 8.8.8.8 (Google public
   DNS) instead of the Domain Controller IP
4. Retrieved correct DNS/DC IP from a working marketing machine
   via ipconfig /all — confirmed DC IP as 192.168.10.10
5. Confirmed user was on Wi-Fi not ethernet before running
   network commands
6. Updated DNS to point at Domain Controller via command line:
   netsh interface ip set dns "Wi-Fi" static 192.168.10.10
7. Verified DNS change via ipconfig /all — confirmed DNS now
   showing 192.168.10.10
8. Retrieved company domain name from working machine via
   ipconfig /all DNS Suffix Search List — confirmed domain
   as marketing.local
9. Navigated to Computer Name Changes — selected Domain radio
   button, entered marketing.local
10. Domain join requires administrator credentials — escalated
    to IT department with full context. Documented current state,
    steps completed, and outstanding requirement in ticketing system
11. IT administrator completed domain join with privileged
    credentials — machine restarted
12. User logged in with domain account — shared drives mapped
    automatically via Group Policy, internal applications
    appeared and functioned correctly

---

## Root Cause
The IT technician who performed the reimage did not complete
two critical post-reimage steps — rejoining the machine to
the Active Directory domain and configuring DNS to point at
the Domain Controller. Without domain membership the machine
authenticated users with local accounts that had no access
to domain resources. Without correct DNS pointing at the DC
a domain join could not have been completed even if attempted.

---

## Resolution
Correcting DNS to point at the Domain Controller and rejoining
the machine to the Active Directory domain with administrator
credentials restored full access to shared drives and internal
applications via Group Policy.

---

## Additional Notes
Domain join requires an account with domain join privileges —
this step must be escalated to an IT administrator. Network
technicians should complete all prerequisite steps (DNS
correction, connectivity verification) and document clearly
before escalating to minimize administrator time on site.

After domain join if shared drives or applications do not
populate immediately run gpupdate /force in Command Prompt
to force immediate Group Policy application rather than
waiting for the automatic refresh cycle.

---

## Lessons Learned
A reimaged machine that can access the internet but not
internal resources should immediately raise domain membership
as the primary suspect. Always verify domain join status
first via System Properties > Computer Name before any other
diagnostic steps. DNS must point at the Domain Controller
before a domain join can succeed — verify with ipconfig /all
and correct if pointing at a public resolver. Always confirm
the network adapter name (Ethernet vs Wi-Fi) before running
netsh commands — targeting the wrong adapter fails silently
and leaves the configuration unchanged. Retrieve the DC IP
and domain name from a known working machine on the same
segment rather than relying on documentation that may be
outdated. Ping the DC IP before attempting domain join to
confirm network connectivity to the domain controller as
a prerequisite.
