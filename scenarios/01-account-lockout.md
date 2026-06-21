# Scenario 01 — User cannot log into domain account (locked out)

**Category:** Authentication  ·  **Severity:** High (user down)

## Problem (as reported)
"I keep getting 'your account has been locked out' when I try to sign in."

## Symptoms
- Login rejected with a lockout message even when the user is sure of the password.
- Started after several failed attempts (or with no obvious trigger).

## Investigation steps
1. **Verify the caller's identity** per policy before touching anything.
2. ADUC → user → **Account** tab: confirm **"Account is locked out"** is checked (vs. disabled/expired).
3. Check **Event Viewer (Security) → Event 4740** on the DC for *which* source workstation triggered the lockout.
4. Confirm the account isn't *disabled* or *expired* (different fixes).

## Root cause
Account lockout policy tripped by repeated bad passwords — either the user mistyped, or (very often) a device/app was retrying a stale cached password in the background.

## Fix / resolution
- **Unlock** the account (ADUC → Account → uncheck lockout, or `Unlock-ADAccount`).
- If the password was forgotten, **reset** it and set **"User must change password at next logon."**
- If a source device caused it, clear the stale credential there so it doesn't re-lock (see Scenario 06).
- **Validate** the user logs in successfully.

## Prevention notes
- Teach users to update saved passwords on **all** devices after a reset.
- Self-service password reset (SSPR) cuts these tickets dramatically.
