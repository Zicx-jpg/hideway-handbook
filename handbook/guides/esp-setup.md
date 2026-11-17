# Set up the ESP

A good ESP is easy to read, steady, and in the right place on the screen. Go through this once and you will rarely need to touch it again.

## 1. Start from a preset

**Config > Presets** has four starting points. A preset only changes the options it lists, so everything else stays as you had it.

| Preset | What you get |
|---|---|
| ESP only | Boxes, skeletons, names, health, radar. Aim off |
| Clean visuals | Corner boxes, name, distance and health bars |
| Full visuals | Everything on: gradients, glow, all text, lines, radar |
| Subtle aim assist | Narrow field of view, slow random smoothing, visible targets only |

If you already have settings you like, save them as a config first. Auto-save keeps backups too, see [Configs](configs.md).

## 2. Choose what to draw

All of this is on **Visuals**. Hold the cursor on a row for its explanation.

* **Box style**: Box, Corners (cleaner in a crowd) or 3D box.
* **Skeleton**: thin lines read well at distance. **Distance-scaled lines** keep far players from cluttering the screen.
* **Health + shield bars**: you will only see them where the game sends the value, which in practice means you and your squad. See [Health and shield bars](../troubleshooting/health-and-data.md).
* **Team ID**: the game's own team number in front of the name. **Team ID colours** gives each team a colour, which helps in a crowd.
* **Squad list** and **Match info**: a panel with the other squads, and the players and teams left.
* **Max ESP players** and **Render distance** limit the load in big lobbies.
* **Show bots** and **Show teammates** are separate switches. Bots get the same colours as other players (pink hidden, green visible) plus a small BOT tag next to the name.

In a crowded match, turn on **Distance detail (LOD)**: far players get thinner lines and fewer extras.

## 3. Colours: what you are looking at

* Pink: the player is not visible to you.
* Green: the player is visible.
* Blue: a teammate.
* Grey: a knocked player.
* Yellow: the player your aim or trigger has picked (**Highlight target**).

All of these can be changed under **Visuals > Colors**.

## 4. Smoothness

On **Misc**:

| Option | What it does |
|---|---|
| Smooth ESP | Boxes glide between data updates instead of stepping. On by default |
| ESP smoothness | *Responsive*, *Balanced* (default) or *Silky*. Silky smooths the most; the boxes sit a few centimetres from the raw readings |
| Motion estimator | One motion model per player, shared by the ESP and the aim lead |
| VSync | Match it to your display |

## 5. Put it in the right place

If the boxes trail the players, raise **ESP time offset** on Misc by a few milliseconds. If they run ahead, lower it. The default is 0. Run the game borderless or full screen on the monitor you actually capture.

## 6. Keep it readable

* **Fade in players**: a player entering view fades in instead of popping.
* **Avoid overlapping labels**: names and team numbers of nearby players are moved apart.
* **Hide knocked players**, if downed players clutter the screen.

<figure><img src="../.gitbook/assets/overlay-esp-radar.png" alt="Demo ESP"><figcaption><p>Demo: Team ID badges, bars, skeletons, a bot with its BOT tag.</p></figcaption></figure>

## 7. Check the load

Open **Debug > Performance**. *Tick* should be well under 10 ms and *Data age* under about 20 ms. High numbers usually point at the DMA link (cable, USB port, other USB traffic) rather than the overlay. See [ESP looks wrong](../troubleshooting/esp-quality.md).
