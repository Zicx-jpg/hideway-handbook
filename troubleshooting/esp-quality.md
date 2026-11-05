# ESP quality: names, choppy, offset, skeleton

## Names are blank

Name decoding depends on the string layout of the current build. Hideway tries the known layouts and finds the name field by scanning. On 43.00 the custom name was found and read live.

* **Debug > DATA HEALTH > Names** shows `N of M players`.
* If names stay empty while boxes work, turn **Name** off and report it with a diagnostics copy.
* Bots are named too; if you cannot see bots, check **Show bots**.

## Choppy ESP

1. **Debug > PERFORMANCE**: *Tick* well below 10 ms and *Data age* below about 20 ms. High values point at the DMA link (cable, USB port, other USB traffic) rather than the overlay.
2. Keep **Fast DMA reads** and **High-rate camera lane** on (default). They self-verify at attach and fall back by themselves.
3. Turn on **Fast position refresh** (Misc > ENGINE) in crowded matches.
4. Lower the load: fewer players with skeleton, no glow, lower FPS limit, **Distance detail (LOD)**.
5. Make sure **Smooth ESP** is on and try **ESP smoothness: Silky** (Misc).
6. A black **Fuser** window on the same GPU as the game competes for GPU time; run it on the overlay PC only.

## Boxes lag or lead

Boxes **trail** the players: raise **ESP time offset**. Boxes **lead**: lower it. Do it a few milliseconds at a time. The default is 0.

## Boxes jitter

* **Smooth ESP** on, **ESP smoothness** Balanced or Silky.
* **Smooth skeleton** on: it anchors the skeleton on the pelvis, so limbs stop shaking when the root position steps with network updates.
* **Motion estimator** on.

## Skeletons look static

Two separate things can make a skeleton look frozen:

1. **The game does not animate hidden or far players much.** On recordings, hidden players' poses changed in only about 12 to 23 % of frames, because the game itself stops updating the pose of things it does not draw. Nothing in Hideway can make a hidden player's skeleton move when the game's data does not.
2. **Hideway thinned the reads.** In crowded matches, distant players are read less often (**Thin skeleton reads**, on by default). Since 2.9.1 a pose is refreshed by **time** (14 ms mid-range, 28 ms far) instead of by tick count, so visible mid-range players are smooth. Turn **Thin skeleton reads** off only to compare, expecting more load.

## Skeleton has a stray limb

A bone array with a joint more than 2.5 m from the pelvis is refused (2.10.0), and the last good pose is kept instead.

## Health bar missing

See [Health and shield bars](health-and-data.md).

## Labels overlap

Turn on **Avoid overlapping labels** (Visuals > HUD).

## Players pop into view

Turn on **Fade in players** (Visuals > HUD).

## The overlay does not cover the right screen

**Misc > Overlay monitor**: choose the screen the overlay (and the fuser window) covers.
