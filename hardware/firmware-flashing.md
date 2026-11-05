# Flash the card firmware

Most cards arrive ready. You flash only when your seller tells you to: a new firmware, a fix, or a card that comes blank. This page describes the general procedure for the common **Xilinx 35T / 75T cards flashed through a CH347 USB-JTAG adapter**.

{% hint style="warning" %}
**Hideway does not ship firmware and does not flash anything.** Get the flashing tool, the driver and the firmware file from **your card's seller** and check each file against what they publish. Do not run files from random links. A wrong firmware or an interrupted flash can leave the card unusable.
{% endhint %}

{% hint style="info" %}
Flash from the **overlay PC**, never from the game PC.
{% endhint %}

## Before you start

* Power both PCs off **completely** before you move any cable. Power supply switch off, then press the case power button a few times to drain the board.
* **Never plug or unplug the JTAG cable while the card or PC is powered.** That is how cards and firmware get damaged.
* Know your chip: **35T** or **75T**. The card or its sticker says so. Picking the wrong one is the most common mistake.
* Put the tool and firmware in a short folder **without spaces** (for example `C:\flash\`).

## Steps

{% stepper %}
{% step %}
### Use the JTAG port

Connect the cable to the card's **JTAG** port. On the common layout this is the USB-C port **closest to the motherboard**; the data port is the one by the status lights. Check your manual.
{% endstep %}

{% step %}
### Install the JTAG driver

On the overlay PC run the setup of the CH34x / CH347 driver **as administrator** and click Install. In Device Manager the adapter should appear without a warning icon.
{% endstep %}

{% step %}
### Start the flashing tool

Run the vendor's FPGA download tool as administrator.
{% endstep %}

{% step %}
### Pick the chip and the file

Set the chip dropdowns to match your card (`xc7a35t` for a 35T, `xc7a75t` for a 75T), then select the firmware file. The path must contain **no spaces**.
{% endstep %}

{% step %}
### Flash and wait

Click the download button. **Do not disconnect or power off**, even when the bar reaches 100 %. Wait for the tool's final message (the CH347 tools print `Info: Close the CH347`).
{% endstep %}

{% step %}
### Power-cycle and switch to data

Shut both PCs down, switch the power supply off, press the power button a few times, then move the cable from **JTAG** to **DATA**. Power the game PC first, then the overlay PC.
{% endstep %}
{% endstepper %}

## If flashing fails

| Message or symptom | Try |
|---|---|
| `jtagspi_init_chain_id proxy_bit` or a similar init error | Rename the firmware to `firmware.bin` and move it and the tool folder to the root of `C:` (for example `C:\flash\`), then retry |
| Tool does not see the adapter | Reinstall the driver as administrator, try another USB port and cable |
| Flash completes but the card is not detected afterwards | Cable still on JTAG instead of DATA; do the cold power cycle again |
| Still failing | Ask the seller for a known-good test firmware to rule out the file |

After flashing, run the [speed test](dma-card-setup.md#step-6-test-the-link) and then check [READY CHECK](../getting-started/ready-check.md).
