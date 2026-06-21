# Reference: Group Policy explained (plain English)

**Purpose:** centrally enforce settings on users and computers without touching each machine.

**Processing order (precedence, last wins):** Local → Site → Domain → OU = **LSDOU**. Closer-to-the-object (OU) overrides broader (Domain), unless **Enforced** or **Block Inheritance** changes it.

**Two halves of every GPO:** *Computer Configuration* (applies at boot, to the machine) and *User Configuration* (applies at login, to the user).

**Refresh:** automatically every ~90 min (+random offset); force with `gpupdate /force`.

**Reading results:**
- `gpresult /r` — quick summary of applied GPOs.
- `gpresult /h report.html` — full, readable report.
- **GPMC → Group Policy Results** — remote target, GUI.

**Why a GPO might *not* apply:** wrong link/OU, **security filtering** excludes the user, WMI filter, Block Inheritance, or it's the other half (user vs computer) than expected.

**Help desk role:** read and explain policy, confirm it's applying, trace why it isn't — and escalate *changes* to the GPO owner.
