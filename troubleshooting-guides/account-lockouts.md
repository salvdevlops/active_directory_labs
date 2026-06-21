# Guide: Account lockouts

**Golden rule:** don't just unlock — find the *source*, or it comes back.

1. **Verify identity** of the caller (always, first).
2. Confirm status in ADUC: locked vs disabled vs expired vs wrong-password.
3. **Unlock** (`Unlock-ADAccount` or ADUC).
4. **Find the source:** DC Security log → **Event 4740** → Caller Computer Name. Correlate **4625** failures.
5. **Clear stale creds** at the source (phone, Credential Manager, mapped drives, RDP, service accounts).
6. Reset password + "change at next logon" if forgotten.
7. **Validate** it stays unlocked.

Key events: **4740** (locked), **4625** (failed logon), **4624** (success), **4767** (unlocked).
