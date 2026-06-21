# Lab 01 — Create OU, user, and security group; grant access

**Goal:** the core provisioning loop, done the right (group-based) way.

## Tasks
1. ADUC → create an **OU** (e.g., `Sales`).
2. Create a **user** in it (UPN, temp password, "must change at next logon").
3. Create a **security group** `Sales-Share-RW`.
4. Create a folder, share it, set **NTFS Modify** for `Sales-Share-RW` only.
5. Add the user to the group.

## Validate
- New user logs in, is forced to change password, and can write to the share.
- A user *not* in the group is denied. Prove it with **Effective Access**.

## Screenshot targets
`/screenshots/lab01-ou-tree.png`, `/screenshots/lab01-member-of.png`
