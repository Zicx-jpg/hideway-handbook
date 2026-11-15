# Launcher and updates

## The launcher says a file is not the signed one

A file in `core\` does not match the publisher's signed manifest: it was changed, deleted, or partly downloaded. The launcher refuses to start the module.

1. Press **Restore the files** (it sends you to **Updates**), or
2. Download the package again from your account or the [download page](https://download.hideway.cc/download) and unzip it into a fresh folder (see [Install and first start](../getting-started/install-and-first-start.md)).

Antivirus can quarantine a DLL; check its history if a file vanished.

## "Already running"

Only one launcher and one overlay can run at a time. Close the other one (Task Manager if it is hidden).

## Update does not start

* **Updates** page: the status line says why (no internet, the release host not reachable, nothing new).
* `update_source.txt` must hold one `https` line. Empty or starting with `#` = automatic updates off.
* Check your **system clock**; a wrong clock breaks signature checks.

## Update installed but the old version is back

A **bad update rolls back by itself**: if the new version does not start or does not report healthy, the previous one is restored. `update\updater.log` says why (for example `did not report healthy`). Common reasons: another Hideway was running, a missing runtime file, antivirus interfering.

## Update was interrupted (power cut, crash)

Start Hideway again; it restores the previous version by itself. If `Hideway.exe` will not start at all, run in `core\`:

```bash
HidewayUpdater.exe --recover
```

## It says a newer version is required

For KeyAuth builds: the application's Version in the KeyAuth dashboard differs from the one built into the program. Ask support; do not change it yourself.

## Downgrade refused

Releases carry a version and an **anti-downgrade** rule: an older signed release does not replace a newer installed one. Use **Restore previous version** only for the version the installer kept as backup.

## Where the logs are

| File | Contains |
|---|---|
| `hideway.log`, `hideway.log.1` | The program and launcher log |
| `update\updater.log` | The installer's log after an update |
| `update\journal.json` | The installer's state (for recovery) |

## The launcher's System page

It lists real checks of this PC (Windows, administrator, DMA runtime files, the card's USB bridge, input device, updates) with a **Next:** line. **Copy diagnostics** and the support bundle contain no license key and no user name.
