# No Wireless Network Adapter Found — Wi-Fi Card Not Fully Seated

**Date:** April 2026
**Environment:** Custom-built or pre-built desktop PC, Windows OS,
dedicated Wi-Fi card (PCIe), wired ethernet available via motherboard

---

## Problem
A user reported their PC had no option to connect to Wi-Fi. The wireless
network adapter was completely absent from Windows — no Wi-Fi toggle, no
available networks, no adapter listed in settings. The issue began after
the user had moved and cleaned their PC.

---

## Symptoms
- No Wi-Fi option visible in Windows network settings
- No wireless adapter appearing in Device Manager
- Wired ethernet via motherboard LAN port worked normally
- Issue started immediately after PC was moved and cleaned

---

## Diagnostic Steps
1. Confirmed there was no wireless adapter visible in Windows network
   settings — no Wi-Fi toggle present
2. Checked Device Manager — no wireless adapter listed, confirming
   Windows could not detect the card at all
3. Connected PC to router via ethernet cable — wired connection worked
   immediately, confirming internet service and motherboard LAN port
   were both functional
4. Asked the user when the problem started — confirmed it began after
   they disconnected all cables, moved the PC to a new location to clean
   it, and reconnected everything
5. Opened the case to visually inspect internal components
6. Identified the Wi-Fi card was not fully seated in its PCIe slot —
   it had likely been knocked loose or not fully reseated after the move
7. Firmly reseated the Wi-Fi card into the PCIe slot until it clicked
   and secured the retention bracket
8. Powered the system back on — wireless adapter appeared in Windows
   immediately and Wi-Fi networks were detected normally

---

## Root Cause
The Wi-Fi card was dislodged from its PCIe slot during the cleaning
process when the user disconnected and reconnected components. A card
that is not fully seated cannot communicate with the motherboard,
causing Windows to have no awareness of the adapter entirely. Because
the motherboard's built-in LAN port was unaffected, wired connectivity
remained functional while wireless was completely absent.

---

## Resolution
Reseating the Wi-Fi card fully into the PCIe slot restored the wireless
adapter immediately. No driver reinstallation or software changes were
required.

---

## Lessons Learned
When a previously working component suddenly stops being detected after
a PC has been moved or cleaned, always open the case and check whether
expansion cards are fully seated before assuming hardware failure or a
driver issue. Cleaning and moving a PC introduces vibration and handling
that can unseat cards even without direct contact. A component that is
partially seated may still appear physically installed but will be
completely invisible to the operating system.
