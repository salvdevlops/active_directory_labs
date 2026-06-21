# Lab 03 — Trace a recurring lockout to its source

**Goal:** stop unlocking blindly; find *what* is locking the account.

## Tasks
1. Simulate a stale credential: map a drive or save a credential on the client with the user's **old** password, then reset the password on the DC.
2. Watch the account re-lock.
3. On the DC: **Event Viewer → Security → filter Event ID 4740** — read the **Caller Computer Name**.
4. Go to that source and clear the stale credential (Credential Manager / re-map / update).

## Validate
- You can name the exact source from the 4740 event.
- After clearing it, the account **stays** unlocked through a few minutes of idle time.
