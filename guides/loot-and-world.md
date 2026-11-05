# Loot, containers and reboot cards

All of these are **read-only** drawings of things that lie in the world. They are found live and drawn only after Hideway has proved it understands the game's layout.

## Loot ESP

**Visuals > LOOT ESP > Enable loot ESP.**

{% hint style="warning" %}
Loot ESP needs the **Wall check** on (Misc > ENGINE), because it uses the level layout. Without it the Debug page says *NOT RUNNING: Wall check is off*.
{% endhint %}

| Option | What it draws |
|---|---|
| Loot weapons / ammo / heals / shields / grenades / materials / traps / other items | Groups of ground items |
| **Loot minimum rarity** | Hide items below this rarity. Items whose rarity could not be read are drawn white |
| **Loot max distance** | Do not draw items further away |
| Loot marker / distance text / snaplines | How each item is marked |
| **Show containers** | Chests, ammo boxes, coolers, llamas and similar, recognised by their display name |
| **Hide opened containers** | The reader learns the "opened" flag by watching containers get opened, so it only works after a few have been opened |
| **Show vehicles** | Vehicles by display name, refreshed every 0.7 s |
| **Show other named actors** | Everything else with a display name (usually noise, for checking what the reader sees) |

**Debug > LOOT READER** shows what it found: layout state (searching / verified), counts, rejects, rarity. The log has `LOOT` lines. On 43.00 the loot reader has been seen working in real matches.

## Reboot cards

**Visuals > REBOOT CARDS > Enable reboot cards** marks the reboot cards of dead players whose squad can still bring them back: a ring at the place they died, the owner's nickname, the seconds left and the distance. A card is drawn only after its numbers pass sanity checks. **Debug > REBOOT CARDS** and the `REBOOT` log lines show its state. This one has not been verified in a real match yet.

## Spectators

**Visuals > SPECTATORS** shows who is spectating you (names, bots marked) and logs changes. Read-only. **Spectators: ignore teammates** leaves your own team out. The layout it reads comes from a community post and is checked on every read: the log says so when it does not match this build.

## Audio alerts

**Visuals > AUDIO ALERTS**: a short positional tone (left / right / distance) when an enemy comes inside the alert range, and when somebody starts spectating you. Tones are generated, no sound files. Off by default. **Audio alert range**, **volume** and **device** are adjustable.

## Match info and squad list

* **Match info**: players left and teams left at the top, as the game counts them (hidden in the lobby).
* **Squad list**: other squads in range with their team number.
