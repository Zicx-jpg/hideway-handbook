# Frequently asked questions

Short answers with a link to the full page. If your question is not here, use the search box at the top of this handbook.

## The basics

{% hint style="info" %}
**What is Hideway?** A Fortnite overlay for DMA setups. It runs on a second PC, reads the game over a DMA card (read-only) and draws ESP, radar and optional aim assist on a transparent window. See the [overview](README.md).
{% endhint %}

<details>
<summary>Do I need two PCs?</summary>

Yes. The game PC runs Fortnite and holds the DMA card; the overlay PC runs Hideway. See [What you need](getting-started/requirements.md).

</details>

<details>
<summary>Can I try it without a DMA card?</summary>

Yes, in **demo mode**: `Hideway.exe --demo`. It shows synthetic players and needs no license, no card, no game. See [Demo mode](getting-started/demo-mode.md).

</details>

<details>
<summary>Which Windows versions work?</summary>

Windows 10 and 11, 64-bit. The publisher tested Windows 10 22H2; other versions are untested.

</details>

<details>
<summary>Which Fortnite build does this release support?</summary>

Offsets in this release are for **Fortnite 43.00**. After a patch there can be a gap until new offsets are released. See [After a Fortnite update](guides/after-a-fortnite-update.md).

</details>

<details>
<summary>Why does it need administrator rights?</summary>

The DMA transport needs them. Windows asks once through the normal UAC prompt. Hideway never turns off or changes Windows security settings.

</details>

<details>
<summary>Is it safe? Will I get banned?</summary>

**Nobody can promise that.** Hideway reads the game from outside the game PC and does not write to the game, but any tool used next to an online game can lead to action by the game's publisher. You use it at your own risk. Hideway's own safety work is about *your PC*: signed updates, checked files, no secrets in logs; see [Security and privacy](reference/security-and-privacy.md).

</details>

<details>
<summary>How do I build the hardware setup?</summary>

See [Hardware at a glance](hardware/overview.md): card, BIOS, cabling, speed test, input device and fuser, in order.

</details>

<details>
<summary>Do I need a fuser?</summary>

No. It is only for seeing the overlay on your main monitor. Without one, use a second monitor or the [web radar](guides/web-radar.md). See [Fuser](hardware/fuser.md).

</details>

<details>
<summary>Which input devices work?</summary>

MAKCU, Ferrum and KMBox NET. Other devices are not supported. See [Input devices](hardware/input-devices.md).

</details>

<details>
<summary>My DMA speed test is low.</summary>

