# ESP looks wrong

Names missing, boxes that jump or lag, frozen skeletons. Start with the part that matches what you see.

## Names are blank

Hideway reads names with the layout of the current build and, if that gives nothing, finds the name field by scanning. This usually takes a few seconds after a match starts, and during that time you may see short names or none.

* **Debug > Data health > Names** shows how many players have a name.
* If boxes work but names stay empty, turn **Name** off and send diagnostics.
* Bots have names too. If you cannot see bots, check **Show bots**.

## The ESP is choppy

1. Open **Debug > Performance**. *Tick* should be well under 10 ms and *Data age* under about 20 ms. Higher values point at the DMA link (cable, USB port, other USB traffic) before the overlay.
2. The fast paths (**Fast DMA reads**, the **High-rate camera lane**, **Fast position refresh**, **Thin skeleton reads**, **DMA stall guard**) and the smoothing (**Smooth ESP**, **ESP smoothness**, **Motion estimator**) are automatic: always on, not in the menu. The fast reads check themselves against live data when the game is attached and switch back on their own if something is wrong.
3. Reduce the load: fewer skeletons, no glow, a lower FPS limit, **Distance detail (LOD)**.
4. A black Fuser window on the same GPU as the game competes for GPU time. Run it on the overlay PC only.
5. Still choppy? Turn on **Debug > RECORDING > Rolling recorder**, play, and press the **Save last minutes key** right after it happens; send the file (see [Collect diagnostics](collecting-diagnostics.md)). The black box's **frame(ms)** column tells an overlay hitch from slow data.

If **Tick** sits at 100 ms or more for a long time, send the log. In the log, the line "scatter reads DISAGREE with single reads" means Hideway switched to the slow way of reading; it tries the fast way again after a few seconds.

## Boxes flash between two colours

 The colour follows the game's own *drawn recently* flag, which blinks when a player is at the edge of the view or behind a thin object. Since 3.6.1 a player that was visible a moment ago keeps the visible colour for 150 ms, so most of the flashing is gone. A box that is white for a long time is really hidden from the game's renderer: behind a wall, a hill or a build.

## Boxes lag or run ahead

Hideway draws every box for the moment the frame is shown (the **ESP time offset** is automatic and fixed at 0, it is not in the menu). A box that trails or leads the picture by the same amount all the time is usually the delay of the capture path: a capture card and the fuser put the game image one to three frames behind what Hideway knows, so the boxes seem to run **ahead** of the image. Use the capture card's low-latency mode and a capture path without extra buffering. If the gap changes while you play, that is a data delay: check **Debug > PERFORMANCE** (*Data age*) and send a recording.

## Boxes jitter

* The smoothing (**Smooth ESP**, Balanced, the **Motion estimator**) is automatic and always on.
* The skeleton is anchored on the pelvis automatically, so limbs stop shaking when the root position steps with network updates (no option to set).
* Check **Debug > PERFORMANCE**: a *Data age* well over 20 ms or a *Tick* near 10 ms makes any box step.

Players that are falling or gliding move in small steps of about 12 cm every 33 ms. That comes from the game's own movement code, so the ESP follows it.

## Skeletons look frozen

Two different things can cause it:

1. **The game barely animates what it does not draw.** Hidden and far players change pose in only a small part of the frames. Since 3.2.7 a running player with a frozen pose gets a running cycle on the arms and legs automatically (since 3.3.3 there is no switch for it). It is only drawn, never used for aim.
2. **Reads are thinned in crowded matches.** Far players are read less often (**Thin skeleton reads**, automatic). Visible mid-range players are still refreshed several times a second.

A bone array with a joint more than 2.5 m from the pelvis is rejected and the last good pose is kept, so a stray limb should not show.

## An enemy vanishes for a few seconds

Check these in order:

1. **Visuals > ESP > Render distance.** Anything beyond it gets no full ESP. This was the cause of most reports (150 m with players read at 200-380 m). The default is 500 m. With **Far markers** on, a player beyond the range still shows a small marker with its distance.
2. **Is the player really in front of you?** The ESP draws players on screen. Behind you or outside the view they are not drawn; **Off-screen arrows** points at them.
3. **Hide knocked players**, **Show bots**, **Show teammates** also filter.
4. Still wrong? Open **Debug** and save the black box, or send `hideway.log` and the newest file in the `blackbox` folder. The columns say what happened: *far* (markers drawn), *seen* (enemies the game itself rendered on screen). A line starting with **REAL** means the game rendered enemies on screen while the ESP drew none: that is a true disappearance and the file says when.

## Other small things

* **Labels overlap**: names and team numbers of players, and the labels of loot, chests and vehicles, are moved apart automatically.
* **Players pop into view**: Visuals > Fade in players.
* **The overlay is on the wrong screen**: Misc > Overlay monitor.
* **No health bar**: see [Health and shield bars](health-and-data.md).
