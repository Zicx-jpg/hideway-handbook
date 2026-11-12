# Install and first start

Allow about ten minutes the first time.

## 1. Put the folder somewhere you own

Unzip the package into its own folder, for example `D:\Hideway`. **Do not run it from inside the zip.**

```
Hideway\
  HidewayLauncher.exe     <- the only program you run
  core\                   <- everything else (signed files, DLLs, offsets, configs)
```

Keep `HidewayLauncher.exe` and the `core` folder together. You never start anything inside `core\` by hand; the launcher starts the game module for you.

{% hint style="info" %}
The DMA runtime files (`vmm.dll`, `leechcore.dll`, `FTD3XX.dll`, `dbghelp.dll`, `symsrv.dll`) must stay next to `Hideway.exe` inside `core\`. They are hash-checked on every start; a missing or changed file is refused.
{% endhint %}

## 2. Power up the hardware

1. Start the **game PC** with the DMA card installed.
2. Plug the card's USB cable into the **overlay PC**.
3. Optional: plug in your input device.

## 3. Start the launcher

Double-click `HidewayLauncher.exe` and accept the Windows administrator prompt. The launcher is the front door for every Hideway game. See [The launcher](the-launcher.md).

{% hint style="info" %}
Windows SmartScreen may show a warning the first time, because the programs are not code-signed yet. Choose **More info > Run anyway**. Do not turn off Windows protections.
{% endhint %}

Click **Launch** on the Fortnite card. The launcher first checks the module's files against the publisher's signed manifest, then starts it.

## 4. Sign in

Use **one** of these:

{% tabs %}
{% tab title="License key" %}
Type or paste your key and press **Activate**. Tick **Remember on this device** to store it encrypted for your Windows account only.
{% endtab %}

{% tab title="Website button (Web Loader)" %}
Sign in on the Hideway website / customer panel and press the **Web Loader** button. The app must already be open on its sign-in screen. The loader listens on `127.0.0.1` port `1337` only. If another program uses that port, the sign-in screen tells you; the license key still works.
{% endtab %}
{% endtabs %}

## 5. Start Fortnite on the game PC

After signing in the overlay starts. **Insert** opens the menu, **End** exits (both can be changed in Misc > Keys). Wait for the game's lobby, then join a match.

## 6. Check that everything is connected

Open **Debug**. If you do not see a Debug page, turn on **Misc > Debug > Show debug page**. The **READY CHECK** card at the top lists each part in green, orange or red. See [READY CHECK](ready-check.md).

{% hint style="success" %}
In the lobby, rows like "waiting (lobby / loading)" are normal. Players only appear once a match has started.
{% endhint %}

## First minutes in a match

1. Open **Config** and pick a starting point under **Presets** (ESP only, Clean visuals, Full visuals, Subtle aim assist). A preset only changes the options it lists.
2. Fine-tune on **Visuals** and **Radar**. Rest the cursor on any option for a short explanation.
3. If boxes sit slightly ahead of or behind the players, adjust **ESP time offset** (Misc) by a few milliseconds.
4. Your changes save by themselves (Auto-save). See [Configs](../guides/configs.md).

## Something did not work?

Go to the [Quick checklist](../troubleshooting/quick-checklist.md).
