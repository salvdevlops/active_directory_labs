# Scenario 06 — Account locks every few minutes (stale credential)

**Category:** Authentication  ·  **Severity:** High (recurring, disruptive)

## Problem (as reported)
"You unlocked me but it locked again ten minutes later. This keeps happening all day."

## Symptoms
- Account re-locks shortly after each unlock.
- The user isn't even actively trying to log in when it happens.

## Investigation steps
1. On the DC: **Event Viewer (Security) → Event 4740** — note the **Caller Computer Name** (the lockout source).
2. Cross-reference **4625** failed-logon events for the time/source.
3. Common sources: a **phone** with old Wi-Fi/Exchange creds, a **mapped drive** using old creds, a stuck **RDP session**, a saved credential in Credential Manager, or a scheduled task/service running as the user.

## Root cause
A device or app is repeatedly authenticating with an **old (post-reset) password**, tripping the lockout policy on a loop.

## Fix / resolution
- Identify the source from Event 4740, then clear the stale credential there:
  - Update the password on the phone / Wi-Fi profile.
  - Remove old entries in **Credential Manager**.
  - Re-map drives / kill the stale RDP session / update the service account.
- Unlock once more and confirm it **stays** unlocked.

## Prevention notes
- After every reset, prompt users to update saved creds on **all** devices (phone especially).
- Lockout-source tooling (or auditing 4740 centrally) turns a day-long ghost hunt into minutes.
