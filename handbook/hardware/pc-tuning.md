# Windows tuning

Hideway is light, but a busy overlay PC can still cost you smoothness, and a game PC under memory pressure hurts the DMA reads. These are safe, ordinary settings. None of them is required.

## Overlay PC

| Do | Why |
|---|---|
| Power plan **High performance** (Control Panel > Power Options) | Keeps CPU and USB at full speed; helps the DMA link |
| Plug the card on a **motherboard USB 3 port**, no hub | The link speed is the first limit |
| Close browsers, launchers and updaters | Fewer interruptions of the player lane |
| Keep Windows updates from running mid-session (set active hours) | A background update can stall the machine |
| Keep the **system clock** correct | A wrong clock fails the signed license answer |
| Do not run a second DMA tool at the same time | Only one program can hold the card |

Check the effect on **Debug > PERFORMANCE**: *Tick* should stay well below 10 ms and *Data age* below about 20 ms.

## Game PC

| Do | Why |
|---|---|
| Enough **RAM** | Pages pushed to the page file cannot be read by the card |
| Close heavy background programs | Less memory pressure |
| Keep the BIOS settings from [Install the DMA card](dma-card-setup.md#step-2-bios-settings) | Wrong ones stop the card from initialising |

## About stripped-down Windows builds

Custom, trimmed Windows builds exist to save CPU, but Hideway has **not been tested** on them. Our own tests ran on Windows 10 22H2. A trimmed build can remove services or components other tools rely on, and its source and updates are your responsibility. If you try one, do it on the overlay PC first and keep a restore point. If something stops working, test again on a normal Windows before reporting a problem.
