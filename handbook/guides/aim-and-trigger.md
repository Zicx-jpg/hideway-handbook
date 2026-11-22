# Tune aim and trigger

Aim and trigger need a connected input device ([Connect an input device](input-device.md)). In the lobby nothing happens: they need a match and a valid target.

## 1. Check the device first

Press **Test move (+/-60)** on Misc, under Input device. The crosshair should jump. If it does not, fix the device link before touching anything on the Aimbot page.

## 2. Calibration

**Counts per degree X / Y** (Aimbot > Calibration) say how many mouse counts turn your view by one degree. Hideway measures them for you at start. If the aim overshoots, the number is too high; if it falls short, it is too low. Changed your in-game sensitivity? Calibrate again or adjust the numbers.

## 3. The basics

| Setting | Advice |
|---|---|
| Aim key | Default is Mouse 2. It can also be a **controller button** (see below). Mouse 1 works too, **Only with a gun in hand** stops it from locking on while you place a wall |
| Field of view | Smaller is more selective: only targets near the crosshair count |
| Smoothing | 1 is instant. Each step adds about 8 ms to the time the aim needs to get on target. Start high and lower it until it feels right |
| Aim bone | Head, Neck, Chest, Pelvis, or Closest bone. **Head** aims about 3 cm above the head joint, where the game's own hit trace lands (it counts a head hit up to about 16 cm above the joint); the triggerbot's head area is a 13 cm sphere around that point. **Closest bone** aims at the point of the body nearest to your crosshair, between the joints. A chosen part that is behind a wall falls back to the nearest exposed part |
| Max aim distance | Targets further away are ignored |
| Team check | Leave it on |

The **Field of view** is measured to the part you chose: at close range the head sits far above the chest, so a small field of view may not engage there. Use **Close aim** (its own field of view and bone for enemies up close), a bigger field of view, or **Closest bone**.

Smoothing means what it says. The aim moves in a straight, even approach to the target, and a higher number is slower but never jerky. Hideway also knows the game reacts to a mouse move about 50 ms late and allows for the movement that is still on its way, so it does not overshoot and swing back. If you have measured your own delay (step 5), it uses that instead.

The lock is kept through short interruptions: if the game stops drawing the locked player for a moment (the edge of the view, a thin occluder), the aim keeps it for 200 ms, and when nobody qualifies for a moment the lock and the ease-in progress are kept for 300 ms, so the aim does not start again from zero every time. A wall that really stands in the way still stops it (the wall check and the game's own crosshair trace decide).

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

## Use a controller button

The **Aim key** and the **Trigger key** can be a controller button: click the box, then press the button (the box says *key or pad*). LT / RT are good hold keys.

The **CONTROLLER** card on the Aimbot page shows what Hideway sees: how many pads are connected and which buttons are held right now, so you can check a pad before binding it. **Trigger pull** sets how far LT or RT must be pulled (0-255, default 30) before it counts as pressed; raise it if a light touch fires it.

* It works with an **Xbox pad, or any pad Windows shows as an Xbox pad** (DualShock / DualSense through DS4Windows or Steam Input, an adapter that appears as an Xbox pad), connected to the **overlay PC**.
* A pad that is only plugged into the **game PC** cannot be read: nothing in the DMA link sees it. Use a mouse button there, or an adapter that also shows up on the overlay PC.
* The aim itself still moves through your input device ([Connect an input device](input-device.md)).

### Controller on the game PC (Ferrum or MAKCU, no XIM)

If your controller is only plugged into the game PC, Hideway still sees it: it reads the game's own input table through the DMA card, nothing runs on the game PC and no adapter is needed.

1. Open the **Aimbot** page. The **CONTROLLER** card should say **Game PC pad: readable** once you are in a match (it needs the game running and the DMA card connected).
2. Click the **Aim key** box (or **Trigger key**) and press the button on your controller, for example **RT**. The box shows *Game pad RT*.
3. **Held in game** on the card lists the keys the game says are held: press the button and check it appears.

If **Game PC pad** stays *not found yet*, press a button on the controller once in the game (the game only lists a button after its first press) and give it a few seconds. Hideway finds the game's key table by what is in it (an array of keys whose names it can read, such as *Gamepad Right Trigger* or *Left Mouse Button*), so it does not depend on the game version, and it learns which byte means *pressed* from the buttons you press while the CONTROLLER card is open: press a few buttons, one at a time, with the card visible.

If it still says *not found yet*, send the support the file **gameinput_debug.txt** (next to Hideway.exe, up to 6 reports per run) and **hideway.log**. The report lists every array of the game's input object that was examined, the raw bytes of its first keys, what was learned and why each candidate was accepted or refused.

**Another way, without any key:** set **Aim activation** to **Aiming down sights** (or **Key or aiming down sights**). The aim then follows what the game says: it is on while you aim down sights (LT on a controller) and off when you let go. The CONTROLLER card shows **Game says: aiming down sights / not aiming** live.

* The movement still goes out through your input device (Ferrum, MAKCU or KMBox NET), exactly as with a mouse.

