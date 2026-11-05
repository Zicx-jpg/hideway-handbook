# The game closes or crashes

Two different things can look like "a crash". Find out which one you have first.

| It was... | You see | Where to look |
|---|---|---|
| **Fortnite** that closed | The game window disappears. Hideway keeps running and says `GAME: Fortnite process ended` | The log (below) and the game PC's crash folder |
| **Hideway** that closed | The overlay disappears but the game keeps running | `hideway.log` has a `FATAL` line |

## How to tell

Open `hideway.log` **and** `hideway.log.1` (the older half of the log) in `core\`.

* A line `FATAL exception 0x... at module+0xRVA` followed by `FATAL stack: ...` means **Hideway** crashed. Send both logs.
* No `FATAL` line, but `GAME: Fortnite process ended - waiting for it to start again` means the **game** ended. Hideway noticed and waited for it to start again.
* The overlay simply being gone with no `FATAL` and no `GAME:` line usually means it was closed (End key, Task Manager) or Windows ended it.

Hideway also releases a held mouse button if it crashes, so a crash never leaves the button stuck.

## What the logs showed for "Fortnite closes"

In logs from 3 and 4 November, **no Hideway crash was recorded**. The log showed Fortnite ending **three times, each 3 to 11 seconds after a match ended** (right after `WORLD: UWorld lost (loading screen / match transition)`). Hideway keeps running through it and re-attaches when the game starts again.

{% hint style="info" %}
This is what the log shows; it does not prove why the game closed. Hideway only sees the process end. A match end is also when the game changes worlds, so that is where a game-side problem would show up.
{% endhint %}

## Get the game's own crash report

Fortnite writes crash information **on the game PC**:

```
%LOCALAPPDATA%\FortniteGame\Saved\Crashes
```

A folder there with the time of your crash holds the game's own reason. Send its contents (or its `CrashContext.runtime-xml`) to support together with your Hideway logs.

## Reduce the load while you investigate

If you suspect that heavy reading at match transitions is a factor, you can test, one change at a time:

1. **Misc > ENGINE > Thin skeleton reads** on (default).
2. Turn off **Loot ESP**, **Reboot cards** and **Spectators** for a few matches.
3. Keep the **DMA stall guard** on.
4. Note whether the game still closes at the end of a match.

Hideway is read-only toward the game: it does not write to game memory. Whether heavy read traffic over the card has any effect on the game PC is **not established**, so do not treat these steps as a fix; treat them as a way to narrow down the cause.

## If Hideway itself crashed

Send:

1. `hideway.log` and `hideway.log.1`.
2. **Copy diagnostics** output (before the next start, if you can), or the support bundle from the launcher's **System** page.
3. What you were doing: which page was open, which option you had just changed.

The `FATAL stack` line names the module and the call chain, which is usually enough to find the cause.

## Windows Error Reporting

Windows also records application crashes in **Event Viewer > Windows Logs > Application** (source *Application Error*, event 1000). Include the fault module and the offset if Hideway.exe shows up there.
