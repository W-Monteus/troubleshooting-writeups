# Quick Reference — Troubleshooting Sequences

A structured first-response checklist for common IT scenarios.
Use these as a starting point before diving deeper into diagnosis.
Each sequence reflects the most efficient diagnostic path based
on real and simulated troubleshooting experience.

---

## 1. No Display Output (New Build)
1. Confirm monitor is working — test with another device
2. Check display cable at both ends
3. Check power connections from wall to surge protector to PC
4. Ask about system history — new build, recent changes
5. Open case — visually inspect all internal power connections
6. Confirm GPU has PCIe power cables connected from PSU
7. Power on and test

---

## 2. System Running Slow
1. Ask when slowdowns occur — idle, browsing, specific apps
2. Open Task Manager > Performance — check CPU, RAM, disk usage
3. Identify resource hog — check Processes tab for high usage
4. If RAM near 100% — identify heavy applications (Chrome, etc.)
5. Check for dust buildup if desktop — inspect fans and heatsink
6. Run Disk Cleanup to free space if disk usage is high
7. Check startup programs — disable unnecessary ones
8. Run Windows Defender scan to rule out malware

---

## 3. No Wi-Fi Adapter Found
1. Ask when issue started and if anything changed recently
2. Check Device Manager — confirm adapter is missing entirely
3. Test wired ethernet — isolates network vs adapter issue
4. If issue started after moving or cleaning — open case
5. Visually inspect Wi-Fi card seating in PCIe slot
6. Reseat card firmly until it clicks
7. Power on and confirm adapter appears in Device Manager
8. Test wireless connectivity

---

## 4. No Internet — Single Device
1. Confirm internet works on other devices — isolates device vs network
2. Run ipconfig — check for APIPA address (169.254.x.x)
3. Check physical cable connection and link light
4. Run ipconfig /release then ipconfig /renew
5. If still APIPA — check adapter settings for static IP
6. If static IP found — switch to automatic, ask about recent IT work
7. Restart device
8. Run ipconfig to confirm valid IP address assigned

---

## 5. Emails Not Sending or Receiving (Outlook)
1. Confirm internet is working on the same device
2. Close Outlook fully from taskbar and reopen
3. Check status bar at bottom right of Outlook window
4. If "Working Offline" displayed — go to Send/Receive tab
5. Toggle Work Offline button to disable offline mode
6. Confirm status bar clears and emails begin syncing
7. Test by sending a test email

---

## 6. Malware / Pop-ups / Browser Hijacking
1. Ask about recent downloads or software installs
2. Uninstall or delete any suspicious recently installed programs
3. Check browser notification permissions — remove unrecognized sites
4. Run Windows Defender full scan
5. Remove all quarantined threats and restart as prompted
6. Check Windows Security — confirm real-time protection is enabled
7. Re-enable real-time protection if disabled
8. Check for other users on device who may have changed settings
9. Create Standard User account for non-admin users if needed
10. Test system stability after restart

---

## 7. BitLocker Recovery Key Prompt
1. Ask if any updates or IT changes occurred recently
2. Direct user to account.microsoft.com on a separate device
3. Locate BitLocker recovery keys in Microsoft account
4. Enter recovery key at boot screen
5. Boot into Windows and confirm access restored
6. Suspend BitLocker via Control Panel > BitLocker Drive Encryption
7. Wait a few minutes then resume protection to refresh state
8. Back up recovery key to Microsoft account if not already done

---

## 8. System Freezes Randomly
1. Ask when freezes occur — idle, specific apps, always
2. Ask about recent changes or new installs
3. Check Task Manager > Performance — CPU, RAM, disk, temperature
4. If temperature high — inspect for dust on fans and heatsink
5. Clean fans and heatsink with compressed air (hold fans still)
6. If freezes persist — run Windows Memory Diagnostic
7. Check Event Viewer > Windows Logs > System for Critical events
8. Look for Kernel-Power 41 and any preceding error events
9. Address root cause based on Event Viewer findings

