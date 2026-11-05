# Fuser

A **fuser** is a small box that takes two video signals, the **game picture** from the game PC and the **overlay picture** from the overlay PC, and combines them into one output for your monitor. You see the ESP on top of the game without a second screen and without an overlay window running on the game PC.

You do **not** need one: Hideway also works on a second monitor or a phone through the [web radar](../guides/web-radar.md). A fuser is for people who want everything on one screen.

## How the picture is fused

The fuser treats **pure black** in the overlay picture as transparent and shows everything else on top of the game. That is why Hideway has a **Fuser mode**: it makes the overlay window a pure black background so only the drawings survive.

* Turn it on at **Visuals > HUD > Fuser mode**. Leave it **off** if you do not use a fuser, otherwise the overlay looks black.
* The overlay window must cover the whole screen of the output the fuser reads. Choose it at **Misc > Overlay monitor**.
* The overlay PC's GPU must be able to output the **same resolution** as the game PC.

## Connection

```
 Game PC GPU ------- Input 1 --+
                               |  FUSER  --- Output --- Monitor
 Overlay PC GPU ---- Input 2 --+
                               |
                      12 V power
```

Do the cabling with everything **powered off**:

1. Unplug every display from the game PC except your main monitor, and unplug the main monitor from the game PC's GPU.
2. **Output** goes to the **main monitor**. Only the fuser is connected to it.
3. **Input 1** to the **game PC's GPU**.
4. **Input 2** to the **overlay PC's GPU**.
5. Plug in the fuser's power supply, then power on the fuser, then both PCs.

{% hint style="warning" %}
Use certified **HDMI 2.1** or **DisplayPort 1.4** cables. Weaker cables (HDMI 2.0 / DP 1.2) cause no signal, flicker or a refresh rate stuck at 60 or 90 Hz.
{% endhint %}

## Windows settings on the overlay PC

1. While each PC is still connected directly to the monitor, right-click the desktop > **Display settings** > **Multiple displays** > **Extend these displays**.
2. On the **overlay PC** set the desktop background to **Solid colour: black** (Settings > Personalization > Background).
3. Reconnect everything through the fuser as in the diagram.

## Buttons

Button functions differ by model, so use your model's manual. Two common layouts:

| Button | Dichen-style (5th / 6th generation) | BAAN-style |
|---|---|---|
| **K1** | Cycles the output resolution; hold 3 s to show the resolutions and refresh rates of both inputs | Show only the **overlay PC** screen |
| **K2** | Adjusts the strength of the overlay layer (levels 0 to 20) | Show only the **game PC** screen |
| **K3** | Resets the strength to default | Turns the overlay on; further presses adjust its strength |
| **K4** | Turns fusion on / off | Switches the monitor encoding format (older monitors) |

## Troubleshooting

| Symptom | Try |
|---|---|
| Fusion light on but no overlay | Make the overlay PC background **pure black**, turn on **Fuser mode** in Hideway, raise the overlay strength |
| Both desktops merged, two taskbars | Switch the fuser to the main-screen-only mode when no overlay is running |
| "No signal" on a second monitor | A second monitor belongs on its own PC, not on the fuser. Turn it on |
| Refresh rate stuck at 60 / 90 Hz | Replace cables with certified HDMI 2.1 / DP 1.4 |
| Overlay is black | Turn **Fuser mode** off if you are not using a fuser |
| Choppy picture | A black fuser window on the same GPU as the game competes for GPU time: run it on the overlay PC only |

{% hint style="info" %}
Some vendors ship fusers that handle monitor identification (EDID) themselves. How a particular fuser does that is a matter between you and its manual and is not covered by Hideway.
{% endhint %}
