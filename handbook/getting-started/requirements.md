# Before you start

Hideway needs two PCs. Most first-day problems come from a missing piece on this list, so check it before you install anything.

## How the two PCs fit together

```
 GAME PC                                  OVERLAY PC
 Fortnite                  USB cable      Hideway (launcher + overlay)
 DMA card in a PCIe slot  ------------->  draws ESP and radar
                                          input device (optional)
```

The **game PC** runs Fortnite and holds the DMA card. The **overlay PC** runs Hideway, draws the overlay and drives the input device. Hideway only reads memory through the card. It does not put anything on the game PC.

## What you need

* A **DMA card** in the game PC, with its USB cable plugged into the overlay PC. Use a USB port on the motherboard itself, and USB 3 if you have it.
* **Windows 10 or 11, 64-bit** on the overlay PC. It was tested on Windows 10 22H2.
* **Administrator rights** on the overlay PC. Windows asks once; the card driver needs it.
* A **license key** from the seller. Keep it private.
* **Internet** on the overlay PC for the license and update checks.
* A **correct clock** on the overlay PC. If it is off by more than about 25 seconds, sign-in fails.

Optional:

* An **input device** (MAKCU, Ferrum or KMBox NET) if you want aim assist or the triggerbot. See [Connect an input device](../guides/input-device.md).
* A phone or tablet on your network for the [web radar](../guides/web-radar.md).

Building the hardware yourself? The step-by-step pages start at [Hardware at a glance](../hardware/overview.md).

## No hardware yet?

You can try the whole menu with generated players and no card, no game and no license. See [Demo mode](demo-mode.md).

## The Fortnite build

Hideway finds players through a table of memory offsets that belongs to one Fortnite build. This release is made for **43.10**. After a Fortnite patch the offsets can move and the ESP can stay empty until new data is out. The program checks for signed game data on its own, and [After a Fortnite update](../guides/after-a-fortnite-update.md) explains what you will see in the meantime.
