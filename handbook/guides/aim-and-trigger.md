# Tune aim and trigger

This guide is about getting the controls to behave predictably. Everything here is a tuning control for your own setup.

{% hint style="info" %}
Aim and trigger need a connected input device ([Connect an input device](input-device.md)). In the lobby nothing happens: they need a match and a visible target.
{% endhint %}

## 1. Calibrate first

On **Aimbot > CALIBRATION**, **Counts per degree X** and **Y** are the mouse counts that turn your view by one degree. If the aim overshoots, the numbers are too high; if it undershoots, too low. Use **Test move (+/-60)** (Misc) to see a real movement, then adjust until the crosshair lands on the target.

## 2. Pick the basics

| Setting | Guidance |
|---|---|
| **Aim key** | Default Mouse 2. You can use Mouse 1; the **Only with a gun in hand** option keeps it from locking on while you place a wall |
| **Field of view** | Smaller is more selective. A narrow cone means the aim only reacts to targets near your crosshair |
| **Smoothing** | 1 is instant; higher is slower. Start high and lower it until it feels right |
| **Aim bone** | Head, Neck, Chest, Pelvis, or Closest bone |
| **Max aim distance** | Targets further than this are ignored |
| **Team check** | Keep on |

## 3. Visibility

**Visible only** (Aimbot) makes the aim ignore targets that are not visible. Visibility is judged by Raycast VisCheck against the level geometry: see [Visibility](visibility.md). If aim seems to work through walls, read that page and [Aim through walls](../troubleshooting/aim-and-trigger.md#aim-reaches-through-a-wall).

## 4. Per-weapon behaviour

* **Weapons page**: give a class its own field of view, smoothing and bone with **Override**.
* **Aimbot > CLOSE AIM**: a different field of view, smoothing and bone for close enemies.
* **Aimbot > STICKY AIM**: once close to a target, the aim stays attached; turn it off against groups.

## 5. Prediction

For moving targets: **Aimbot > PREDICTION**. Set **Projectile speed** and **gravity** (or use **Per-weapon ballistics**), and **Prediction lead** for the delay between your input and what you see.

**Measure your lead:** Debug > LATENCY > **Measure latency** (stand still in a match, hands off the mouse). It measures the mouse-to-camera delay and offers **Use as Prediction lead** / **Use as Trigger lead**.

## 6. The triggerbot

| Setting | Guidance |
|---|---|
| **Trigger mode** | *Hold key*, *Always on*, or *Toggle key* |
| **Trigger delay** and **reaction spread** | How soon after an enemy is under the crosshair it fires, and how much that varies |
| **Trigger source** | *Both (strictest)* needs the game's own crosshair trace **and** our hitbox test to agree. If the game target cannot be read it falls back to geometry and the Assist page says so |
| **Trigger visible only** | Off = fires at anyone under the crosshair, even through a wall |
| **Trigger confirm frames** | Higher = fewer one-frame flickers, slightly later |
| **Trigger hold on target** | Full-auto: keep the button down while the target stays valid (safety stop 1.5 s) |
| **Trigger indicator** | A ring at the crosshair so you can see it working |

## 7. Understand what it is doing

* The **Highlight target** option (Visuals) draws the player the aim or trigger picked in its own colour.
* The Triggerbot page shows why the trigger did or did not fire (**Last check**, with Advanced debug).
* Debug > TELEMETRY counts key-held ticks, ticks with a target and shots.

## 8. When something goes wrong

See [Aim or trigger problems](../troubleshooting/aim-and-trigger.md).
