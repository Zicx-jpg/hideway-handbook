# Install and first launch

Plan on about ten minutes.

## 1. Unzip it somewhere you own

Extract the package to its own folder, for example `D:\Hideway`. Do not run it from inside the zip.

```
Hideway\
  HidewayLauncher.exe     the only program you start
  core\                   everything else: game module, DLLs, game data, configs
```

Keep `HidewayLauncher.exe` and the `core` folder together. You never start anything inside `core` by hand. The DMA files in there (`vmm.dll`, `leechcore.dll`, `FTD3XX.dll`, `dbghelp.dll`, `symsrv.dll`) are checked on every start, so do not move or replace them.

## 2. Power up

1. Start the game PC with the DMA card in it.
2. Plug the card's USB cable into the overlay PC.
3. Plug in your input device if you have one.

## 3. Start the launcher

Double-click `HidewayLauncher.exe` and accept the administrator prompt. Windows SmartScreen may warn the first time because the programs are not code-signed yet. Choose **More info > Run anyway** and leave Windows protection on. Then press **Launch** on the Fortnite card. The launcher checks the module's files against the signed list first, then starts it. More on the launcher: [The launcher](the-launcher.md).

## 4. Sign in

The sign-in screen has three tabs:

* **Create account** (first time). Choose a username and a password (8 characters or more), paste the license key you bought, and press **Create account**. The key is redeemed by the account and you are signed in. One key makes one account.
* **Sign in** (every time after that). Username and password, then **Sign in**. Tick **Keep me signed in** to store the account, encrypted, for your Windows account only; Hideway then signs in by itself at the next start.
* **License key.** The old way still works: paste the key and press **Activate**, no account needed.

Also possible:

* **Website button.** Sign in on the customer panel and press the Web Loader button while the sign-in screen is open. It talks to Hideway through `127.0.0.1` port 1337 and nowhere else. If another program already uses that port, the sign-in screen says so and the key still works.

## 5. Start Fortnite on the game PC

After sign-in the overlay appears. **Insert** opens the menu and **End** closes Hideway. Both can be changed under Misc. Go to the lobby and join a match: the lobby has no other players to draw.

## 6. Check the connection

Turn on **Misc > Debug > Show debug page**, then open **Debug**. The READY CHECK card at the top lists each part in green, orange or red and tells you what to fix first. See [Is everything connected?](ready-check.md).

In the lobby, "waiting" rows are normal.

## Your first match

1. Open **Config** and pick a preset under **Presets**: ESP only, Clean visuals, Full visuals or Subtle aim assist. A preset only changes the options it lists.
2. Adjust **Visuals** and **Radar** to taste. Hold the cursor on any option for a one-line explanation.
3. Run the game borderless or full screen on the monitor you capture. If the boxes seem a little ahead of the game image on a fuser, that is the capture card's delay, see [Boxes lag or run ahead](../troubleshooting/esp-quality.md).
4. Your changes are saved by themselves. See [Configs](../guides/configs.md).

If something is not right, go to the [quick checklist](../troubleshooting/quick-checklist.md).
