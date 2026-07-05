# Cannot Attach Large PDF to Email — Outlook Attachment Size Limit

**Date:** May 2026
**Environment:** Windows 10, Outlook 365 desktop, corporate
Exchange environment, 30 MB PDF attachment, time-sensitive
client deliverable

---

## Problem
A user was unable to attach a 30 MB PDF to an Outlook email
for a client deliverable due later that day. Outlook rejected
the file as too large. The user was unaware of email attachment
size limits and needed a fast professional workaround.

---

## Symptoms
- 30 MB PDF rejected by Outlook as too large to attach
- Time-sensitive client deliverable creating urgency
- No other symptoms — Outlook otherwise functioning normally

---

## Diagnostic Steps
1. Identified the issue as a standard email attachment size
   limit rather than a system fault — no diagnosis required,
   the error message was the expected behavior
2. Recognized two viable solutions — compress the file or
   send via OneDrive link. Chose OneDrive link as the primary
   recommendation for professional appearance and preservation
   of file quality
3. Instructed user to click Attach File in Outlook and select
   the PDF via Browse This PC — Outlook 365 automatically
   detected the oversized file and offered to upload to
   OneDrive and share a link
4. User accepted the prompt — file uploaded and link inserted
   into the email body automatically
5. Advised user to add a short line in the email indicating
   the file can be sent directly if the link has any issues —
   provides a professional backup without bloating the email
   with a redundant compressed attachment

---

## Root Cause
Standard email attachment size limits. The default Outlook
attachment limit is approximately 20 MB. Corporate Exchange
servers can raise this cap but recipient mail servers may
still reject oversized attachments, making cloud sharing
the reliable choice for files above the limit regardless
of internal server configuration.

---

## Resolution
Uploading the PDF to OneDrive via Outlook's integrated
one-click sharing and inserting the link into the email
body allowed the file to be delivered to the client without
attachment size restrictions. Adding a brief note in the
email offering direct file delivery on request provided a
professional fallback path.

---

## Additional Recommendations
- Files above approximately 20 MB should be sent via OneDrive
  link rather than attached directly — this is corporate
  email standard practice regardless of internal server limits
- Outlook 365 integrated OneDrive attachment prompt is the
  fastest method — click Attach File and select via Browse
  This PC to trigger the prompt reliably
- Manual OneDrive upload via File Explorer is the fallback
  when the Outlook prompt does not appear — save a copy to
  OneDrive, then generate a share link from OneDrive itself
- Requesting IT to raise the mail server attachment limit is
  generally not approved — IT prefers to standardize on
  OneDrive sharing rather than increase server load
- For users who send large files frequently to specific
  clients IT can help configure dedicated SharePoint folders
  or streamlined workflows

---

## Lessons Learned
Standard attachment size limits are not system faults —
recognize the pattern immediately and pivot to the workaround
rather than treating it as a diagnostic problem. OneDrive
link sharing is the standard professional workaround and
preserves file quality — compression can degrade PDFs
especially with images or formatted content. Trust real
world experience — deliver the simplest correct solution
confidently rather than layering multiple redundant
contingencies. Outlook 365 native cloud attachment
integration handles the OneDrive upload and link insertion
in one step when triggered via Attach File > Browse This PC.
