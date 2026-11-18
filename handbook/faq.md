# Questions people ask

Short answers, with a link when there is more to read. If yours is not here, use the search box at the top.

## Before you buy or install

**Do I need two PCs?**
Yes. One runs Fortnite and holds the DMA card, the other runs Hideway. See [Before you start](getting-started/requirements.md).

**Can I try it without a card?**
Yes, in demo mode: `Hideway.exe --demo`. It uses generated players and needs no license, card or game. See [Demo mode](getting-started/demo-mode.md).

**Which Windows and which Fortnite build?**
Windows 10 or 11, 64-bit, tested on Windows 10 22H2. This release carries the data for Fortnite 43.10. After a patch there can be a gap until new data is out, see [After a Fortnite update](guides/after-a-fortnite-update.md).

**Why does it need administrator rights?**
The DMA driver does. Windows asks once. Hideway does not change any Windows security setting.

**Will I get banned?**
Nobody can promise you won't. Hideway reads the game from outside the game PC and does not write to it, but any tool used next to an online game can lead to action from the publisher. It is your call. What Hideway does protect is your PC: signed updates, checked files, no secrets in logs. See [Security and privacy](reference/security-and-privacy.md).

**Which input devices work?**
MAKCU, Ferrum and KMBox NET. See [Input devices](hardware/input-devices.md).

**Do I need a fuser?**
No. It only lets you see the overlay on your main monitor. Without one, use a second monitor or the [web radar](guides/web-radar.md). See [Fuser](hardware/fuser.md).

## Getting started

