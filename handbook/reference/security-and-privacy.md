# Security and privacy

This page is about **your PC** and **your data**: what Hideway checks, what it sends, and what it does not protect. It says nothing about any game's anti-cheat; see the warning on the [first page](../README.md).

## What Hideway sends over the network

| To | What | Why |
|---|---|---|
| The license service (KeyAuth) | Your license key and a hardware identifier (your Windows account SID) | Check the license and lock it to one PC |
| The release host in `update_source.txt` | An update check, and the signed game-data packs (**Auto-update game data**) | Find new signed releases and the offsets for the current game build |
| The Hideway support service (a Cloudflare Worker) | By itself, every 10 minutes: a request for the announcement, with no data in it. Only when you press **Send report to support** (Debug) or send one from the launcher's Help page: your text, the category, the contact you typed, the program version and, if you leave it on, diagnostics (system checks, the tail of the logs and the black box, with your Windows user name and profile path removed) | Support tickets and announcements |
| The Hideway radar relay (a Cloudflare Worker) | **Only if you turn on Share radar online** (off by default): the radar snapshot (positions, teams, health, and names unless **Web radar names** is switched off in the config file, see below) over HTTPS, with a push key that only your PC knows and the key that is in the link | A friend on another network can open your radar |
| Nothing else | | Settings, configs, logs and positions stay on your PC |

Your license key is never part of a report, a log or a support bundle, and neither are player names or positions (except in the radar relay, as above). The **local web radar** serves a page from your PC to this PC or your own network; it is **off by default**, and LAN access and **Share radar online** are off by default too.

## What Hideway does not do

* It does not write to game memory.
* It does not turn off or change Windows security settings.
* It does not put your license key in the log, in diagnostics or in a support bundle.

## Updates and files

* Every release is **signed** (ECDSA P-256). The program refuses a release that does not verify or that is older than the one installed.
* Every file's **SHA-256** and size are checked when downloading, when applying, and after install.
* The module and the installer are checked **at the moment they start**, through a handle that denies write, rename and delete until the process exists: the file that was checked is the file that runs.
* Paths in a release cannot leave the install folder (no `..`, no drive letters, no Windows 8.3 short names).
* A bad update rolls back by itself.

## Configs and imports

* Files read from the config folders are size-limited.
* Imported or pasted configs validate every line and ignore anything unknown.
* **Machine-specific settings are never exported and never applied from shared text:** input device and its address / port, Kmbox values, web radar and LAN, audio device.

## Web radar

* The link contains an access key; without it every request is refused, and 12 wrong keys shut an address out for a minute.
* **Allow other devices (LAN)** is off by default. Turn it on only on a network you trust.
* **Share radar online** is off by default and sends the radar to the Hideway radar relay so a friend anywhere can open it. The online link contains its own key, anyone who has it can watch, and **New online link** makes a new room and new keys so the old link stops working. Nothing is sent while the option is off.
* **Web radar names** (on by default, not in the menu: set `B|Web radar names|0` in your config file) off sends no names, to the local page or to the relay.

## Recordings

The **Rolling recorder** (on by default) keeps the last 2 minutes of the match, with the names and positions of the players, in memory only. It writes a file to the `recordings\` folder next to the program when you press the Save last minutes key or when the ESP really goes blank (at most 3 files per run, the newest 3 of each kind are kept). Those files stay on your PC; they leave it only if you send them to support or choose **Create it with the newest recording** in the support bundle. Untick **Debug > RECORDING > Rolling recorder** if you do not want them.

## Input device safety

A held mouse button is released on disconnect, link loss, shutdown and if Hideway crashes. The trigger never fires while the menu is open or panic is active.

## Test hooks

Test-only switches in the program need both an environment variable **and** a marker file beside the exe that only the publisher's test tools create. A stray environment variable does nothing on an installed copy.

## What is not solved

{% hint style="warning" %}
* The install folder is **writable by your Windows user**, while the launcher and overlay run **elevated** from it. The launch-time checks narrow this but do not remove it. Install the package in a folder only you can write to, and do not run it from a shared or download folder.
* The programs are **not Authenticode-signed** (no code-signing certificate yet), so Windows shows "unknown publisher".
{% endhint %}

## Reporting a security problem

Send the details privately to support (see [Collect diagnostics](../troubleshooting/collecting-diagnostics.md)); do not post them publicly.
