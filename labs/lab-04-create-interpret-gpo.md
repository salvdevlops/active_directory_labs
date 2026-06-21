# Lab 04 — Create and interpret a GPO

**Goal:** be able to read Group Policy (and create a simple one) — the firm-up area.

## Tasks
1. **GPMC** → create a GPO (e.g., set a desktop wallpaper or a simple security setting), link it to the `Sales` OU.
2. On the client: `gpupdate /force`, then log in as a user in that OU.
3. Confirm the setting applied.
4. Run `gpresult /h gpo-report.html` and read which GPOs hit the user and why.
5. Practice **GPMC → Group Policy Results** against the client.

## Validate
- The setting visibly applies to OU users (and not to users outside it).
- You can explain **LSDOU** precedence and read a `gpresult` report.

## Screenshot targets
`/screenshots/lab04-gpmc-link.png`, `/screenshots/lab04-gpresult.png`
