# DMA card

{% hint style="info" %}
Errors from the DMA runtime itself (VMM init failed, memory map, DTB, symbols, low speed) and building or flashing the card are in [DMA troubleshooting](../hardware/dma-troubleshooting.md) and [Install the DMA card](../hardware/dma-card-setup.md).
{% endhint %}

## `DMA OFFLINE` in the top bar

The card is not detected. Check, in this order:

1. **USB cable**: use a port **directly on the motherboard** (USB 3 preferred), not a hub or front-panel port.
2. **Game PC is powered** and the card is seated.
3. **Nothing else holds the card**: close MemProcFS, Fuser and any other tool that talks to it.
4. **Administrator**: accept the UAC prompt; the DMA transport needs it.
5. **Driver**: in Device Manager, check the FTDI device for a warning icon.
6. **Runtime files**: `vmm.dll`, `leechcore.dll`, `FTD3XX.dll` must be the shipped versions next to `Hideway.exe`. The launcher's **System** page checks them.

Hideway retries every **2 seconds**, so you can plug the card in after starting it.

## `WAITING FOR FORTNITE`

The card works but the game is not running on the game PC (or not yet in the lobby). Start Fortnite there.

## The card drops in the middle of a session

Hideway reconnects by itself when the cable drops. If it does not, use **Debug > DMA LINK > Disconnect DMA card**, then **Reconnect DMA card**, or restart Hideway.

{% hint style="warning" %}
Recovery after the card drops in the middle of a session has been tested only partially on hardware. If it happens, restart Hideway.
{% endhint %}

## `Game data` red

The card works and the game is found, but its structures were not located within 90 seconds. That is almost always a **Fortnite patch**: see [After a Fortnite update](../guides/after-a-fortnite-update.md).

## Slow reads, choppy data

**Debug > PERFORMANCE**: *Tick* should be well below 10 ms and *Data age* below about 20 ms. High values point at the link: cable, USB port, other USB traffic. Keep **Fast DMA reads** and **High-rate camera lane** on (default); they self-verify and fall back by themselves.

A black **Fuser** window on the same GPU as the game can compete for GPU time: run it on the overlay PC only.

## Freezes about every 10 seconds

MemProcFS refreshes its process list in the background and every read waits for it: a ~105 ms freeze every ~10 s on some setups. **DMA stall guard** (Misc > ENGINE, on by default) pauses that refresh.
