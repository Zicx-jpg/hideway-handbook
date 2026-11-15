# After a Fortnite update

Hideway finds data in the game with a table of **offsets** (positions of fields inside the game's structures). Every Fortnite patch can move them. This release carries offsets for **Fortnite 43.00**.

## What you will see after a patch

| Symptom | Cause |
|---|---|
| **Game data** red in READY CHECK, 90 s after the game started | The game's structures were not found: the offsets are older than the game |
| No ESP, but the game is running | Same cause, or you are not in a match |
| Players = 0 in a match | Player offsets are stale, or the server is empty |
| Names blank, or skeleton missing, but boxes work | A single group of offsets moved |

**Debug > OFFSET HEALTH** shows which group is wrong: Game process, World, Game state, Local player, Camera, Players, Names, Skeletons, Health, Visibility clock. The first red line points at what moved.

Expect a **short period without ESP** after a patch, until a new dump has been made and released.

## What to do

1. Check the **Updates** page of the launcher: a release with new offsets may already be available. Install it.
2. If there is none yet, wait. Hideway cannot work with offsets that do not match the build, and guessing them would give wrong data.
3. Use **Copy diagnostics** (Debug > OFFSET HEALTH) and send it to support with the Fortnite build number if the problem lasts.

{% hint style="info" %}
The offsets in `all\` must match the **exact** Fortnite build you run. Hideway also checks the game's executable fingerprint on attach and warns in the log when the build is not the one the offsets were made for.
{% endhint %}