---

## 9. Blue Screen of Death (BSOD)
1. Ask what user was doing before crash occurred
2. Ask about recent changes, updates, or new hardware
3. Check Task Manager > Performance — note RAM and specs
4. Open Event Viewer > Windows Logs > System
5. Filter by Critical — locate Kernel-Power Event ID 41
6. Filter by Critical and Error — look for events logged just
   before the 41 for the actual cause
7. Common signatures:
   - Disk Event ID 7 — bad sectors, failing drive
   - Event ID 1001 BugCheck — contains stop code, check for driver or RAM issues
   - Event ID 55 NTFS — filesystem corruption, run chkdsk
   - Event ID 129 StorPort — drive response timeout, failing drive
8. Run Windows Memory Diagnostic to rule out RAM
9. If drive related — back up data immediately before further steps
10. Address root cause based on findings

---

## 10. Account Locked Out
1. Ask if password was recently changed
2. Ask if user has been away from office recently — check for expiration
3. Ask if any other devices (phone, tablet) are connected to the account
4. In corporate environment — escalate to IT administrator immediately
5. IT unlocks account via Active Directory and issues temporary password
6. User resets password on first login — advise strong complex password
7. Recommend password manager (Bitwarden) and Windows Hello biometrics
8. Check connected devices — update saved credentials to prevent re-lockout

---

## 11. Printer Not Responding
1. Ask if multiple users are affected — isolates printer vs workstation
2. Check print queue on workstation — Settings > Devices > Printers
   & Scanners > Open Queue — look for error status on jobs
3. Clear any stuck jobs from the queue
4. Check printer display physically for error messages
5. Check all cable connections — power and network
6. Address physical issue (paper jam, out of paper, offline)
7. Use Clear Error or restart printer if error persists after fix
8. Test print to confirm resolution
9. Confirm coworkers can print if multiple users were affected

---

## 12. Failing Hard Drive
1. Ask about symptoms — clicking noise, slowdowns, BSODs
2. Back up all important data immediately before any other steps
3. Run chkdsk /r /f — schedule on next restart if drive is in use
4. Check Event Viewer for Disk Event ID 7 bad block errors
5. Check Event Viewer for Event ID 129 StorPort timeout errors
6. Run CrystalDiskInfo to read SMART data for definitive health status
7. If drive confirmed failing — advise SSD replacement
8. Have user take to local PC repair shop if not comfortable
   with self-installation

---

## 13. USB Device Not Recognized
1. Ask when it last worked and if anything changed since then
2. Ask if device was dropped or physically mishandled
3. Try alternate USB ports on the front panel
4. Try rear USB ports — directly connected to motherboard,
   more reliable than front panel ports
5. Check File Explorer — confirm drive is not appearing
6. Open Device Manager > Universal Serial Bus Controllers —
   look for Unknown Device or yellow warning triangle
7. Check device Properties for error code
8. Code 43 — attempt driver reinstall via uninstall then
   scan for hardware changes
9. If Code 43 persists after reinstall — hardware damage
   is the likely cause, advise data recovery specialist
10. Check Disk Management if drive detected but not visible
    in File Explorer — may need drive letter assigned

---

## 14. No Display Output — Existing System
1. Ask if system previously worked or is a new build
2. Check display cable at both ends — monitor and GPU
3. Confirm cable is in GPU port not motherboard port
4. Confirm monitor is on and set to correct input
5. Swap display cable if available
6. Open case — check motherboard for fault indicator lights
7. Red DRAM light — inspect RAM seating, look for gold contacts
8. Power off and unplug before touching internal components
9. Reseat RAM firmly until both clips click
10. Check for dust while case is open — clean preventatively
11. Power on and confirm POST completes and system boots
12. Recommend thermal paste replacement if system is 2+ years old

