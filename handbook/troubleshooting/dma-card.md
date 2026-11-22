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

**Debug > PERFORMANCE**: *Tick* should be well below 10 ms and *Data age* below about 20 ms. High values point at the link: cable, USB port, other USB traffic. The fast paths (**Fast DMA reads** and the **High-rate camera lane**) are automatic and always on; they self-verify and fall back by themselves.

A black **Fuser** window on the same GPU as the game can compete for GPU time: run it on the overlay PC only.

### Hideway tells you when the link stalls

Since 3.7.5, **Config > ADVICE** shows **Card link stalls** when, during steady play, at least one ten-second window in five had a read tick of 100 ms or more (and at least three windows did). A healthy link stays under about 40 ms, so you should never see this line on a good setup. Ticks of 100 ms to a second right around a loading screen (lobby to match, match to lobby) are normal and are **not counted**: only windows that began at least 30 seconds after the last loading screen count, and the verdict needs at least two minutes of them. When it shows:

1. Plug the card's USB cable **straight into a USB 3 port on the motherboard**: no hub, no extension cable, no front-panel port.
2. Try another cable and another port; a cable that is a little too long or too thin is the usual cause.
3. Switch off USB power saving: Device Manager > *Universal Serial Bus controllers* > each *USB Root Hub* and the card's own entry (the FTDI one) > Properties > Power Management > untick *Allow the computer to turn off this device to save power*; Windows power plan > Change advanced power settings > USB settings > *USB selective suspend* > Disabled.
4. An overloaded or throttling **game PC** stalls the reads the same way: close other programs there and check its temperatures.

The same line is written to the log (`ADVICE: Card link stalls ...`), so a log tells at once whether the link was the problem.

## Freezes about every 10 seconds

MemProcFS refreshes its process list in the background and every read waits for it: a ~105 ms freeze every ~10 s on some setups. The **DMA stall guard** (automatic, always on) pauses that refresh.
