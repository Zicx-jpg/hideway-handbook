# Input devices

An **input device** is a small hardware box that sits between your mouse and your PCs. Hideway tells it to move or click, and the game PC only ever sees normal mouse input. It is needed **only for aim and trigger**; ESP, radar and the HUD work without one.

This page covers the hardware. The software side (the Misc page, auto-detect, test move) is in [Connect an input device](../guides/input-device.md).

## What Hideway supports

| Device | Link | Notes |
|---|---|---|
| **MAKCU** | USB serial (CH343 chip) | The most common choice. Passes your real mouse through |
| **Ferrum** | USB serial | Follows the vendor's documented commands; the least proven of the three here |
| **KMBox NET** | Network (UDP) | IP, port and UUID shown on the device |

Other devices that exist on the market (Arduino-based boxes, older KMBox models, legacy kits) are **not supported by Hideway**.

## Pass-through

With **pass-through** the device forwards your real mouse to the game PC and only adds its own movement on top. The mouse keeps working normally, and vendors say mouse software such as Logitech G Hub or Razer Synapse keeps recognising the mouse so DPI and profiles still work. Without pass-through the device is a separate virtual mouse.

## MAKCU: wiring

```
                 +--------------------+
   Game PC  <----| LEFT   MIDDLE RIGHT|
                 |   |      |      |  |
                 +---|------|------|--+
                     |      |      |
                 game PC  overlay  your
                 (USB)     PC      mouse
```

| Cable | Goes to |
|---|---|
| **Left** | The **game PC** (the device presents itself there as a mouse) |
| **Middle** | The **overlay PC** (Hideway talks to it here, as a COM port) |
| **Right** | Your **real mouse** |

Labels can differ between revisions: check the silk-screen on your board and the seller's manual.

## MAKCU: driver

On the overlay PC the MAKCU appears as a **serial (COM) port** and needs the WCH **CH343** driver. If Windows shows a problem code (28 means no driver), install the driver; Hideway can open the WCH download page for you and checks the installer's publisher before offering to run it. See [Missing driver](../guides/input-device.md#missing-driver-makcu).

Some tools want a low COM number. In Device Manager > Ports (COM & LPT) > your port > Port Settings > Advanced you can set the number below 10. Hideway does not need this: it finds the device again even if Windows gives it a new number.

## MAKCU: firmware

Flash only if your seller says so, and do it from the **overlay PC** (the flashing tool unpacks temporary files where it runs).

1. Download the seller's flashing tool and let it update itself.
2. Hold the **LEFT** button on the board, then plug the USB cable into the **LEFT** port. The tool should say it sees the MCU **in flash mode**.
3. Press **Flash Left**, wait for it to finish, then unplug.
4. Repeat with the **RIGHT** button and **RIGHT** port, **Flash Right**.
5. Reconnect the three cables as in the wiring above, restart the tool and run its **TEST**: the cursor on the game PC should move.

## Check it in Hideway

**Misc > INPUT DEVICE > Enable input device > Connect > Test move (+/-60)**. The top bar shows the real device state. If it does not connect, see [Not working?](../guides/input-device.md#not-working).

## Controller players: XIM Matrix with MAKCU

If you play with a gamepad and want the game to see mouse input, a **XIM Matrix** can translate a controller into mouse and keyboard, and the MAKCU is wired behind it. The general flow, from the vendors' guides:

1. Pair the controller with the XIM Matrix (wired to its controller port, or wirelessly). Xbox pads: hold the sync button until the guide button flashes fast. PlayStation pads: hold **Share** then **PS** until the light flashes quickly.
2. On the game PC install the XIM manager software, connect the XIM Matrix and create a new config: pick the game and PC, input **Gamepad**, output **Mouse and keyboard**.
3. Connect the MAKCU as in the wiring above, with the XIM Matrix on the cable your seller's diagram shows.
4. In the game set the input to mouse and keyboard.

Follow the wiring picture from the XIM Matrix and MAKCU vendors for your exact revision; the Hideway side stays the same (Misc > INPUT DEVICE).

## Safety behaviour

A held button is released on disconnect, link loss, shutdown and if Hideway crashes. The trigger never fires while the menu is open or panic is active.
