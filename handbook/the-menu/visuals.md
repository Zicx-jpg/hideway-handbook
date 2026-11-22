# Visuals

Everything Hideway draws on players and in the world. The page opens on a **PREVIEW** card that shows your current style on sample players.

<figure><img src="../.gitbook/assets/menu-visuals.png" alt="Visuals page with the preview card"><figcaption><p>The Visuals page. The PREVIEW card shows demo data (labelled) so you can see what a toggle changes. The arrows under it change the outfit.</p></figcaption></figure>

## Cards

| Card | What is in it |
|---|---|
| **PREVIEW** | Your style on sample players. Always marked DEMO: synthetic, not a real match |
| **ESP** | **Enable ESP** (master), Show bots, Show teammates, Hide knocked players, Render distance, Far markers, Max ESP players, Box style (Off / Box / Corners / 3D box), thickness, rounding, fill, gradient |
| **SKELETON** | Skeleton, thickness, distance-scaled lines, joint dots, glow (the smooth pose and the running cycle on frozen limbs are automatic) |
| **HEAD & BARS** | Head circle (filled, size, offset); **Health + shield bars**, Low health highlight and threshold, Health numbers, Bar style (Classic / Segmented), Bar side, Damage trail |
| **INFO TEXT** | Name, **Team ID**, Distance, Weapon class, Fade in players, Platform, Kill score, Enemy ammo |
| **TRACERS** | Snaplines (with thickness), off-screen arrows (with radius) |
| **TARGET + DETAIL** | Highlight target (the player the aim or trigger picked, with its colour), Facing direction, Distance detail (LOD) |
| **HUD** | Crosshair, **Match info**, **Enemy counter**, Team panel, Squad list, Fuser mode and its toggle key |
| **LOOT ESP** | Items on the ground. See [Loot, containers and reboot cards](../guides/loot-and-world.md) |
| **REBOOT CARDS** | Marks reboot cards of dead players |
| **SPECTATORS** | Who is spectating you |
| **AUDIO ALERTS** | Generated positional tones when an enemy comes in range |
| **COLORS** | Every colour used above |

<figure><img src="../.gitbook/assets/menu-visuals-2.png" alt="Visuals page, ESP and HUD"><figcaption><p>Scrolled down: the SKELETON and HEAD & BARS cards, and the LOOT ESP card with Group identical loot.</p></figcaption></figure>

## Team ID

A small number before the name: the **game's own team number**. Everyone in the same duo / trio / squad carries the same number. The number is hidden when nobody else has it (solo play) and every team gets its own colour; both are automatic and not in the menu.

## Health and shield bars

Bars next to the box, read from the game. Read the rules on [Health and shield bars](../troubleshooting/health-and-data.md): the game does not always send enemy health, and Hideway shows **no bar** rather than an invented one.

* **Bar style**: Classic, or Segmented (split in four so 25 / 50 / 75 % are easy to read).
* **Damage trail**: the lost part of a bar drains down slowly so you can see how big a hit was.
* **Low health highlight**: a pulsing red outline on an enemy under the threshold (only when a real health value was read).

## Squad list and match info

* **Squad list**: a panel at the top right with every other squad in range: team number, members alive (and down), distance of the nearest one.
* **Match info**: players left and teams left at the top of the screen, as the game counts them. Hidden when the game gives no sensible numbers (lobby).
* **Enemy counter**: a bar under it with the enemies within 50, 150 and 300 m, the ones that are down, and the nearest one (red when someone is inside 50 m). Off by default.

## Smoothing and label spacing are automatic

How smoothly the boxes move (Smooth ESP, Balanced smoothness, the motion estimator) is always set to the best value and is not in the menu, and labels that would overlap (player names, loot, chests, vehicles) are moved apart by themselves. See [Set up the ESP](../guides/esp-setup.md) and [Automatic settings](../reference/options.md#automatic-settings-not-in-the-menu).

<figure><img src="../.gitbook/assets/menu-visuals-3.png" alt="Visuals page, lower half"><figcaption><p>Lower half: the end of the LOOT ESP card, reboot cards, spectators and audio alerts (the colours follow).</p></figcaption></figure>
