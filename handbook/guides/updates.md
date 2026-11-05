# Updates

Hideway updates through **signed releases**. Nothing is installed without your click, and a bad update undoes itself.

## How an update works

1. The launcher (and the app, **Config > UPDATES**) checks the release host for a new signed release.
2. A new version is **downloaded in the background** and checked: the publisher's **signature** on the release manifest and the **SHA-256** of every file.
3. Nothing is installed until you press **Restart to install** (or the equivalent button on the launcher's **Updates** page).
4. The installer (`HidewayUpdater.exe`) backs up the current files, writes a journal, swaps the files, starts the new version and waits for it to report **healthy**.
5. If the new version does not start or does not report healthy, the previous version is **restored automatically**.

## What is never touched

Your **configs** and your license / remember data are never overwritten. Configs live in your user profile anyway ([Configs](configs.md)).

## Manual controls

| Where | Control |
|---|---|
| Launcher > Updates | Check, install, **What's new**, **Restore previous version** |
| Config > UPDATES | Installed version and status |
| Command line | `HidewayUpdater.exe --recover` undoes an install that was interrupted (power cut, crash) |

If an update was interrupted, just start Hideway again; it restores the previous version by itself. If `Hideway.exe` will not start at all, run `HidewayUpdater.exe --recover`.

## The release host

The address is in `update_source.txt` (one https line). While the file is empty or starts with `#`, automatic updates are off.

## What is checked

* The manifest signature (ECDSA, publisher's key). A downgrade to an older version is refused.
* Every file's SHA-256 and size, re-checked when applying and again after install.
* Paths in a release cannot escape the install folder, and Windows 8.3 short names are refused.
* The module and installer are checked again **at the moment they start**.

See [Security and privacy](../reference/security-and-privacy.md).

## Offsets are separate

A Fortnite patch needs fresh offsets, which are part of a release (`all\`). See [After a Fortnite update](after-a-fortnite-update.md).

## When updating fails

[Launcher and updates](../troubleshooting/launcher-and-updates.md).
