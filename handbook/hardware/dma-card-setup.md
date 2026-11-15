# Install the DMA card

Step by step, from the empty slot to a working link.

{% hint style="danger" %}
**Cold power rule.** Before you touch any card, cable or slot, shut the PC down, **switch the power supply off at the back**, then press the case power button once or twice to drain what is left in the capacitors. Plugging or unplugging PCIe parts on a live board can destroy them.
{% endhint %}

## Step 1: Fit the card

1. Power the game PC off completely (see the rule above) and open the case.
2. Pick a free PCIe slot. A slot cover blocks the bracket? Remove only the one you need.
3. Seat the card fully until it clicks. If the graphics card blocks the slot, use a PCIe extender.
4. If your card has a **power / kill switch**, set it to **on** (usually the position away from the motherboard). Check your card's manual: not every card has one.

## Step 2: BIOS settings

Power the PC back on and enter the BIOS (usually **Delete**, **F2** or **F10** right after power-on).

Your game PC stays clean: **nothing needs to be turned off**. Hideway's firmware supports IOMMU, so **VT-d** (Intel) and **IOMMU** (AMD) stay on, and so do Secure Boot and virtualization (SVM / VT-x). Leave every option as it is.

Save, exit and boot into Windows.

{% hint style="info" %}
The first boot after fitting a card can be slow. If it hangs, try turning off AMD EXPO / memory overclocking for the first start.
{% endhint %}

## Step 3: Check the card lights

With the PC on, the card should show its normal "powered" lights (a steady green and red pair on common cards). No light at all usually means the kill switch, the slot or the power-off rule above.

## Step 4: Windows on the game PC

Nothing to change here either. Leave **Core isolation / Memory integrity** and the virtualization features of Windows as they are.

## Step 4b: The overlay PC

* Hideway ships its own Visual C++ runtime in `core\`, so you do **not** install one separately. DirectX 11 is part of Windows 10 / 11.
* The card talks through an **FTDI FT601** USB 3 chip. Windows normally installs its driver by itself when the cable is connected; Hideway also ships the `FTD3XX.dll` it needs. If the card shows up with a warning icon in Device Manager, install the FTD3XX driver: [Download the FTD3XX driver](https://download.hideway.cc/drivers/FTD3XX-WinUSB-driver-1.4.0.6.zip) (FTDI WinUSB D3XX 1.4.0.6). Unzip it, open the `WU_FTD3XX_Driver` folder, right-click `FTD3XXWU.inf` and choose **Install**, then replug the card's USB cable.

## Step 5: Connect the card to the overlay PC

1. Use the card's **DATA** USB-C port. On cards with two ports the data port is usually the one **next to the status lights**; the other is the **JTAG / flashing** port. Check your manual.
2. Plug the other end into a **USB 3.x port directly on the motherboard** of the overlay PC (a blue port). No hub, no front-panel port.
3. Open **Device Manager** on the overlay PC. You should see the FTDI FT601 device without a warning icon. If not, power-cycle both PCs (cold) and look again.

## Step 6: Test the link

Run the **DMA speed test** you received with the card on the overlay PC and keep its whole folder together. A healthy link is above both of these:

| Measure | Healthy |
|---|---|
| Reads per second | about **4000 per second** or more |
| Throughput | about **125 MB/s** or more |

Below that the cause is almost always the **USB cable, USB port or card seating**; see [DMA troubleshooting](dma-troubleshooting.md#the-speed-test-fails-or-is-low).

## Step 7: Start Hideway

1. Start Fortnite on the game PC (the lobby is enough).
2. Start `HidewayLauncher.exe` on the overlay PC and sign in.
3. Open the Debug page and read [READY CHECK](../getting-started/ready-check.md). **DMA** should be green; **Game data** turns green once the game's structures are found.

Hideway retries the card every 2 seconds, so the order in which you plug things in does not matter.
