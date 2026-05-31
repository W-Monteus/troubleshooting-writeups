# No Internet Access — ISP DNS Server Failure Resolved with Public DNS

**Date:** May 2026
**Environment:** Windows 10 desktop, ethernet connection,
home network, remote troubleshooting via phone

---

## Problem
A user reported being unable to load any websites on their
desktop while their phone on the same Wi-Fi network worked
normally. Investigation revealed the router's DNS server
provided by the ISP was failing to resolve domain names,
preventing all web browsing despite a valid network connection.

---

## Symptoms
- No websites loading on desktop
- Phone on same network working normally
- Valid IP address assigned — 192.168.1.x range
- Default gateway reachable
- nslookup returning DNS request timed out
- No recent changes or downloads on the device

---

## Diagnostic Steps
1. Asked about system history and recent changes simultaneously
   while running ipconfig — confirmed no recent changes and
   no outside access to the device
2. ipconfig returned valid IPv4 address 192.168.1.45, subnet
   mask 255.255.255.0, gateway 192.168.1.1, DNS 192.168.1.1 —
   confirmed device had a valid DHCP lease
3. Ran nslookup google.com — returned DNS request timed out
   and Server: UnKnown, confirming DNS resolution was failing
   despite a valid IP configuration
4. Ran ipconfig /release, ipconfig /flushdns, ipconfig /renew
   to refresh network configuration and clear DNS cache
5. Ran nslookup google.com again — still timing out, confirming
   the issue was not resolved by a simple renewal
6. Identified router DNS at 192.168.1.1 as the likely failure
   point — bypassed router DNS by setting Google public DNS
   via: netsh interface ip set dns "Ethernet" static 8.8.8.8
7. Flushed DNS cache and ran nslookup google.com — returned
   Server: dns.google, Address: 8.8.8.8 with valid IP
   resolution confirming router DNS was the problem
8. User confirmed websites loading successfully with Google
   DNS active
9. Identified root cause as likely ISP DNS server outage —
   ISP name servers go down periodically causing DNS
   resolution failures on all devices using the router DNS
10. Configured dual public DNS fallback for long term
    reliability:
    - Primary: netsh interface ip set dns "Ethernet" static 1.1.1.1
      (Cloudflare)
    - Secondary: netsh interface ip add dns "Ethernet" 8.8.8.8 index=2
      (Google)
    - ipconfig /flushdns to apply
11. User tested multiple sites — all loading successfully
    with dual DNS configuration active

---

## Root Cause
The ISP's DNS servers were experiencing an outage causing
all domain name resolution to fail. Despite having a valid
IP address and network connection the device could not
translate domain names into IP addresses making all web
browsing impossible. Bypassing the ISP DNS with reliable
public DNS servers resolved the issue immediately.

---

## Resolution
Setting Cloudflare 1.1.1.1 as primary DNS and Google 8.8.8.8
as secondary DNS via static configuration provided immediate
resolution and long term protection against future ISP DNS
outages. Static DNS settings persist through DHCP renewals
ensuring the public DNS servers remain active without
reconfiguration.

---

## Lessons Learned
When a device has a valid IP address but cannot load websites
while other devices on the same network work normally DNS
failure is the primary suspect — run nslookup immediately
to confirm. DNS request timed out in nslookup confirms the
DNS server is unreachable or non-functional. Bypassing router
DNS with a public server like 8.8.8.8 is both a diagnostic
step and a potential fix — if nslookup succeeds with the
public DNS the router DNS is confirmed as the failure point.
ISP DNS servers experience outages periodically — configuring
dual public DNS servers as primary and secondary provides
reliable fallback protection. Static DNS settings persist
through DHCP renewals and do not need to be reconfigured
when the IP address changes. If DNS appears configured
correctly but specific sites still fail check the hosts
file at C:\Windows\System32\drivers\etc\hosts for corrupted
or tampered entries redirecting legitimate domains.
