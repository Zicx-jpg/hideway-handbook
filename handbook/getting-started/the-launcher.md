# The launcher

`HidewayLauncher.exe` is the multi-game hub. It checks your files, starts the game module and keeps it updated. It runs with administrator rights.

## Library

One card per game ("Fortnite" today, more later).

| Button | What it does |
|---|---|
| **Launch** | Checks the module's files against the publisher's signed manifest, then starts it. The check and the start are the same file: a file swapped after the check is refused |
| **Verify files** | Re-checks the files on demand |
| **Restore the files** | Appears when something was changed or deleted. It sends you to **Updates** to put the files back |

## System

Real checks of this PC, each green / orange / red, with one **Next:** line for the first thing that is not green:

* Windows version and administrator rights
* DMA runtime files
* The DMA card's USB bridge
* Input device
* Updates

**Copy diagnostics** copies a report for support. It contains no license key and no user name.

## Updates

Signed releases only. A new version is downloaded in the background and checked against the publisher's signature and SHA-256 hashes. **Nothing is installed until you click.** If the new version does not start, the previous one is restored automatically. See [Updates](../guides/updates.md).

The Updates page also shows **What's new** for the installed version.

## Settings and About

Launcher settings and the version information.

## Good to know

* Only **one** launcher can run at a time. A second copy waits with an "already running" box.
* The overlay of the game module covers the launcher after you press **Launch**; use the module's menu key (Insert by default) to open the menu.
* Command-line options: `--demo`, `--no-update`, `--page <name>`.

{% hint style="info" %}
If the launcher says a file is "not the signed one", do not run the program. Use **Restore the files** or download the package again and verify it.
{% endhint %}
