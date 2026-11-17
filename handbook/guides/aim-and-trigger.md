# Tune aim and trigger

Aim and trigger need a connected input device ([Connect an input device](input-device.md)). In the lobby nothing happens: they need a match and a valid target.

## 1. Check the device first

Press **Test move (+/-60)** on Misc, under Input device. The crosshair should jump. If it does not, fix the device link before touching anything on the Aimbot page.

## 2. Calibration

**Counts per degree X / Y** (Aimbot > Calibration) say how many mouse counts turn your view by one degree. Hideway measures them for you at start. If the aim overshoots, the number is too high; if it falls short, it is too low. Changed your in-game sensitivity? Calibrate again or adjust the numbers.

## 3. The basics

| Setting | Advice |
|---|---|
| Aim key | Default is Mouse 2. Mouse 1 works too, **Only with a gun in hand** stops it from locking on while you place a wall |
| Field of view | Smaller is more selective: only targets near the crosshair count |
| Smoothing | 1 is instant. Each step adds about 8 ms to the time the aim needs to get on target. Start high and lower it until it feels right |
| Aim bone | Head, Neck, Chest, Pelvis, or Closest bone |
| Max aim distance | Targets further away are ignored |
| Team check | Leave it on |

Smoothing means what it says. The aim moves in a straight, even approach to the target, and a higher number is slower but never jerky. Hideway also knows the game reacts to a mouse move about 50 ms late and allows for the movement that is still on its way, so it does not overshoot and swing back. If you have measured your own delay (step 5), it uses that instead.

## 4. Visibility

**Visible only** (Aimbot > Visibility) makes the aim ignore players the game is not drawing. How "visible" is judged is a separate choice, explained in [Visibility](visibility.md). If the aim seems to reach through a wall, read that page and [Aim or trigger problems](../troubleshooting/aim-and-trigger.md).

## 5. Prediction

For moving targets use the Prediction card on the Aimbot page: set the projectile speed and gravity, or switch on **Per-weapon ballistics**, and use **Prediction lead** for the delay between your input and what you see.

To measure that delay, stand still in a match with your hands off the mouse and press **Debug > Latency > Measure latency**. It measures the time from a mouse move to the camera moving and offers **Use as Prediction lead** and **Use as Trigger lead**.

## 6. Per-weapon settings

* **Weapons** page: give a weapon class its own field of view, smoothing, bone, trigger on/off and trigger delay with **Override**.
* **Close aim** (Aimbot page): different field of view, smoothing and bone for enemies up close.
* **Sticky aim**: once the crosshair is near a target the aim stays on it. Turn it off against groups.

## 7. The triggerbot

| Setting | Advice |
|---|---|
| Trigger mode | *Hold key*, *Always on* or *Toggle key* |
| Trigger delay and reaction spread | How soon it fires once an enemy is under the crosshair, and how much that varies |
| Trigger source | *Both* needs the game's own crosshair trace and Hideway's hitbox test to agree |
| Trigger visible only | Off means it fires at anyone under the crosshair, walls or not |
| Trigger confirm frames | Higher means fewer one-frame flickers and a slightly later shot |
| Trigger hold on target | Full-auto: keep the button down while the target stays valid |
| Trigger indicator | A ring at the crosshair so you can see it working |

## 8. See what it is doing

* **Highlight target** (Visuals) draws the player the aim or trigger picked in yellow.
* The Triggerbot page shows why the trigger did or did not fire.
* **Debug > Telemetry** counts ticks with the key held, ticks with a target and shots.

If something is off, go to [Aim or trigger problems](../troubleshooting/aim-and-trigger.md).
