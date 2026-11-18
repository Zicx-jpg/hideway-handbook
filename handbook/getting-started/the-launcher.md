# The launcher

`HidewayLauncher.exe` is the front door. It checks your files, starts the game module and keeps everything up to date. It runs as administrator.

## Library

Each game has a card (Fortnite and Wardogs at the moment).

* **Launch** checks the module's files against the signed list and starts it. A file that changed after the check is refused.
* **Verify files** repeats the check on demand.
* **Restore the files** shows up when something was changed or deleted. It takes you to **Updates**, which puts the files back.

## System

A set of real checks on this PC, each green, orange or red, with one **Next:** line naming the first thing to fix:

* Windows version and administrator rights
* the DMA runtime files
* the DMA card's USB bridge
* the input device
* updates

**Copy diagnostics** puts a report on the clipboard for support. It has no license key and no user name in it.

## Updates

Only releases signed by the seller are accepted. A new version downloads in the background and is checked against its signature and file hashes. Since 3.3.6 the launcher installs a new version by itself when it starts (turn it off in Settings); before that, nothing is installed until you click. If the new version does not start, the previous one is put back automatically. The page also shows what changed in the version you have. See [Updates](../guides/updates.md).

## Good to know

* Only one launcher runs at a time. A second copy shows an "already running" box.
* After **Launch**, the game module's overlay covers the launcher. Press **Insert** to open the module's menu.
* Command-line options: `--demo`, `--no-update`, `--page <name>`.

{% hint style="info" %}
If the launcher says a file is "not the signed one", do not run it. Use **Restore the files**, or download the package again and verify it.
{% endhint %}

## Your account

The box at the bottom of the left column shows who is signed in and when the license ends. Click it to open the account panel:

* **Add a key** adds the time of another license key to your account. Use it to renew before the end date or to stack more days. It needs an account (a plain license-key sign-in has none: sign out and use **Create account** once).
* **Buy or renew a key** opens the shop. **Sign out** signs you out.
* From 7 days before the end date a banner at the top reminds you, with **Renew** and **Add a key** buttons.
* Forgot your password? Press **Forgot password?** on the sign-in screen and open a ticket on Discord with your username.
