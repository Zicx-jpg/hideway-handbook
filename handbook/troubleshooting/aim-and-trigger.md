# Aim or trigger problems

Aim and trigger need three things: a connected input device, a match, and a valid target. The top bar shows the device state.

## Aim does nothing

Go through these in order:

1. **Enable aimbot** is on and the **Aim key** is the key you are holding. Click the key box to see what it is bound to.
2. The input device shows CONNECTED in the top bar. If not, see [Connect an input device](../guides/input-device.md).
3. Press **Test move (+/-60)** (Misc > Input device). If the crosshair does not move, the problem is the link to the device, not the aim.
4. **Only with a gun in hand** is on and you are holding a pickaxe, a build piece or an empty weapon. Hold a loaded gun.
5. A target has to be inside the **Field of view**, within **Max aim distance**, and pass **Visible only**, **Team check** and **Ignore knocked**.
6. **Wait for wall check** is on and you are in the first seconds of a match. With a ray-cast visibility style the aim pauses until the level has been read.
7. Overshooting or falling short is a calibration problem: change **Counts per degree X / Y** (Aimbot > Calibration).

## The aim jerks or swings back

The game answers a mouse move about 50 ms late. Since version 3.2.5 Hideway allows for the movement still on its way, so a well-calibrated aim approaches the target in one smooth move. If you still see it overshoot:

* Check the calibration first. A wrong **Counts per degree** makes every move too long or too short, and no smoothing can hide that.
* Lower **Smoothing** step by step, or raise it if it feels too sharp.
* On Debug, run **Latency > Measure latency** once. The measured value is then used instead of the 50 ms default.
* Make sure you run 3.2.5 or later (Config > About, or the launcher).

## Aim locks on while I place a wall

With Mouse 1 as the aim key, a click to place a wall can lock the aim onto an enemy behind it.

* **Aimbot > Only with a gun in hand** must be on (it is by default). Aim and trigger then stay off while you hold a build piece, the pickaxe or an empty weapon.
* If it still locks, look at **Debug > Local player** while you hold the wall and note the weapon id and the ammo. A build piece normally reads ammo 0. If it shows more than 0, send that id to support.

## Aim switches off with one of my weapons

The "has ammo" rule can be wrong for a weapon whose ammo cannot be read. Untick **Only with a gun in hand** to go back to the old behaviour, and tell support which weapon it was. **Debug > Local player** shows its id and ammo.

## Aim reaches through a wall

From most to least likely:

1. **Visible only** is off.
2. The visibility style is *UE5 render time only*, which can call a player behind thin cover visible. Try **Unreal line of sight** (Aimbot > Visibility > Visibility check). See [Visibility](../guides/visibility.md).
3. **A wall a player built.** The wall check only knows the level's fixed geometry, so a target behind a built wall can still count as visible.
4. It is too early in the match. Until the wall check is ready the render-time flag is all that is used, and the Visibility line says which one is active.

## Trigger fires through a wall

**Trigger visible only** must be on. With **Trigger source: Both**, the game's trace and Hideway's hitbox test must agree. If the game target cannot be read, the trigger uses the hitbox test alone and the Triggerbot page says so. Built walls are not part of the geometry.

## Trigger does not fire

* **Enable triggerbot** is on, and the **Trigger key** is held (*Hold key* mode) or the trigger is armed (*Toggle key* mode).
* The menu is open. **Trigger pause in menu** stops it on purpose.
* Check **Trigger max distance**, **Trigger team check**, and **Ignore knocked / bots**.
* You are holding something with no ammo (**Only with a gun in hand**).
* The Triggerbot page has a **Last check** line that names the reason.

## The mouse button stays down

Hideway lets go of a held button when the device disconnects, the link drops, you quit or the program crashes. If a click seems stuck, press the mouse button yourself once, or **Disconnect** the device, and tell support what you were doing.

## The weapon class is wrong

**Weapons > Detection > Holding** shows the class and the raw id. If it says *Other* for a weapon you hold, set the matching anim id for that class, or send the id to support. Only some ids are confirmed.

## Aim feels different with different weapons

Use **Weapons > Override** per class, and **Per-weapon ballistics** for prediction.
