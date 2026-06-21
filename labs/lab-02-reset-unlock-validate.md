# Lab 02 — Reset password, unlock, force change, validate

**Goal:** the #1 help desk ticket, done cleanly with verification habits.

## Tasks
1. Lock the test account (fail the password a few times on the client).
2. In ADUC, confirm **Account is locked out** is checked.
3. **Unlock** + **Reset Password**, set **"must change at next logon."**
4. (PowerShell alternative) `Unlock-ADAccount -Identity user` and `Set-ADAccountPassword`.
5. Log in as the user on the client.

## Validate
- Login forces a password change, then succeeds.
- You can state, out loud, the identity-verification step you'd do *before* any of this on a real call.