**Which program do I run?**
Only `HidewayLauncher.exe`. Everything else is in `core\`. See [The launcher](getting-started/the-launcher.md).

**Windows shows a SmartScreen warning.**
The programs are not code-signed yet, so Windows warns the first time. Choose **More info > Run anyway** and leave Windows protection on.

**How do I sign in?**
Create an account once (username, password and your license key), then sign in with the username and password. You can also still use just the license key, or the Web Loader button on the customer panel while the sign-in screen is open. "Keep me signed in" stores the account encrypted for your Windows account.

**Where is the Debug page?**
Hidden until you turn on **Misc > Debug > Show debug page**.

**What do the READY CHECK colours mean?**
Green is fine, orange is waiting for something normal (lobby, loading), red needs fixing. The **Next:** line names the first thing to do. See [Is everything connected?](getting-started/ready-check.md).

**What do Insert and End do?**
Insert opens and closes the menu, End closes Hideway. You can change both under Misc > Keys. See [Hotkeys](guides/hotkeys.md).

## Menu and configs

**Where are my configs?**
In `%APPDATA%\Hideway\Fortnite\configs`. A new folder, a reinstall or an update keeps them. See [Configs](guides/configs.md).

**Do I have to press Save?**
No. **Auto-save config** (on by default) writes your changes 2.5 seconds after the last one and when you close the program, and it keeps a backup of the old file.

**I deleted a config by mistake.**
It went to `configs\_trash` and can be restored. Backups are in `configs\_backups` (Config > Backups).

**Can I share a config?**
Yes: **Config > Share > Copy config**. Settings that belong to your machine (input device, ports, web radar, audio device) are never exported and never applied from shared text.

## ESP

**There is no ESP in the lobby.**
There is nobody to draw. Players appear when the match starts. See [No ESP](troubleshooting/no-esp.md).

**The boxes are a bit behind or ahead.**
Change **ESP time offset** (Misc) by a few milliseconds: up if they trail, down if they lead.

**What is the number before the name?**
The Team ID, the game's own team number. Everyone in the same duo, trio or squad has the same one. See [Visuals](the-menu/visuals.md#team-id).

**Why do bots have a small BOT tag?**
Bots use the same colours as everyone else, pink when hidden and green when visible, so you can read visibility on them. The tag is what tells them apart.

**Why is there no health bar on enemies?**
Fortnite only sends health for you and your squad. When there is no value Hideway draws no bar. See [Health and shield bars](troubleshooting/health-and-data.md).

**The skeletons look frozen.**
The game barely animates players it does not draw, and in crowded matches far players are read less often. See [ESP looks wrong](troubleshooting/esp-quality.md#skeletons-look-frozen).

**Can it show loot?**
Yes, under **Visuals > Loot ESP**. See [Loot, containers and reboot cards](guides/loot-and-world.md).

## Aim and trigger

**Do aim and trigger work without extra hardware?**
No. They move the mouse through an input device. Without one you still get ESP, radar and the HUD. See [Connect an input device](guides/input-device.md).

**Why did the aim lock on while I placed a wall?**
Aim and trigger now stay off while you hold something without ammo (**Only with a gun in hand**, on by default). See [Aim or trigger problems](troubleshooting/aim-and-trigger.md#aim-locks-on-while-i-place-a-wall).

**The aim locks onto someone behind a wall.**
The wall check knows the level's fixed geometry, not walls that players build. Also check **Visible only** and the **Visibility check** style, see [Visibility](guides/visibility.md).

**The aim overshoots or falls short.**
Adjust **Counts per degree X / Y** (Aimbot > Calibration) and test with **Test move (+/-60)** on Misc. See [Tune aim and trigger](guides/aim-and-trigger.md).

**The aim feels slower than before.**
In 3.2.5 the smoothing value means what it says: each step adds about 8 ms to the time the aim needs to get on target, and the aim no longer overshoots and swings back. Lower **Smoothing** if you want it quicker.

**How do I find my input delay?**
**Debug > Latency > Measure latency**, standing still in a match with your hands off the mouse. It also offers the result as Prediction lead and Trigger lead.

**Does Hideway click for me?**
Only the triggerbot, and only when it is on, armed, a valid target is under the crosshair and the menu is closed.

## Web radar

**What is it?**
Your radar in a browser (phone, tablet, second monitor), served by Hideway itself. Nothing goes to the internet. See [Web radar](guides/web-radar.md).

**My phone cannot open it.**
Same network, **Allow other devices (LAN)** on, Windows Firewall allowing Hideway on private networks, and the right port. See [Phone cannot connect](guides/web-radar.md#phone-cannot-connect).

**Is the link private?**
It contains an access key. Do not post it. **New access key** cancels old links.

## Updates and privacy

**How do updates work?**
Signed releases download in the background and install only when you click. If the new version does not start, the old one comes back. See [Updates](guides/updates.md). Configs are never touched.

**What does Hideway send over the internet?**
Your license key and a hardware identifier (your Windows account SID) to the license service, which locks a license to one PC, and the update check to the release host. Nothing else. Settings stay on your PC. See [Security and privacy](reference/security-and-privacy.md).

**Is my license key in the log?**
No. Neither `hideway.log` nor Copy diagnostics ever contain keys or tokens.

## When something breaks

**I was asked to sign in again after about an hour.**
Versions before 3.2.6 could lock themselves when the license service stopped recognising the session. The log said `locked: sig_missing`. Update to 3.2.6 or later. See [Start-up and license](troubleshooting/startup-and-license.md).

**Fortnite closed after a match. Was it Hideway?**
In the logs we looked at, Hideway recorded no crash and the game process ended by itself. See [The game closes or crashes](troubleshooting/game-closes-or-crashes.md).

**The launcher says "not the signed one".**
A file in `core\` was changed or is missing. Use **Restore the files** or download the package again. See [Launcher and updates](troubleshooting/launcher-and-updates.md).

**"Cannot reach license server".**
Hideway keeps running for up to 15 minutes without the server, then locks. Check your internet and your clock. See [Start-up and license](troubleshooting/startup-and-license.md).

**DMA OFFLINE.**
Use a motherboard USB port, power the game PC, close other tools that use the card, and accept the UAC prompt. See [DMA card](troubleshooting/dma-card.md).

**The overlay is all black.**
Turn off **Visuals > Fuser mode** unless you use a capture card.

**What should I send to support?**
Your version, **Copy diagnostics**, both `hideway.log` and `hideway.log.1`, and what you were doing. See [Collect diagnostics](troubleshooting/collecting-diagnostics.md).
