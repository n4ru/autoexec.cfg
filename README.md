# autoexec.cfg

A Counter-Strike 2 autoexec — *"mostly just things I think should be in the game anyway."*

Quality-of-life binds plus a handful of aim helpers, built entirely from in-game console
aliases (no external software or macros). Highlights: hold-to-peek knife quickswitch,
weapon-aware right-click, dynamic crosshairs, a mouse-motion-driven smooth crosshair color
sweep, one-key buy-and-equip for utility, and a reload/inspect combo.

## Install

1. Drop `autoexec.cfg` into your CS2 cfg folder:
   `…\Steam\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg\`
2. Load it from the console: `exec autoexec`
3. (Optional) To run it every launch, add `+exec autoexec` to CS2's launch options
   (Steam → CS2 → Properties → Launch Options).

> CS2 only — the scripting relies on CS2's console aliases and `bind mouse_x / mouse_y`.

## Crosshair

Share code: `CSGO-W8rpQ-SA3BC-9SpCA-HizOk-DeCcO`

The crosshair changes dynamically between firing and idle states (see below). The config
sets a negative gap for an 8K ultrawide; drop it to `-1.5` at 1080p:

| Resolution        | Setting                  |
| ----------------- | ------------------------ |
| 1080p             | `cl_crosshairgap -1.5`   |
| 8K / 2K ultrawide | `cl_crosshairgap -4.0`   |

## Binds at a glance

### Mouse

| Input               | Action                                                                                   |
| ------------------- | ---------------------------------------------------------------------------------------- |
| **Left click**      | Fire. Cycles spectator target when dead.                                                 |
| **Right click**     | Weapon-aware: rifle = scope/silencer, knife = heavy stab.                                |
| **Mouse 5** (hold)  | Quick-peek **knife**; snaps back to your **primary** on release.                          |
| **Mouse 4** (hold)  | Quick-peek **knife**; snaps back to your **pistol** on release.                           |
| **Wheel up**        | Grenade slot.                                                                             |

### Keyboard

| Key             | Action                                                       |
| --------------- | ----------------------------------------------------------- |
| **1**           | Buy AK-47 / M4A1-S (side-aware) and equip primary.          |
| **2**           | Buy armor + helmet and equip pistol.                        |
| **3**           | Buy defuser and pull knife.                                 |
| **4 / 5**       | Grenade slots.                                              |
| **E**           | Use.                                                        |
| **R**           | **Reload + inspect** with a wider viewmodel FOV.            |
| **T**           | Switch hands.                                               |
| **B**           | Sell back everything (freeze time).                         |
| **G**           | Drop current weapon, re-equip primary.                      |
| **Z**           | Buy HE grenade + equip.                                     |
| **X**           | Buy flashbang + equip.                                      |
| **C**           | Buy smoke + equip.                                          |
| **V**           | Buy molotov / incendiary + equip.                           |
| **Space**       | Jump.                                                       |

## Features

### Knife quickswitch (hold-to-peek)
Hold **Mouse 5** or **Mouse 4** to instantly pull your knife — faster movement, defuse/plant
fake-outs, animation cancels — and snap straight back the moment you let go. **Mouse 5**
returns to your **primary**, **Mouse 4** to your **pistol**. (Pressing **3** also pulls the
knife and buys a defuser, but stays on the knife.)

### Weapon-aware right-click
Right-click maps to your weapon's secondary (`+attack2`), so it does the sensible thing for
whatever you're holding:

- **Rifle** → scope / silencer toggle
- **Knife** → heavy stab

### Rifle "super follow recoil" crosshair
While spraying a rifle, the crosshair follows the recoil (`cl_crosshair_recoil`) and rapidly
swaps between a tight firing crosshair and a spread one as the gun climbs — a strong visual
recoil reference.

> The rifle behavior engages once the config knows a rifle is out (after you select it with
> **1** or a quickswitch). See **Notes** below.

### Dynamic crosshairs
Two crosshair states, swapped automatically:

- **Firing** — no size, dot on, T-style, tight and out of the way.
- **Idle** — small, dotless, dynamic split so you can read spread.

### Smooth 317-step color sweep
The crosshair colour is a continuous gradient rather than a handful of preset colours: a
317-step loop through **green → red → yellow → magenta → cyan → violet → sky → green**,
advanced by mouse motion (`bind mouse_x / mouse_y`), so the colour flows as you move.

The sweep runs at two speeds:

- **Moving** — one step per motion tick, a slow drift.
- **Firing** — five steps per tick, so holding down the trigger visibly rips through the
  spectrum while you spray.

### Buy + equip utility (one key each)
**Z / X / C / V** buy a grenade *and* switch to it in a single press (HE / flash / smoke /
molotov-incendiary). **1** buys your rifle, **2** buys armor, **3** buys a defuser — each also
equips the right slot.

### Reload + inspect
**R** reloads and plays the inspect animation with a roomier viewmodel FOV, snapping back to
your gameplay FOV on release.

### Spectator cycling
While dead, left-click cycles to the next player you're spectating.

## Notes & gotchas

- **Sync your weapon at round start.** The config infers your current weapon from the
  weapon-select inputs you press — it can't detect what you spawn holding. Tap **1**
  (or a quickswitch) once each round so right-click and the rifle follow-recoil match your
  actual gun. Most players hit a buy/select key in freeze time anyway.
- **This config sets your sensitivity** (`sensitivity 1.3`, `m_yaw 0.022`).
- **`Q` and mouse wheel down are explicitly unbound** — they're free for you to use.
- **The colour sweep is motion-driven** via `bind mouse_x / mouse_y` — moving the mouse is
  what advances it (and what drives the rifle follow-recoil swap). That's intended, not a bug.
- Pure vanilla console scripting — **no external macros or third-party software.**

## Credits

Config by **n4ru** (in-game: *thebigsneed*).
