# Troubleshooting Write-Ups

Real IT scenarios I have encountered, diagnosed, and resolved — documented 
in a structured format.

Each write-up follows the same structure: environment, symptoms, diagnostic 
steps, root cause, and resolution.

---

## Reference Guides

| File | What it is |
|------|------------|
| [quick-reference-sequences.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/quick-reference-sequences.md) | Quick diagnostic sequences for common IT scenarios |

---

## Help Desk Scenarios

| File | Scenario |
|------|----------|
| [no-os-found-new-pc-build.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-os-found-new-pc-build.md) | New PC build — no operating system found on first boot |
| [high-memory-chrome-slowdown.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/high-memory-chrome-slowdown.md) | Family member's PC running slow — Chrome pushing RAM to 99% |
| [no-display-gpu-power-not-connected.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-display-gpu-power-not-connected.md) | New PC build — no display output due to GPU not connected to PSU |
| [no-wifi-adapter-card-not-seated.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-wifi-adapter-card-not-seated.md) | Desktop PC — no Wi-Fi option after cleaning, Wi-Fi card not fully seated |
| [random-freezes-dust-buildup-overheating.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/random-freezes-dust-buildup-overheating.md) | Windows 10 desktop — random freezes caused by dust buildup and CPU overheating |
| [outlook-not-sending-receiving-work-offline.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/outlook-not-sending-receiving-work-offline.md) | Windows 10 laptop — Outlook not sending or receiving, Work Offline mode accidentally enabled |
| [malware-browser-hijack-pdf-converter.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/malware-browser-hijack-pdf-converter.md) | Windows 10 laptop — malware and browser hijacking from malicious PDF converter download |
| [bitlocker-recovery-key-after-update.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/bitlocker-recovery-key-after-update.md) | Windows 10 laptop — BitLocker recovery key prompted after overnight IT update |
| [clicking-hdd-failing-drive-diagnosis.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/clicking-hdd-failing-drive-diagnosis.md) | Windows 10 desktop — progressive slowdown and clicking noise diagnosed as failing HDD |
| [no-internet-static-ip-blocking-dhcp.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-internet-static-ip-blocking-dhcp.md) | Windows 10 desktop — no internet access on single workstation, static IP preventing DHCP lease |
| [bsod-kernel-power-failing-hard-drive.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/bsod-kernel-power-failing-hard-drive.md) | Windows 10 desktop — repeated blue screens caused by failing HDD identified via Event Viewer |
| [usb-drive-not-recognized-code-43-physical-damage.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/usb-drive-not-recognized-code-43-physical-damage.md) | Windows 10 desktop — USB drive not recognized, Code 43 error caused by physical damage from drop |
| [account-locked-out-password-expired.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/account-locked-out-password-expired.md) | Windows 10 corporate desktop — account locked out after password expired during vacation |
| [network-printer-down-paper-jam.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/network-printer-down-paper-jam.md) | Office network printer not responding for multiple users — paper jam cleared |
| [no-display-post-failure-unseated-ram.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-display-post-failure-unseated-ram.md) | Windows 10 desktop — no display on boot, POST failure caused by unseated RAM stick |
| [wifi-drops-bluetooth-interference-router-upgrade.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/wifi-drops-bluetooth-interference-router-upgrade.md) | Windows 10 laptop — random Wi-Fi drops caused by Bluetooth interference after router upgrade |
| [windows-update-stuck-open-applications.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/windows-update-stuck-open-applications.md) | Windows 10 desktop — update stuck at 35%, caused by open applications during installation |
| [sites-unreachable-outdated-vpn-client.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/sites-unreachable-outdated-vpn-client.md) | Windows 10 desktop — specific sites unreachable, outdated VPN client causing limited network access |
| [outlook-password-loop-new-laptop-misconfigured.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/outlook-password-loop-new-laptop-misconfigured.md) | Windows 10 laptop — Outlook repeatedly prompting for password on newly provisioned device |
| [no-post-cpu-overheat-degraded-thermal-paste.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-post-cpu-overheat-degraded-thermal-paste.md) | Desktop PC — no POST, CPU overheating from dust buildup and degraded thermal paste, unseated RAM |
| [random-restarts-corrupted-windows-update.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/random-restarts-corrupted-windows-update.md) | Windows 10 desktop — random restarts without BSOD caused by corrupted Windows update files |
| [screen-flickering-display-driver-update-conflict.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/screen-flickering-display-driver-update-conflict.md) | Windows 10 laptop — screen flickering caused by incompatible display driver pushed by Windows update |
| [no-internet-isp-dns-failure-public-dns-fix.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/no-internet-isp-dns-failure-public-dns-fix.md) | Windows 10 desktop — no internet access caused by ISP DNS server failure, resolved with public DNS configuration |
| [slow-boot-excessive-startup-programs-hdd.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/slow-boot-excessive-startup-programs-hdd.md) | Windows 10 desktop — extremely slow boot caused by excessive startup programs on aging HDD |
| [cannot-print-stuck-queue-hung-spooler.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/cannot-print-stuck-queue-hung-spooler.md) | Windows 10 desktop — cannot print, stuck print queue and hung print spooler service |
| [cannot-connect-wifi-driver-update-rollback.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/help-desk-scenarios/cannot-connect-wifi-driver-update-rollback.md) | Windows 10 work laptop — cannot connect to office Wi-Fi after IT-pushed driver update |
---

## Network Technician Scenarios

| File | Scenario |
|------|----------|
| [switch-uplink-down-bad-rj45-termination.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/network-tech-scenarios/switch-uplink-down-bad-rj45-termination.md) | Switch uplink failure — incorrectly terminated RJ45 causing full segment outage |
| [domain-not-joined-after-reimage.md](https://github.com/W-Monteus/troubleshooting-writeups/blob/main/network-tech-scenarios/domain-not-joined-after-reimage.md) | Windows 10 workstation — user cannot access shared drives after reimage, machine not rejoined to AD domain |
