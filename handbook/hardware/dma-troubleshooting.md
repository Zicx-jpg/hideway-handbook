# DMA troubleshooting

Hardware and driver problems, grouped by what you see. The messages in this page come from the DMA runtime underneath Hideway (**MemProcFS / LeechCore**) and from the vendors' speed-test tools, so exact wording can differ a little. Hideway's own symptoms (`DMA OFFLINE`, `WAITING FOR FORTNITE`, `Game data`) are in [DMA card](../troubleshooting/dma-card.md).

Always change **one thing at a time** and retest.

## The card is not found (VMM init failed)

Try in this order, retesting after each one:

1. The USB cable is on the card's **DATA** port, not the JTAG port.
2. The overlay PC end is a **USB 3.x port directly on the motherboard**.
3. Another **USB data cable** (many cables are charge-only or too long).
4. The driver is correct (FTDI FT601 without a warning in Device Manager).
5. **Hard power cycle of the game PC:** shut down, switch the power supply off, unplug the power cable and the card's USB cable, hold the power button for 15 seconds, then plug back in and boot.
6. Move the card to the **main GPU slot** (the first x16) and re-check the [BIOS settings](dma-card-setup.md#step-2-bios-settings).
7. Still failing: ask your seller for a test firmware, to rule out the firmware.

## Failed to retrieve the physical memory map

* Check the USB connection as above.
* Remove **OneDrive** from the game PC (vendors report this clears it on some systems).
* Last resort: reinstall Windows on the game PC (vendors suggest Windows 11 23H2).

## Unable to locate a valid DTB / unable to identify the operating system

The runtime could not find Windows' page tables.

* Redo the [BIOS settings](dma-card-setup.md#step-2-bios-settings) on the game PC.
* Check the USB connection.
* Remove OneDrive.
* Last resort: reinstall Windows on the game PC.

## Offline symbols unavailable

The runtime could not download the Windows symbols it needs to read the system.

* Make sure the whole folder is extracted and that `symsrv.dll` and `dbghelp.dll` sit next to the program (Hideway ships both in `core\`).
* The overlay PC needs **internet**, and its firewall must not block the program.
* As a fallback you can place an `info.db` file from the MemProcFS releases next to the DLLs. It is an offline symbol dump.

## "TINY PCIe TLP algorithm auto-selected"

The card is running in a slow mode. This is nearly always a **bad USB connection** and rarely the firmware. Reseat both ends and try another USB port.

## The speed test fails or is low

A test failure usually means **too low a speed**: under about 4000 reads per second, or under about 125 MB/s.

* Use a real **USB 3** data cable, seated firmly at both ends. A bracket can stop the plug sitting fully.
* Try other ports and cables.
* On the overlay PC set the power plan to **High performance**.
* Re-seat the card.
* An overlay PC far below the recommended level can lower the speed.
* A custom firmware can lower speed on purpose; ask its vendor if that is normal.
* Close other tools that use the card. A speed slightly under the thresholds can still work.

Inside Hideway, the real numbers are on **Debug > PERFORMANCE**: see [Slow reads, choppy data](../troubleshooting/dma-card.md#slow-reads-choppy-data).

## Players missing or data freezing

When the game PC is short of memory, Windows moves some of it to the **page file** on the drive. The card can only read **RAM**, so those pages are invisible to it. The symptoms are players that disappear, data that stops updating or things that look random.

* The real fix is **more RAM** on the game PC.
* Disabling the page file avoids the symptom but can make Windows crash when memory runs out. It is **not recommended**.
* Close heavy background programs on the game PC.

## Quick map

| You see | Start with |
|---|---|
| `DMA OFFLINE` | USB cable, port, power cycle |
| VMM init failed | JTAG vs DATA port, driver, cable |
| Physical memory map | USB, OneDrive |
| DTB / unknown OS | BIOS (VT-d / IOMMU), USB |
| Symbols | `symsrv.dll`, `dbghelp.dll`, internet |
| Low speed | Cable, port, seating, power plan |
| Data comes and goes | RAM on the game PC |

Still stuck? Collect what support needs: [Collect diagnostics](../troubleshooting/collecting-diagnostics.md).
