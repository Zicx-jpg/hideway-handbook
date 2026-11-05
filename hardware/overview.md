# Hardware at a glance

This section is the **hardware side** of the handbook: the DMA card, the input device, the fuser and the two PCs. Read it if you are building a setup from scratch or something below the software is not working.

{% hint style="warning" %}
**Where this section comes from.** It is rewritten for Hideway from public setup guides of DMA hardware vendors. The publisher has not re-tested every step on every card, input device or fuser model. When your own hardware manual disagrees with a page here, **follow the manual**. Anything that is only a vendor recommendation is marked as such.
{% endhint %}

## What DMA is, in two minutes

**Direct Memory Access (DMA)** is a normal PCIe feature: a device on the bus can read and write the PC's memory without going through the CPU. A DMA card turns that feature into a link to **another computer**: the second PC asks the card for memory, and the card fetches it from the game PC.

For Hideway that means:

* **Fortnite runs on the game PC.** Nothing of Hideway is installed or started there.
* **Hideway runs on the overlay PC** and reads the game through the card. It only **reads**; it does not write to game memory.
* The overlay PC draws the ESP, radar and menu, and (optionally) drives an input device.

{% hint style="danger" %}
Using any tool next to an online game can break the game's rules and lead to a ban or other action by the publisher. **Nobody can promise you will not be banned.** You use Hideway at your own risk. See [Security and privacy](../reference/security-and-privacy.md).
{% endhint %}

## What you need

| Part | Where | Notes |
|---|---|---|
| **DMA card** | Game PC (PCIe) | Cards with an FPGA such as 35T / 75T are the usual kind. Follow your seller's manual |
| **USB data cable** | Card to overlay PC | A real **USB 3** data cable (not charge-only), into a port **directly on the motherboard** |
| **Overlay PC** | Next to your monitor | Windows 10 / 11 64-bit. It also needs a GPU able to output the same resolution as your game PC |
| **Input device** (optional) | Between mouse and PCs | MAKCU, Ferrum or KMBox NET. See [Input devices](input-devices.md) |
| **Fuser** (optional) | Between both PCs and the monitor | Merges the two video signals. See [Fuser](fuser.md) |

### Game PC: desktop

* A free PCIe slot (x1, x4 or x16). If the graphics card blocks the slots, a **PCIe extender** (riser) solves it.
* Enough performance and **enough RAM** to run the game with headroom. Memory that Windows pushes into the page file cannot be read by the card; see [Missing or frozen data](dma-troubleshooting.md#players-missing-or-data-freezing).

### Game PC: laptop

A laptop needs a way to reach PCIe. Typical routes are a free **M.2 slot** with an M.2-to-PCIe adapter, a spare M.2 slot for an M.2 version of the card, or a **Thunderbolt 3** port with a Thunderbolt-to-PCIe enclosure. Adapters can need **external power** for the card.

### Overlay PC

Hideway has **no measured minimum spec**. The vendor guides recommend roughly an Intel i5 4th generation as a floor and an i5 9th generation / Ryzen 5 5600G as a comfortable level, with an integrated or dedicated GPU. Judge your own PC with **Debug > PERFORMANCE** (*Tick* well below 10 ms, *Data age* below about 20 ms; see [DMA card](../troubleshooting/dma-card.md#slow-reads-choppy-data)).

## Does your motherboard allow it?

1. On the game PC press **Win + R**, type `msinfo32` and press Enter.
2. Look for **Kernel DMA Protection** in the system summary.
3. If it says **Off**, nothing blocks the card at the Windows level.
4. If it says **On**, the platform restricts what devices may read. DMA guides ask you to switch the matching option off in the BIOS (called **VT-d** on Intel and **IOMMU** on AMD). Some boards do not offer that switch; on those the card may not work. See [Install the DMA card](dma-card-setup.md#step-2-bios-settings).

## The order to build it

1. [Install the DMA card](dma-card-setup.md): card, BIOS, cables, speed test.
2. [Flash the card firmware](firmware-flashing.md) (only if your card needs it).
3. [Input devices](input-devices.md) (only for aim and trigger).
4. [Fuser](fuser.md) (only if you use one).
5. [Windows tuning](pc-tuning.md).
6. Start Hideway and follow [READY CHECK](../getting-started/ready-check.md).

When something fails, go to [DMA troubleshooting](dma-troubleshooting.md).
