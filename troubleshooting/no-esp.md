# No ESP

Check these **in this order**. Open the Debug page (Misc > Debug > Show debug page) and read **READY CHECK**, **OFFSET HEALTH** and **DATA HEALTH**.

## 1. Is the game running and are you in a match?

The lobby has nobody to draw. In OFFSET HEALTH, **Other players** says `none in view (lobby, bus, or PlayerArray offset?)` until a match starts. Boxes appear once a match has begun; during the bus phase players may be few.

## 2. World not found

OFFSET HEALTH: **World** red with `GEngine / World / Level offsets are probably outdated`. The game was patched. → [After a Fortnite update](../guides/after-a-fortnite-update.md).

## 3. Camera not valid

Same cause, or you are in a loading screen. The log shows `CAMERA: camera no longer valid (loading screen / lobby)` at match transitions, which is normal.

## 4. Players = 0 in a match

The player offsets are stale, or the server is empty. **DATA HEALTH > Names** says how many of the players read have names.

## 5. Boxes are drawn but offset from the players

* Adjust **ESP time offset** (Misc) a few milliseconds.
* Make sure the game runs **borderless or full-screen** on the **same monitor** you capture.
* Check **Overlay monitor** (Misc).

## 6. The ESP master switch or a filter

* **Visuals > ESP > Enable ESP** must be on.
* **Show bots** and **Show teammates** are separate switches; a lobby of bots shows nothing if bots are hidden (the default is *on*).
* **Render distance** and **Max ESP players** cap what is drawn.
* **Master toggle key** or **Panic key**: if you pressed it, everything is hidden. Press it again.

## 7. A black screen

**Visuals > HUD > Fuser mode** draws a pure-black window under the overlay. Switch it off if you do not use a capture card.

## 8. Only the first few seconds are wrong

At the start of every match the world is found again (the log shows `WORLD: UWorld ... resolved`). Visibility and the wall check need a few seconds more. Wait about ten seconds.

## Still nothing?

[Collect diagnostics](collecting-diagnostics.md) and include the log (`hideway.log` and `hideway.log.1`).
