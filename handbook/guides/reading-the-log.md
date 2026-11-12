# Reading hideway.log

`hideway.log` sits next to `Hideway.exe` (inside `core\`). It is plain text, **never contains keys or tokens**, and is the first thing support asks for.

* When it grows past a size limit it becomes `hideway.log.1` and a new `hideway.log` starts. **Keep both** when you send logs.
* **Debug > LIVE LOG** shows the last events; **Copy log** copies everything.

## Line types

```
[2026-11-04 18:15:08] WORLD: UWorld lost (loading screen / match transition) - searching again
[2026-11-04 18:15:08] CAMERA: camera no longer valid (loading screen / lobby)
[2026-11-04 18:15:08] MATCH: MATCH ended after 669 s, 78438 ticks ...
[2026-11-04 18:15:10] GAME: Fortnite process ended - waiting for it to start again
```

| Prefix | Meaning |
|---|---|
| `start vX.Y.Z dma` | Hideway started (or `demo`) |
| `launcher ...` | The launcher started, signed in, checked modules, started the game module |
| `GAME:` | The Fortnite process was found or ended on the game PC |
| `WORLD:` | The game world was found or lost (loading screens and match transitions) |
| `CAMERA:` | The camera became valid or invalid |
| `PLAYERS:` | No other players readable (lobby, bus, match ended) |
| `OFFSET:` | An offset was discovered at runtime |
| `DEVICE:` | Input device connecting / connected / lost |
| `LOOT:` / `REBOOT:` | Loot and reboot card readers |
| `VISCHECK:` | The visibility check (Raycast VisCheck): whether the level geometry was read |
| `HEALTH:` | A probe of what each health source holds when none is readable |
| `MATCH:` | One summary line when a match ends |
| `FATAL` | A crash inside Hideway, with the module, address and call chain |

## The 10-second line

```
DMA: 10 s: 1188 ticks, avg 5 ms, max 14 ms, 12 player(s), 7 skeleton(s) | bones read 4, carried 0, skipped 0 far / 1 off-screen, fresh 25 | rounds 1.0 + 0.4 ms, governor x1.00 | health: 2 direct (2 mates, 0 enemies), 0 held, recovered 0 (pawn 0, base 0, player state 0), 10 unknown (0 mates, 10 enemies) | vis: layout ok, submit-time V3 O0 OOV8 ?1, render-time visible 2, agree 2 of 3
```

| Part | Meaning |
|---|---|
| `1188 ticks, avg 5 ms, max 14 ms` | Player reads in 10 s and how long each took. High averages point at the DMA link |
| `12 player(s), 7 skeleton(s)` | Players read, and how many had a skeleton this tick |
| `bones read / carried / skipped` | The load governor's work: skeletons read, reused, skipped far or off-screen |
| `governor xN` | 1.00 = full rate; up to 4 = heavily thinned because the link is the bottleneck |
| `health: N direct (M mates, K enemies)` | Players whose health was read directly, split by team. `unknown` = nothing readable |
| `vis: layout ok` | The level geometry was read and rays can be traced. It can read `not ready` for a few seconds at the start of a match |

## The match summary

```
MATCH: MATCH ended after 669 s, 78438 ticks (avg 4.8 ms); 36 players at most, per tick 12.0 humans + 0.0 bots; skeleton on 37 % of players | health read directly: teammates 76 %, enemies 1 % (recovered 0) | submit-time vs render-time agree in 92 % of 189804 comparisons, timestamps looked like times in 100 % of ticks
```

One line per match: how long, how many players, how much skeleton and health data was available, and how the visibility sources compared.

## A one-screen verdict

`tools\health_check.ps1` (in the full package) reads a log and prints a verdict per feature: loot OK, names OK, wall check, health (mates vs enemies), visibility, offsets found.

## What the log does **not** show

* Why **Fortnite** closed. Hideway only sees the process end (`GAME: Fortnite process ended`). The game's own crash report is on the **game PC**: `%LOCALAPPDATA%\FortniteGame\Saved\Crashes`. See [The game closes or crashes](../troubleshooting/game-closes-or-crashes.md).
