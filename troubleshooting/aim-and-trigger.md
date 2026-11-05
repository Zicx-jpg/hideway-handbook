# Aim or trigger problems

First rule: aim and trigger need a **connected input device**, a **match**, and a **valid target**. Check the top bar for the device state.

## Aim does nothing

Work through these:

1. **Enable aimbot** is on (Aimbot page) and the **Aim key** is the key you are holding. Click the key box to see what it is bound to.
2. The input device is **CONNECTED** (top bar). If not, [Connect an input device](../guides/input-device.md).
3. Press **Test move (+/-60)** (Misc > INPUT DEVICE). If the crosshair does not move, the problem is the device link, not aim.
4. **Only with a gun in hand** (Aimbot page): aim is off while you hold a pickaxe, a build piece or an empty weapon. Hold a loaded gun.
5. A target must be inside the **Field of view**, within **Max aim distance**, and pass **Visible only** / **Team check** / **Ignore knocked**.
6. **Wait for wall check** (default on): with a ray-cast visibility style, aim pauses until the wall check has read the level, a few seconds into a match.
7. The overshoot / undershoot is a **calibration** problem: tune **Counts per degree X / Y** (Aimbot > CALIBRATION).

## Aim locks on while I place a wall

This was a real bug fixed in **2.10.2**. With **Mouse 1** as the aim key, a click to place a wall made the aim lock onto an enemy behind it.

* Make sure you run **2.10.2 or later** (Config > ABOUT, or the launcher).
* **Aimbot > Only with a gun in hand** must be **on** (default). Aim and trigger then stay off while you hold a build piece, the pickaxe or an empty weapon.
* If it still locks, look at **Debug > LOCAL PLAYER** while holding the wall: note the **Weapon** id and **Ammo**. A build piece normally shows ammo 0. If it shows a number above 0, send that id to support.

{% hint style="info" %}
The rule is derived from a recorded match: the pickaxe read ammo 0 in all frames and the build tool in about 95 %, firearms 1 to 30. If the game's weapon cannot be read, aim keeps working as before.
{% endhint %}

## Aim switches off with one of my weapons

The "has ammo" rule can misjudge a weapon whose ammo is not readable. Untick **Only with a gun in hand** to go back to the old behaviour, and tell support which weapon it was. **Debug > LOCAL PLAYER** shows its id and ammo.

## Aim reaches through a wall

Several reasons, from most to least common:

1. **Visible only** is off.
2. The **visibility style** is *UE5 render time only*: a player drawn behind **thin cover** counts as visible. Try **Unreal line of sight** (Aimbot > VISIBILITY > Visibility check). See [Visibility](../guides/visibility.md).
3. **A wall that a player built.** The wall check reads the level's static geometry only; it does not know about built walls. A target behind a built wall can still count as visible.
4. Too soon in a match: before the wall check is ready, aim uses the render-time flag alone (the Visibility line says which one is in use).

## Trigger fires through a wall

**Trigger visible only** must be on. With **Trigger source: Both** (default), the game's own crosshair trace and our hitbox test must both agree. If the game target cannot be read, the trigger falls back to geometry and the Assist page says so. Remember that built walls are not in the geometry.

## Trigger does not fire

* **Enable triggerbot** on, **Trigger key** held (in *Hold key* mode) or armed (*Toggle key* mode).
* Menu open? **Trigger pause in menu** stops it by design.
* **Trigger max distance**, **Trigger team check**, **Ignore knocked / bots**.
* Holding something with no ammo (**Only with a gun in hand**).
* The Assist page's **Last check** line (with Advanced debug) names the reason.

## The mouse button stays down

Hideway releases a held button on disconnect, link loss, shutdown and crash. If a click seems stuck, press the mouse button yourself once, or **Disconnect** the device. Tell support the situation.

## The weapon class is wrong

**Weapons > DETECTION > Holding** shows the class and raw id. If it says `Other` for a weapon you hold, set the matching **anim id** for that class, or report the id. Only some ids are confirmed on 43.00.

## Aim feels off at different weapons

Use **Weapons > Override** per class, and **Per-weapon ballistics** for prediction.