---

## 15. Random Wi-Fi Disconnections
1. Ask when issue started and what notification appears on disconnect
2. Confirm other devices stay connected — isolates laptop vs router
3. Ask about recent router changes or ISP upgrades
4. Check Device Manager > Network Adapters for yellow triangle
5. If Code 43 — uninstall driver, reboot to reinstall automatically
6. Check adapter Properties > Advanced tab
7. Set Transmit Power to Highest
8. Ask about Bluetooth peripherals in use
9. If Bluetooth device in use — check Bluetooth Collaboration setting
10. Set Bluetooth Collaboration to Wi-Fi First if on 2.4GHz network
11. Test with Bluetooth device active for 20+ minutes to confirm fix

---

## 16. Windows Update Stuck
1. Confirm whether stuck on download or installation phase
2. If installation — network is not the primary concern
3. Remove all non-essential USB devices
4. Toggle network connection
5. Ask what was running when update started — close all open apps
6. Run Windows Update Troubleshooter before force restarting —
   Settings > Update & Security > Troubleshoot > Windows Update
7. If still stuck — force restart via power button (safe to do)
8. Confirm rollback completes and system returns to desktop
9. Close all applications, check Task Manager for high resource usage
10. Set realistic time expectations based on HDD vs SSD storage
11. Re-run update with clean system state
12. If update fails repeatedly — clear SoftwareDistribution folder

---

## 17. Specific Sites Unreachable — VPN
1. Ask if affected sites require VPN access
2. Confirm VPN is connected — check for warning messages
3. If "Limited network access" — traffic not flowing through tunnel
4. Try VPN disconnect and reconnect first — fastest fix
5. Check VPN client version — look for available updates
6. Update client if behind current version
7. Reconnect VPN and test previously unreachable sites
8. If update doesn't resolve — run ipconfig /flushdns and /renew
9. Enable automatic updates in VPN settings to prevent recurrence

---

## 18. Outlook Password Loop
1. Ask if account is personal or Microsoft 365 work account
2. Confirm whether issue is app or web based
3. If web works but app doesn't — issue is app configuration
4. Check for Office updates via File > Office Account > Update Options
5. Navigate to Settings > Accounts > Email & Accounts
6. Remove the affected account
7. Re-add account — approve MFA prompt if it appears
8. Test Outlook — confirm no password prompt on open
9. Check File > Account Settings > Change — set offline sync to All
10. If password loop persists after re-add — check Windows
    Credential Manager for corrupted Microsoft Office entries
    and remove them before re-adding the account

---

## 19. Beeping on Power On — No POST
1. Count the beep pattern carefully — number and length matter
2. Check motherboard for fault indicator lights — more reliable
   than beep codes
3. Identify motherboard manufacturer — label inside case or
   model sticker on board itself
4. Cross reference beep code with manufacturer documentation
5. Ask about room temperature and environment — heat is a
   common overlooked factor
6. If CPU fault light — inspect heatsink for dust and check
   for CPU fan presence
7. Power off and unplug before touching internal components
8. Clean fans and heatsink with compressed air — hold fans still
9. Remove heatsink — inspect thermal paste condition
10. If dried or cracked — clean with isopropyl alcohol and
    apply fresh pea sized dot of thermal paste
11. Reseat heatsink securely
12. Perform final check of all components — especially RAM seating
13. Reassemble and power on — confirm no beeping and POST completes
14. If still no POST after thermal fix — allow system to cool
    30 minutes before retrying

---

## 20. Random Restarts Without BSOD
1. Ask when restarts started and what user was doing each time
2. Ask about recent Windows updates — check update history via
   Settings > Update & Security > Windows Update > View Update History
