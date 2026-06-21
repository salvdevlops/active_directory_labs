# Reference: AD objects explained

| Object | What it is | Help desk relevance |
|--------|-----------|---------------------|
| **User** | An identity (person) | resets, lockouts, group membership |
| **Computer** | A domain-joined machine account | trust-relationship issues |
| **OU (Organizational Unit)** | A container for organizing objects | where you create users; **GPOs link here** |
| **Security group** | Grants permissions/access | the right way to give access |
| **Distribution group** | Email list only (no permissions) | used by Exchange, not for access |

## Group scope (quick version)
- **Domain Local** — assign permissions to resources.
- **Global** — group users by role/department.
- **Universal** — span domains in a forest.

**AGDLP** best practice: **A**ccounts → **G**lobal groups → **D**omain **L**ocal groups → **P**ermissions. (Put users in role groups, put role groups into resource groups, assign permissions to the resource group.)

> OU ≠ group. An OU organizes objects and receives GPOs; a group grants access. Mixing these up is a classic beginner mistake.
