# No ESP

Turn on **Misc > Debug > Show debug page**, open Debug, and keep READY CHECK, OFFSET HEALTH and DATA HEALTH in view while you go through this.

## 1. Are you in a match?

The lobby has nobody to draw. OFFSET HEALTH says "none in view" for the other players until a match starts, and during the bus phase there are few players. Boxes appear once the match has begun.

## 2. World not found

OFFSET HEALTH shows **World** in red with a note that the GEngine / World / Level offsets are probably outdated. The game was patched. See [After a Fortnite update](../guides/after-a-fortnite-update.md).

## 3. Camera not valid

Same cause, or you are on a loading screen. The log prints "camera no longer valid (loading screen / lobby)" at match changes, which is normal.

## 4. Zero players in a match

Either the server is empty or the player offsets are out of date. **DATA HEALTH > Names** tells you how many of the players that were read have a name.

## 5. Boxes are drawn but not on the players

* Change **ESP time offset** (Misc) by a few milliseconds.
* The game must run borderless or full screen on the same monitor you capture.
* Check **Overlay monitor** on Misc.

## 6. A switch or a filter is hiding them

* **Visuals > ESP > Enable ESP** must be on.
* **Show bots** and **Show teammates** are separate. A lobby full of bots shows nothing if bots are hidden (they are shown by default).
* **Render distance** and **Max ESP players** limit what is drawn. A low **Render distance** (150 m for example) hides every enemy farther away: they come back as soon as they get closer. Raise it, and keep **Far markers** on so players beyond it still show a marker with their distance.
* Did you press the **Master toggle key** or the **Panic key**? Everything is hidden until you press it again.

## 7. A black screen

**Visuals > Fuser mode** draws a pure black window under the overlay. Turn it off if you do not use a capture card.

## 8. Only the first seconds look wrong

At the start of every match the world is found again (the log shows "UWorld ... resolved"). Visibility and the wall check need a few more seconds. Give it ten.

## Still nothing?

[Collect diagnostics](collecting-diagnostics.md) and send the log files with them (`hideway.log` and `hideway.log.1`).
