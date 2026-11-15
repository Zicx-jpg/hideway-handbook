# Is everything connected?

The READY CHECK card is at the top of the **Debug** page, and it also appears on the **Aimbot** page until everything is ready. Each part is green, orange or red, and the **Next:** line names the first thing to deal with.

Debug is hidden to keep the menu short. Turn it on with **Misc > Debug > Show debug page**.

| Row | Colour | What it means | What to do |
|---|---|---|---|
| DMA card | red | The card does not answer | Accept the administrator prompt, use a USB port on the motherboard, power the game PC, close other programs that talk to the card, check the FTDI driver in Device Manager. Hideway retries every 2 seconds and reconnects by itself if the cable drops later |
| Fortnite | orange | The card works, the game is not running yet | Start Fortnite on the game PC and wait for the lobby |
| Game data | red | The game runs but its structures were not found 90 seconds after start | This Fortnite build is newer than the data you have. See [After a Fortnite update](../guides/after-a-fortnite-update.md) |
| Input | red | Aim or trigger is on but the input device is off or not connected | Misc > Input device. See [Connect an input device](../guides/input-device.md) |
| Camera | orange | Waiting for a view | Normal in the lobby and on loading screens |

## The status in the top bar

* **DMA OFFLINE**: the card is not detected.
* **WAITING FOR FORTNITE**: the card is fine, the game is not found.
* **DMA ONLINE**: connected and reading.
* **demo**: generated data.

## Offset health

Under the READY CHECK, **OFFSET HEALTH** goes line by line through what was proven with real data: game process, world, game state, local player, camera, players, names, skeletons, health and the visibility clock. After a patch, the first red line shows what moved.

## Data health

**DATA HEALTH** goes one step further and shows, for every kind of information, how many of the players in the match have it right now. See [Debug](../the-menu/debug.md).

## A black screen at start

**Visuals > Fuser mode** puts a pure black window under the overlay. It is meant for capture-card setups. If you do not use a capture card, turn it off.
