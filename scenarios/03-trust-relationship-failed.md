# Scenario 03 — "Trust relationship between this workstation and the domain failed"

**Category:** Machine account  ·  **Severity:** High (user can't log in to that PC)

## Problem (as reported)
"I get 'The trust relationship between this workstation and the primary domain failed.'"

## Symptoms
- Domain login fails on a specific machine with that exact message.
- Often follows the PC being off for a long time, or being restored from an image/snapshot.

## Investigation steps
1. Confirm it's machine-specific (the user logs in fine elsewhere).
2. Check the **computer object** still exists in ADUC.
3. Understand the cause: the machine-account password rotated on the domain but the local machine's copy is stale.

## Root cause
The computer's secure-channel (machine account) password is out of sync with the domain — so the DC rejects the machine's trust.

## Fix / resolution
- Preferred (no rejoin): `Reset-ComputerMachinePassword` or `Test-ComputerSecureChannel -Repair` from an elevated PowerShell, using domain-admin creds.
- Or remove from domain → reboot → rejoin (heavier; recreates the computer object).
- **Validate** a clean domain login afterward.

## Prevention notes
- Avoid reverting domain-joined machines to old snapshots.
- Don't leave machines powered off past the machine-account password age for long stretches.
