# Debug and Data health

The Debug page shows what Hideway is really getting from the game. It is **hidden by default**: turn it on with **Misc > Debug > Show debug page**.

## Cards

| Card | What it tells you |
|---|---|
| **READY CHECK** | The first thing to fix, in green / orange / red. See [READY CHECK](../getting-started/ready-check.md) |
| **STATUS** | DMA state, overlay FPS, offsets in use, last error |
| **DATA HEALTH** | One row per data source, with the share of players that have it. See below |
| **DMA LINK** | Disconnect / reconnect the card without closing Hideway (so you can re-plug it) |
| **OFFSET HEALTH** | Which offset group was proven by real data |
| **PERFORMANCE** | Frame time, spread, hitches, render thread cost, player-lane rate, card traffic, data age on screen |
| **LOCAL PLAYER** | Your held weapon (class and raw id), ammo, team, position |
| **LOOT READER** | What the loot reader found about the game's item layout |
| **REBOOT CARDS** | State of the reboot card reader |
| **TELEMETRY** | Measured prediction error, data age, visibility flips, aim and trigger counters |
| **LATENCY** | Measure the mouse-to-camera delay and use it as Prediction / Trigger lead |
| **RECORDING** | A flight recorder for sharing a session with support |
| **LIVE LOG** | Real events with timestamps, with **Copy log** |
| **ADDRESSES**, **PLAYERS** | Raw addresses and the player list (Advanced debug / Player list) |

## DATA HEALTH

Added in 2.10.1. One table, one row per data source, with a state and the share of players that have it right now.

| State | Meaning |
|---|---|
| **LIVE** | Nearly every player (at least 90 %) has it |
| **PARTIAL** | Only some do. The row says which, for example *teammates only; no enemy value is sent* |
| **MISSING** | It should be there and is not |
| **WAITING** | Nothing to judge yet: lobby, loading screen, nobody in view |
| **OFF** | You turned the option off |

Rows: **Names**, **Team ID**, **Health / shield**, **Weapon**, **Skeleton**, **Visibility: render time**, **Visibility: wall check**, **Visibility: submit time**, **Loot**, **Match counters**.

{% hint style="info" %}
A lobby is *WAITING*, never *MISSING*: nothing is broken just because nobody is there. An option you turned off is *OFF*, not *MISSING*.
{% endhint %}

**Copy data health** copies the table as text. **Copy diagnostics** (in the OFFSET HEALTH card) includes it, plus versions, offset status, performance and the log. It never contains your license key.

## OFFSET HEALTH rows

Game process · World · Game state · Local player · Camera · Other players · Names · Skeletons · Health · Visibility clock. Each line is proven by data the reader actually returned, so after a game update the first red line points at what moved.

## LATENCY

**Measure latency** sends ten tiny mouse moves (net zero) and times how long the game camera takes to answer. Stand still in a match with your hands off the mouse. The result suggests a **Prediction lead** and **Trigger lead**, with buttons to use them.
