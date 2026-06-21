# Scenario 05 — User can't access a department resource (group)

**Category:** Access / authorization  ·  **Severity:** Medium

## Problem (as reported)
"Everyone on my team can open the Finance folder except me."

## Symptoms
- User denied on a resource peers can access.
- No lockout; authentication is fine — this is *authorization*.

## Investigation steps
1. Confirm it's authorization, not authentication (they log in fine).
2. Compare the user's **group memberships** to a working teammate's (ADUC → Member Of).
3. Identify which **security group** the resource's permissions are tied to.

## Root cause
The user isn't a member of the security group that grants access to the resource — almost always the cause when peers can get in and they can't.

## Fix / resolution
- Route an **access request** for the correct group (approval as required).
- Add the user to the group.
- Have them **log off/on** (new token) — the new membership won't apply mid-session.
- **Validate** they can now open the resource.

## Prevention notes
- Access via **groups**, never per-user ACLs.
- Keep a map of "resource → group" so this is a fast, auditable fix.
