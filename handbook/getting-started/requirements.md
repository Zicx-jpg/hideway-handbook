# What you need

Hideway is built for a **two-PC DMA setup**. Read this page before anything else; most start-up problems are a missing piece here.

## The two PCs

```
   GAME PC                                   OVERLAY PC
 +----------------------+   USB cable    +----------------------------+
 | Fortnite             |<-------------->| Hideway (launcher + overlay)|
 | DMA card (PCIe)      |  (card to PC)  | draws ESP / radar           |
 +----------------------+                | input device (optional)     |
                                         +----------------------------+
                                                     |
                                              monitor / capture
```

| | Game PC | Overlay PC |
|---|---|---|
| Runs | Fortnite | Hideway |
| Needs | The DMA card installed in a PCIe slot | The card's USB cable plugged in, Windows 10 / 11 (64-bit), administrator rights |
| Hideway touches it | **Read-only** over the card. Nothing is installed or started on it | The overlay window and the input device live here |

{% hint style="info" %}
Hideway reads game memory through the card. It does not inject anything into the game or run code on the game PC.
{% endhint %}

## Checklist

* [ ] A **DMA card** in the game PC, with its USB cable to the overlay PC (use a USB port directly on the motherboard, preferably USB 3).
* [ ] **Windows 10 or 11, 64-bit** on the overlay PC. The publisher tested Windows 10 22H2; other versions are untested.
* [ ] **Administrator rights.** Windows asks once through the normal UAC prompt. The DMA transport needs them.
* [ ] A **license key** (or a KeyAuth account with an active subscription) from the publisher. Never post it anywhere.
* [ ] An **internet connection** for the license check and update check.
* [ ] A correct **system clock** on the overlay PC (within about 25 seconds). A wrong clock fails the signed license answer.
* [ ] Optional: an **input device** for aim and trigger: MAKCU, Ferrum or KMBox NET. See [Connect an input device](../guides/input-device.md).
* [ ] Optional: a phone or tablet on the same network for the [web radar](../guides/web-radar.md).

{% hint style="info" %}
Building the hardware from scratch? Step-by-step pages for the card, BIOS, input device and fuser are in [Hardware at a glance](../hardware/overview.md).
{% endhint %}

## No hardware yet?

You can explore everything with synthetic data. Start Hideway with `--demo` (see [Demo mode](demo-mode.md)). It needs no license, no card and no game.

## Fortnite build

Hideway reads the game with a table of structure offsets (the `all\` folder). Each Fortnite patch can move them. This release carries offsets for **Fortnite 43.00**. After a patch there can be a short period without ESP until a new dump is made; see [After a Fortnite update](../guides/after-a-fortnite-update.md).
