# Scenario 02 — Forgot password / reset workflow

**Category:** Authentication  ·  **Severity:** Medium–High

## Problem (as reported)
"I forgot my password and can't get in."

## Symptoms
- User can't authenticate; not locked, just doesn't know the password.

## Investigation / process (this one is about doing it *correctly*)
1. **Identity verification first** — name + employee ID + a second factor your org requires. Never skip this; password resets are a top social-engineering vector.
2. Confirm account status in ADUC (enabled, not expired).

## Root cause
Forgotten credential — routine, but the **process** is the point.

## Fix / resolution
1. ADUC → user → **Reset Password**.
2. Set a strong temporary password and check **"User must change password at next logon."**
3. (If also locked) uncheck **Account is locked out**.
4. Deliver the temp password over an approved channel (not plaintext email if avoidable).
5. **Validate**: user logs in, is forced to set a new password, succeeds.

## Prevention notes
- Push **Self-Service Password Reset** so users handle routine resets themselves.
- Document the verification you performed in the ticket (audit trail).
