# Flash the card firmware

Everything here is done with **Hideway Tool** on the **overlay (second) PC**. Hideway Tool reads your card's DNA, flashes the firmware and runs the speed test in one window. The same five steps are on the site: [hideway.cc/guide.html](https://hideway.cc/guide.html). **Hideway Tool is sent to you in a ticket** on our Discord: it is not a public download.

Hideway's **Basic** and **Advanced** firmware packages are built for **your card's DNA** and delivered by the team in a ticket on our Discord, either as a **firmware file** (`.bin`) or as a **cloud key**.

{% hint style="warning" %}
Use only Hideway Tool and the firmware file or cloud key the team gives you in your ticket. A wrong firmware or an interrupted flash can leave the card unusable. If you are not sure, open a ticket **before** you flash.
{% endhint %}

{% hint style="info" %}
Your game PC stays clean: nothing in its BIOS or Windows needs to be turned off for flashing.
{% endhint %}

## What you need

| | |
|---|---|
| Card | 35T, 75T or 100T. Hideway Tool detects the model by itself. |
| JTAG cable | **CH347** or **RS232** (FT2232-based). 100T cards and cloud keys need **CH347**. |
| JTAG driver | CH347: run `CH341PAR\SETUP.EXE` from the Hideway Tool package. RS232: open **Zadig** → *Options* → *List All Devices* → pick **Quad RS232-HS (Interface 0)** or **Single RS232-HS** → *Replace / Install driver*. |

**Never plug or unplug the JTAG cable while the game PC is on.** Connect it with the PC fully off, then power on: the card needs power to be read and flashed.

## Step 1: Read the DNA

The DNA is the card's unique ID. Firmware is built for it, so the team needs it first.

{% stepper %}
{% step %}
### Connect JTAG

With the game PC off, connect the JTAG cable from the overlay PC to the card's **JTAG** port (Hideway Tool shows the wiring under *JTAG wiring guide*). Power the game PC on.
{% endstep %}

{% step %}
### Read

In Hideway Tool open **Firmware & DNA**, choose **CH347** or **RS232**, then **Read DNA**. The tool auto-detects the FPGA model and prints a line like `DNA = ... (0x0123abcdef456789)`.
{% endstep %}

{% step %}
### Send it

Click **Copy DNA** and paste it in your ticket. The team sends back your firmware file or cloud key.
{% endstep %}
{% endstepper %}

## Step 2a: Flash a firmware file

{% stepper %}
{% step %}
### Choose the file

In **Firmware & DNA**, keep the source on the local file and select the `.bin` you received. Check that the detected model matches your card.
{% endstep %}

{% step %}
### Flash

Click **Start flashing**. The tool writes the firmware, then reads it back to verify. **Do not unplug anything or turn the game PC off** until it reports that flashing and verification completed.
{% endstep %}

{% step %}
### Cold boot

Shut the game PC down, switch the power supply off for about 10 seconds, then power on. A simple restart does not reload the card.
{% endstep %}
{% endstepper %}

## Step 2b: Install with a cloud key

If you received a **cloud key** instead of a file:

1. Use a **CH347** cable (cloud install needs the CH347 read-back).
2. In **Firmware & DNA**, switch the source to **Cloud firmware** and enter the key.
3. The tool reads your card, gets the firmware made for it, flashes and verifies it.
4. Cold boot the game PC.

A cloud key is tied to your card. Keep it private: never post it in a Discord channel, only in your ticket.

## After flashing

Run the **Speed Test** in Hideway Tool (see [Install the DMA card](dma-card-setup.md#step-6-test-the-link)), then check [READY CHECK](../getting-started/ready-check.md).

## If something fails

| Message or symptom | Try |
|---|---|
| `DNA was not found` / `JTAG did not initialize` | Cable is on DATA instead of JTAG, the game PC is off, or the cable's driver is missing. Fix, then read again. |
| Tool does not see the adapter | Reinstall the CH347 driver (or redo Zadig for RS232), try another USB port and cable |
| `Cloud installation requires CH347 readback` | You are on an RS232 cable. Use a CH347 cable for cloud keys. |
| `Cloud request failed` | Copy the *Cloud diagnostic* text the tool shows and send it in your ticket |
| Flash completes but the card is not detected afterwards | Do the cold boot again and make sure the overlay PC is on the **DATA** port for normal use |
| Still failing | Open a ticket: we send a known-good test firmware to rule out the file |