Nearly always the USB cable, port or card seating. See [The speed test fails or is low](hardware/dma-troubleshooting.md#the-speed-test-fails-or-is-low).

</details>

## Getting started

<details>
<summary>Which program do I run?</summary>

Only `HidewayLauncher.exe` at the top of the folder. Everything else is inside `core\`. See [The launcher](getting-started/the-launcher.md).

</details>

<details>
<summary>I get a SmartScreen warning.</summary>

The programs are not Authenticode-signed yet, so Windows warns. Verify the download with `verify_package.ps1` first (see [Install](getting-started/install-and-first-start.md)), then choose "Run anyway". Do not turn off Windows protections.

</details>

<details>
<summary>How do I sign in?</summary>

With your **license key**, or with the website's **Web Loader** button (the app must already be open on its sign-in screen). "Remember on this device" stores the key encrypted for your Windows account only. See [Install and first start](getting-started/install-and-first-start.md#5.-sign-in).

</details>

<details>
<summary>What do the READY CHECK colours mean?</summary>

Green = good, orange = waiting for something normal (lobby, loading), red = fix this. The **Next:** line names the first thing to fix. See [READY CHECK](getting-started/ready-check.md).

</details>

<details>
<summary>Where is the Debug page?</summary>

Hidden by default. **Misc > Debug > Show debug page**.

</details>

<details>
<summary>What do Insert and End do?</summary>

**Insert** opens or closes the menu. **End** exits Hideway. Both can be rebound (Misc > KEYS). See [Hotkeys](guides/hotkeys.md).

</details>

## The menu and configs

<details>
<summary>Where did the Simple and Advanced modes go?</summary>

They were removed in the latest update. The menu is now **all-in-one**: every option is on its page and there is no Mode button to press. Use the search box to jump to any option. See [Menu overview](the-menu/overview.md).

</details>

<details>
<summary>Where are my configs saved?</summary>

In `%APPDATA%\Hideway\Fortnite\configs`. A new Hideway folder, a reinstall or an update keeps them. See [Configs](guides/configs.md).

</details>

<details>
<summary>Do I need to press Save?</summary>

No. **Auto-save config** (on by default) writes your changes 2.5 seconds after the last one and when the program closes, keeping a backup of the old file.

</details>

<details>
<summary>I deleted a config by accident.</summary>

Deleted configs go to a trash folder (`configs\_trash`) and can be restored. Config backups are in `configs\_backups` (Config > BACKUPS).

</details>

<details>
<summary>Can I share a config with a friend?</summary>

Yes: **Config > SHARE > Copy config**. Machine-specific settings (input device, ports, web radar, audio device) are never exported and never applied from shared text, so a shared config cannot point your device somewhere else or open a port.

</details>

## ESP

<details>
<summary>Why do I see no ESP in the lobby?</summary>

There is nobody to draw. Players appear once a match has started. See [No ESP](troubleshooting/no-esp.md).

</details>

<details>
<summary>The boxes are a bit behind or ahead of the players.</summary>

Adjust **ESP time offset** (Misc) a few milliseconds: raise it if boxes trail, lower it if they lead.

</details>

<details>
<summary>What is the number before the name?</summary>

The **Team ID**: the game's own team number. Everyone in the same duo / trio / squad carries the same one. See [Visuals](the-menu/visuals.md#team-id).

</details>

<details>
<summary>Why is there no health bar on enemies?</summary>

The game does not appear to send enemy health, only your own and your squad's. Hideway shows no bar instead of an invented one. See [Health and shield bars](troubleshooting/health-and-data.md).

</details>

<details>
<summary>The skeletons look frozen.</summary>

The game does not animate hidden or far players much, and in crowded matches distant players are read less often. See [ESP quality](troubleshooting/esp-quality.md#skeletons-look-static).

</details>

<details>
<summary>Can it show loot?</summary>

Yes: **Visuals > LOOT ESP**. It needs the wall check on and draws items only after proving the game's layout. See [Loot, containers and reboot cards](guides/loot-and-world.md).

</details>

<details>
<summary>What is the squad list?</summary>

A panel at the top right with every other squad in range: team number, members alive (and down), distance of the nearest one.

</details>

## Aim and trigger

<details>
<summary>Do aim and trigger work without extra hardware?</summary>

No. They move the mouse through an **input device** (MAKCU, Ferrum or KMBox NET). Without one, only ESP, radar and the HUD work. See [Connect an input device](guides/input-device.md).

</details>

<details>
<summary>My aim key is Mouse 1. Why did it lock on while I placed a wall?</summary>

That was a bug, fixed in **2.10.2**: with **Only with a gun in hand** on (default), aim and trigger stay off while you hold a build piece, the pickaxe or an empty weapon. See [Aim or trigger problems](troubleshooting/aim-and-trigger.md#aim-locks-on-while-i-place-a-wall).

</details>

<details>
<summary>Why can the aim still lock onto someone behind a wall?</summary>

The wall check knows the level's static geometry, **not walls that players build**. Also check **Visible only** and the **Visibility check** style. See [Visibility](guides/visibility.md).

</details>

<details>
<summary>How do I tune the sensitivity?</summary>

**Aimbot > CALIBRATION > Counts per degree X / Y**, with **Test move (+/-60)** (Misc). See [Tune aim and trigger](guides/aim-and-trigger.md).

</details>

<details>
<summary>How do I know how long my input delay is?</summary>

**Debug > LATENCY > Measure latency**. It measures the mouse-to-camera delay and offers it as **Prediction lead** / **Trigger lead**.

</details>

<details>
<summary>Does Hideway click for me?</summary>

Only the **triggerbot**, and only when it is enabled, armed, a valid target is under the crosshair and the menu is closed. It never fires while the menu is open or panic is active.

</details>

## Web radar

<details>
<summary>What is the web radar?</summary>

Your radar in a browser (phone, tablet, second monitor), served by Hideway itself. Nothing goes to the internet. See [Web radar](guides/web-radar.md).

</details>

<details>
<summary>My phone cannot open it.</summary>

Same network, **Allow other devices (LAN)** on, Windows Firewall allowing Hideway on private networks, and the right **port**. See [Phone cannot connect](guides/web-radar.md#phone-cannot-connect).

</details>

<details>
<summary>Is the radar link private?</summary>

It contains an **access key**. Do not post it. **New access key** invalidates old links.

</details>

## Updates and security

<details>
<summary>How do updates work?</summary>

Signed releases, downloaded in the background, installed only when you click, rolled back automatically if the new version does not start. See [Updates](guides/updates.md).

</details>

<details>
<summary>Will an update delete my configs?</summary>

No. Configs live in your user profile and are never overwritten.

</details>

<details>
<summary>What does Hideway send over the internet?</summary>

Your license key to the license service (KeyAuth) and a hardware identifier it uses to lock a license to one PC (your Windows account SID), plus the update check to the release host. Nothing else is uploaded. Settings stay on your PC. See [Security and privacy](reference/security-and-privacy.md).

</details>

<details>
<summary>Is my license key in the log?</summary>

No. `hideway.log` never contains keys or tokens, and neither does Copy diagnostics.

</details>

## Problems

<details>
<summary>Fortnite closed after a match. Was it Hideway?</summary>

In the logs reviewed, Hideway recorded no crash and the **game process ended** a few seconds after a match ended. See [The game closes or crashes](troubleshooting/game-closes-or-crashes.md) for how to tell and what to send.

</details>

<details>
<summary>The launcher says "not the signed one".</summary>

A file in `core\` was changed or is missing. Use **Restore the files**, or download the package again and verify it. See [Launcher and updates](troubleshooting/launcher-and-updates.md).

</details>

<details>
<summary>"Cannot reach license server".</summary>

The app keeps working for up to 15 minutes offline, then locks. Check your internet and your system clock. See [Start-up and license](troubleshooting/startup-and-license.md).

</details>

<details>
<summary>DMA OFFLINE.</summary>

Use a motherboard USB port, power the game PC, close other tools that use the card, accept the UAC prompt. See [DMA card](troubleshooting/dma-card.md).

</details>

<details>
<summary>The overlay is black.</summary>

Turn off **Visuals > HUD > Fuser mode** unless you use a capture card.

</details>

<details>
<summary>What should I send support?</summary>

The version, **Copy diagnostics**, `hideway.log` **and** `hideway.log.1`, and what you were doing. See [Collect diagnostics](troubleshooting/collecting-diagnostics.md).

</details>
