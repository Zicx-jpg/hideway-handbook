# ESP looks wrong

Names missing, boxes that jump or lag, frozen skeletons. Start with the part that matches what you see.

## Names are blank

Hideway reads names with the layout of the current build and, if that gives nothing, finds the name field by scanning. This usually takes a few seconds after a match starts, and during that time you may see short names or none.

* **Debug > Data health > Names** shows how many players have a name.
* If boxes work but names stay empty, turn **Name** off and send diagnostics.
* Bots have names too. If you cannot see bots, check **Show bots**.

## The ESP is choppy

1. Open **Debug > Performance**. *Tick* should be well under 10 ms and *Data age* under about 20 ms. Higher values point at the DMA link (cable, USB port, other USB traffic) before the overlay.
2. Keep **Fast DMA reads** and **High-rate camera lane** on. They check themselves when the game is attached and switch back on their own if something is wrong.
3. Turn on **Fast position refresh** (Misc > Engine) for crowded matches.
4. Reduce the load: fewer skeletons, no glow, a lower FPS limit, **Distance detail (LOD)**.
5. Make sure **Smooth ESP** is on and try **ESP smoothness: Silky**.
6. A black Fuser window on the same GPU as the game competes for GPU time. Run it on the overlay PC only.

If **Tick** sits at 100 ms or more for a long time, send the log. In the log, the line "scatter reads DISAGREE with single reads" means Hideway switched to the slow way of reading; it tries the fast way again after a few seconds.

## Boxes flash between two colours

 The colour follows the game's own *drawn recently* flag, which blinks when a player is at the edge of the view or behind a thin object. Since 3.6.1 a player that was visible a moment ago keeps the visible colour for 150 ms, so most of the flashing is gone. A box that is white for a long time is really hidden from the game's renderer: behind a wall, a hill or a build.

## Boxes lag or run ahead

Boxes behind the players: raise **ESP time offset**. Boxes ahead: lower it. Move it a few milliseconds at a time. The default is 0.

## Boxes jitter

* **Smooth ESP** on, **ESP smoothness** Balanced or Silky.
* The skeleton is anchored on the pelvis automatically, so limbs stop shaking when the root position steps with network updates (no option to set).
* **Motion estimator** on.

Players that are falling or gliding move in small steps of about 12 cm every 33 ms. That comes from the game's own movement code, so the ESP follows it.

## Skeletons look frozen

Two different things can cause it:

1. **The game barely animates what it does not draw.** Hidden and far players change pose in only a small part of the frames. Since 3.2.7 a running player with a frozen pose gets a running cycle on the arms and legs automatically (since 3.3.3 there is no switch for it). It is only drawn, never used for aim.
2. **Reads are thinned in crowded matches.** Far players are read less often (**Thin skeleton reads**, on by default). Visible mid-range players are still refreshed several times a second. Turn **Thin skeleton reads** off only to compare, and expect more load.

A bone array with a joint more than 2.5 m from the pelvis is rejected and the last good pose is kept, so a stray limb should not show.

## An enemy vanishes for a few seconds

Check these in order:

1. **Visuals > ESP > Render distance.** Anything beyond it gets no full ESP. This was the cause of most reports (150 m with players read at 200-380 m). The default is 500 m. With **Far markers** on, a player beyond the range still shows a small marker with its distance.
2. **Is the player really in front of you?** The ESP draws players on screen. Behind you or outside the view they are not drawn; **Off-screen arrows** points at them.
3. **Hide knocked players**, **Show bots**, **Show teammates** also filter.
4. Still wrong? Open **Debug** and save the black box, or send `hideway.log` and the newest file in the `blackbox` folder. The columns say what happened: *far* (markers drawn), *seen* (enemies the game itself rendered on screen). A line starting with **REAL** means the game rendered enemies on screen while the ESP drew none: that is a true disappearance and the file says when.

## Other small things

* **Labels overlap**: Visuals > Avoid overlapping labels.
* **Players pop into view**: Visuals > Fade in players.
* **The overlay is on the wrong screen**: Misc > Overlay monitor.
* **No health bar**: see [Health and shield bars](health-and-data.md).
