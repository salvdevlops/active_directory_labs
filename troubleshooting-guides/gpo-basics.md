# Guide: Group Policy basics (for help desk)

**What it is:** Group Policy pushes configuration (security settings, drive maps, restrictions, etc.) to users/computers based on where their object lives in AD.

**Where it applies (precedence — last wins):** **L**ocal → **S**ite → **D**omain → **O**U  ("LSDOU"). A lower OU's GPO overrides a higher one unless "Enforced" / "Block Inheritance" change that.

## How to interpret what's hitting a machine/user
- `gpresult /r` (summary) or `gpresult /h report.html` (full report) on the client.
- **GPMC → Group Policy Results** wizard for a remote target.
- `gpupdate /force` to reapply immediately.

## What help desk actually does with GPO
- *Read* it to explain why a setting/restriction is in place ("why can't I change my wallpaper?").
- Confirm a policy is **applying** (or being blocked / filtered out by security filtering).
- Escalate *changes* to the team that owns the GPO — but be able to read the results.
