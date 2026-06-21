# active-directory-helpdesk-lab

A hands-on Active Directory lab simulating the identity/account tickets a help desk handles daily — password resets, lockouts, group access, provisioning, and reading Group Policy — built and worked in my own Windows Server domain.

> **Honesty note:** lab portfolio, not claimed production experience. Built on a self-hosted domain (`SOLTICK`) so I can perform and explain these tasks, not just recite them.

---

## Overview

Simulates **tier-1/tier-2 Active Directory support** on a Windows Server domain: managing users/computers/OUs/groups, resolving lockouts, handling access requests through groups, running account-recovery workflows, and interpreting Group Policy.

## Real-world use case

The single most common help desk ticket is *"I'm locked out / I forgot my password."* Right behind it: *"I can't get into [resource]"* (an access/group problem). This lab is reps for both — done correctly, securely, and documented like a real ticket.

## Tools and systems involved

- Windows Server 2022 — domain `SOLTICK` (VMware Workstation)
- Windows 10/11 domain-joined client
- **Active Directory Users and Computers (ADUC)**
- **Group Policy Management Console (GPMC)**
- RSAT tools; PowerShell (`Get-ADUser`, `Unlock-ADAccount`, etc.)
- Event Viewer (Security log) for lockout source tracing

## Common scenarios covered

See [`/scenarios`](scenarios): account lockouts, forgotten passwords, broken machine trust relationships, new-hire provisioning, group-based access failures, and recurring lockouts from stale cached credentials.

## Step-by-step troubleshooting flow

1. **Verify identity** per policy before any reset (security first — this is how social-engineering attacks get in).
2. **Confirm the symptom** — locked vs. disabled vs. expired vs. wrong-resource.
3. **Check the object** in ADUC: account status, group membership, expiry, last logon.
4. **For lockouts**, find the *source* (Event 4740 / lockout tools) — don't just unlock and walk away.
5. **Apply the correct fix** (unlock, reset + force change, fix group membership).
6. **Validate** the user can actually log in / reach the resource.
7. **Document** and, for access changes, route through the proper approval.

## Resolution methods used here

Password reset with "change at next logon," account unlock, security-group membership changes via access request, machine-account/trust repair, account-recovery procedure, GPO interpretation with `gpresult`/GPMC.

## Root cause patterns I learned to recognize

- **Repeated lockouts** = a stale credential somewhere (phone, mapped drive, old session), not the user fat-fingering it.
- **"Trust relationship failed"** = the computer's machine-account password is out of sync with the domain.
- **"I can't access X"** = group membership, 95% of the time — not a permission set on the user.
- A reset without **identity verification** is a security incident waiting to happen.

## What I learned

Identity work is where help desk most directly touches security. Doing it *correctly* (verify first, fix the root cause, grant via groups, document) is what separates a button-pusher from someone you'd promote.

## Repo structure

```
active-directory-helpdesk-lab/
├── scenarios/              ticket-style identity issues, fully worked
├── troubleshooting-guides/ lockouts, access requests, GPO basics
├── labs/                   hands-on tasks in the SOLTICK domain
├── checklists/             provisioning / offboarding / verification
├── docs/                   AD objects + Group Policy explained
└── screenshots/            evidence from my own lab
```
