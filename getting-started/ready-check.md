# READY CHECK: is everything connected?

The **READY CHECK** card sits at the top of the **Debug** page. The same card also shows on the **Aimbot** page until everything is ready. It lists each part in **green**, **orange** or **red**, and one **Next:** line names the first thing to fix.

{% hint style="info" %}
Debug is hidden by default to keep the menu small. Turn it on with **Misc > Debug > Show debug page**.
{% endhint %}

| Row | Color | Meaning | What to do |
|---|---|---|---|
| **DMA card** | red | The card does not answer | Accept the administrator prompt; use a USB 3 port on the motherboard; power the game PC; close other programs that use the card (MemProcFS, other tools); check the FTDI driver in Device Manager. Hideway retries every 2 seconds by itself and reconnects if the cable drops later |
| **Fortnite** | orange | The card works but the game is not running on the game PC yet | Start Fortnite there and wait for the lobby |
| **Game data** | red | The game runs but its structures were not found 90 seconds after it started | This Fortnite build is newer than the offsets in `all\`. See [After a Fortnite update](../guides/after-a-fortnite-update.md) |
| **Input** | red | Aim or trigger is on but the input device is off or not connected | Misc > Input device. See [Connect an input device](../guides/input-device.md) |
| **Camera** | orange | Waiting for a view (lobby / loading screen) | Normal until a match starts |

## The top bar

| Text | Meaning |
|---|---|
| **DMA OFFLINE** | The card is not detected |
| **WAITING FOR FORTNITE** | Card OK, game not found |
| **DMA ONLINE** | Connected and reading |
| **demo** | Demo mode: synthetic data |

## OFFSET HEALTH

Below the READY CHECK, **OFFSET HEALTH** shows, line by line, which group of offsets was proven by real data (game process, world, game state, local player, camera, players, names, skeletons, health, visibility clock). After a patch the first red line points at what moved.

## DATA HEALTH

The **DATA HEALTH** card goes one step further: for every data source it says how many players actually have it right now. See [Debug and Data health](../the-menu/debug.md#data-health).

## Black screen when you start?

**Visuals > HUD > Fuser mode** puts a pure-black window under the overlay for capture-card setups. Switch it off if you do not use a capture card.
