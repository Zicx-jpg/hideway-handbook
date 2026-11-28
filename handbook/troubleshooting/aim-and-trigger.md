# Aim or trigger problems

Aim and trigger need three things: a connected input device, a match, and a valid target. The top bar shows the device state.

## Aim does nothing

Go through these in order:

1. **Enable aimbot** is on and the **Aim key** is the key you are holding. Click the key box to see what it is bound to.
2. The input device shows CONNECTED in the top bar. If not, see [Connect an input device](../guides/input-device.md).
3. Press **Test move (+/-60)** (Misc > Input device). If the crosshair does not move, the problem is the link to the device, not the aim.
4. You are holding a pickaxe, a build piece or an empty weapon: aim and trigger stay off then (**Only with a gun in hand** is automatic). Hold a loaded gun.
5. A target has to be inside the **Field of view**, within **Max aim distance**, and pass **Team check** and **Ignore knocked**. It also has to be visible: the aim only goes for players the game is drawing on screen.
6. You are in the first seconds of a match. With the wall check the aim waits until the level has been read.
7. The aim seems to land short or long every time: Hideway measures the mouse counts per degree itself once per match (Debug shows the result). Send the log if it stays wrong.

## The aim jerks or swings back

The game answers a mouse move about 50 ms late. Since version 3.2.5 Hideway allows for the movement still on its way, so a well-calibrated aim approaches the target in one smooth move. If you still see it overshoot:

* Lower **Smoothing** step by step, or raise it if it feels too sharp.
* On Debug, run **Latency > Measure latency** once. The measured value is then used instead of the 50 ms default.
* Make sure you run 3.2.5 or later (Config > About, or the launcher).
* Still wrong? Send the log and a recording: press the **Save last minutes key** (**Debug > RECORDING**, the Rolling recorder is on by default) right after the jerk (see [Collect diagnostics](collecting-diagnostics.md)).

## Aim locks on while I place a wall

With Mouse 1 as the aim key, a click to place a wall can lock the aim onto an enemy behind it.

* **Only with a gun in hand** is automatic (always on): aim and trigger stay off while you hold a build piece, the pickaxe or an empty weapon.
* If it still locks, look at **Debug > Local player** while you hold the wall and note the weapon id and the ammo. A build piece normally reads ammo 0. If it shows more than 0, send that id to support.

## Aim switches off with one of my weapons

The "has ammo" rule can be wrong for a weapon whose ammo cannot be read. There is no switch for it: tell support which weapon it was and send what **Debug > Local player** shows (its id and ammo).

## Aim reaches through a wall

From most to least likely:

1. **A wall a player built.** Visibility comes from what the renderer drew and from the game's own crosshair trace (which stops the aim when it ends in front of the player, once it has proven it works), not from level geometry, which has no player-built walls. If it keeps happening behind builds, send a recording.
2. The game draws a player behind thin cover and calls them visible (the aim follows the game's own render time). See [Visibility](../guides/visibility.md).
3. It is too early in the match. Until the wall check is ready the render-time flag is all that is used.

The visibility rule is on the Aimbot page, card **VISIBILITY CHECK** (since 3.8.4): **Visible only**, **Visibility check** (the method), **Visibility tolerance** and **Wait for wall check**. A weapon tab with **Override** on uses its own **Visible only**.

## Trigger fires through a wall

**Trigger visible only** must be on. The game's trace and Hideway's hitbox test must agree (the trigger source is automatic and always the strictest). If the game target cannot be read, the trigger uses the hitbox test alone; with **Misc > Advanced debug** on, the Triggerbot page says so.

## Trigger does not fire

* **Enable triggerbot** is on, and the **Trigger key** is held (*Hold key* mode) or the trigger is armed (*Toggle key* mode).
* The menu is open. **Trigger pause in menu** stops it on purpose.
* Check **Trigger max distance**, **Trigger team check**, and **Trigger ignore knocked / bots**.
* You are holding something with no ammo (**Only with a gun in hand**, automatic).
* With **Misc > Advanced debug** on, the Triggerbot page has a **Last check** line that names the reason.

## The mouse button stays down

Hideway lets go of a held button when the device disconnects, the link drops, you quit or the program crashes. If a click seems stuck, press the mouse button yourself once, or **Disconnect** the device, and tell support what you were doing.

## The weapon class is wrong

**Debug > Local player** shows the class and the raw id of the weapon you hold. If it says *Other* for a weapon you hold, send the id to support: the id table is automatic and only partly known (pistol, shotgun and rifle are confirmed).

## Aim feels different with different weapons

Use **Weapons > Override** per class. Prediction already uses the real bullet speed and drop of the weapon in your hand.
