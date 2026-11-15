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

## Boxes lag or run ahead

Boxes behind the players: raise **ESP time offset**. Boxes ahead: lower it. Move it a few milliseconds at a time. The default is 0.

## Boxes jitter

* **Smooth ESP** on, **ESP smoothness** Balanced or Silky.
* **Smooth skeleton** on. It anchors the skeleton on the pelvis, so limbs stop shaking when the root position steps with network updates.
* **Motion estimator** on.

Players that are falling or gliding move in small steps of about 12 cm every 33 ms. That comes from the game's own movement code, so the ESP follows it.

## Skeletons look frozen

Two different things can cause it:

1. **The game barely animates what it does not draw.** Hidden and far players change pose in only a small part of the frames, and Hideway cannot invent motion the game does not send.
2. **Reads are thinned in crowded matches.** Far players are read less often (**Thin skeleton reads**, on by default). Visible mid-range players are still refreshed several times a second. Turn **Thin skeleton reads** off only to compare, and expect more load.

A bone array with a joint more than 2.5 m from the pelvis is rejected and the last good pose is kept, so a stray limb should not show.

## Other small things

* **Labels overlap**: Visuals > Avoid overlapping labels.
* **Players pop into view**: Visuals > Fade in players.
* **The overlay is on the wrong screen**: Misc > Overlay monitor.
* **No health bar**: see [Health and shield bars](health-and-data.md).
