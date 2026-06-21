# Scenario 04 — New hire needs account + access (provisioning)

**Category:** Provisioning  ·  **Severity:** Medium (time-sensitive)

## Problem (as reported)
"New employee starts Monday and needs an account, email, and access to the Sales share."

## Symptoms
- No existing account; needs to be productive day one.

## Investigation / process
1. Get the request through the proper channel (HR/manager approval) with role + required access.
2. Identify a comparable existing user to **mirror group memberships** from.

## Root cause
N/A — this is a build, not a break. The skill is doing it **consistently and by-group**.

## Fix / resolution
1. ADUC → create the user in the correct **OU**, set UPN, temp password + "must change at next logon."
2. Add to the **security groups** that grant the role's access (mirror the comparable user).
3. Confirm licensing/mailbox if hybrid (hand off to M365 side as needed).
4. **Validate**: first login works, required resources are reachable.
5. Document what was granted (for the eventual offboarding).

## Prevention notes
- Use **role-based group bundles** so provisioning is repeatable, not ad-hoc.
- A template/checklist (see `/checklists`) prevents "they're missing one share" follow-ups.
