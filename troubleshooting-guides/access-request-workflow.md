# Guide: Access request workflow

1. **Confirm it's authorization, not authentication** (user logs in fine, denied on a resource).
2. **Find the controlling group** for the resource.
3. **Compare** to a working peer's `Member Of`.
4. **Route the request** for approval per policy (don't grant access off a verbal ask).
5. **Add to the group** — never set per-user ACLs.
6. **New session** required for the token to refresh (log off/on).
7. **Validate + document** what was granted.

> Group-based access is auditable; per-user permissions are how environments rot.