3. Check for dust and thermal issues — rule out overheating
4. Open Event Viewer > Windows Logs > System
5. Filter Critical — confirm Kernel-Power Event ID 41 present
6. Filter Critical and Error — look for events just before each 41
7. Event ID 7031 Windows Update service — indicates corrupted files
8. Open Command Prompt as Administrator
9. Run DISM first: DISM.exe /Online /Cleanup-Image /RestoreHealth
10. Then run: sfc /scannow
11. Restart to finalize repairs
12. Run sfc /scannow again — confirm no integrity violations
13. Monitor for 20 minutes with Event Viewer open
14. If update is confirmed problematic — check for uninstall option
    in Windows Update history

---

## 21. Screen Flickering
1. Ask when flickering started and whether a recent update installed
2. Check Settings > Display > Advanced Display Settings —
   confirm refresh rate and resolution are correct
3. Open Device Manager > Display Adapters
4. Look for yellow warning triangles on display adapter entries
5. Two adapter entries with warnings indicates driver conflict
6. Right click adapter > Properties > Driver tab > Roll Back Driver
7. If Roll Back Driver greyed out — Update Driver > Browse my
   computer > select previous version manually
8. Roll back the adapter with the warning triangle first
9. Restart before making additional changes
10. Confirm flickering stopped and warning triangles cleared
11. If flickering persists — download latest driver directly
    from manufacturer website using laptop make and model

---

## 22. No Internet — DNS Failure
1. Confirm other devices on same network work — isolates
   device vs DNS/network issue
2. Run ipconfig — confirm valid IP address assigned
3. Run nslookup google.com — DNS request timed out confirms
   DNS resolution failure
4. Run ipconfig /release > ipconfig /flushdns > ipconfig /renew
5. Run nslookup google.com again — if still failing DNS server
   is the problem not the lease
6. Bypass router DNS with public server:
   netsh interface ip set dns "Ethernet" static 8.8.8.8
   (replace Ethernet with Wi-Fi if on wireless)
7. Run ipconfig /flushdns then nslookup google.com
8. If nslookup succeeds — router/ISP DNS confirmed as failure
9. Configure dual public DNS for long term reliability:
   netsh interface ip set dns "Ethernet" static 1.1.1.1
   netsh interface ip add dns "Ethernet" 8.8.8.8 index=2
   ipconfig /flushdns
10. Test multiple websites to confirm resolution
11. If specific sites still fail with working DNS — check
    hosts file at C:\Windows\System32\drivers\etc\hosts
    for corrupted or tampered entries

---

## 23. Slow Boot Time
1. Ask about system history and recent changes
2. Check Task Manager > Performance — note storage type (HDD vs SSD)
3. Check Task Manager > Startup tab FIRST — most common cause
4. Identify high impact and excessive startup programs
5. Disable known non-essential programs systematically
6. Research unrecognized entries before disabling
7. Leave services that affect peripherals enabled unless certain
8. Restart to measure boot time improvement
9. For HDD systems — recommend SSD upgrade as primary long term fix
10. Note manual defrag provides minimal benefit on modern Windows
11. For stubborn cases — check msconfig services and Event Viewer
    Diagnostics-Performance log
12. Emphasize data backup before any hardware upgrade

---

## 24. Cannot Print — Stuck Queue / Spooler
1. Confirm whether others can print to same printer — isolates
   workstation vs printer/network issue
2. Check Settings > Devices > Printers & Scanners for printer status
3. Open print queue — look for stuck jobs
4. Cancel all jobs
5. If a job hangs on "Deleting..." — print spooler is hung
6. Restart Print Spooler: Win + R > services.msc > Print Spooler
   > right click > Restart
7. Recheck queue — confirm cleared and printer status Ready
8. Retry printing to confirm
9. If queue clears but still won't print — check Printer Properties
   > Ports tab for correct IP/TCP-IP port mapping
10. Use vendor-specific driver rather than generic Windows driver
11. Educate user not to spam print button — adds jobs and hangs spooler

---

*Last updated: May 2026*
*Add new sequences as new scenarios are documented.*
