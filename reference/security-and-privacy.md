# Security and privacy

This page is about **your PC** and **your data**: what Hideway checks, what it sends, and what it does not protect. It says nothing about any game's anti-cheat; see the warning on the [first page](../README.md).

## What Hideway sends over the network

| To | What | Why |
|---|---|---|
| The license service (KeyAuth) | Your license key and a hardware identifier (your Windows account SID) | Check the license and lock it to one PC |
| The release host in `update_source.txt` | An update check | Find new signed releases |
| Nothing else | | Settings, configs, logs and positions stay on your PC |

The **web radar** serves a page from your PC; nothing goes to the internet. It is **off by default**, and LAN access is off by default too.

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
* **Web radar names** off sends no names.

## Input device safety

A held mouse button is released on disconnect, link loss, shutdown and if Hideway crashes. The trigger never fires while the menu is open or panic is active.

## Test hooks

Test-only switches in the program need both an environment variable **and** a marker file beside the exe that only the publisher's test tools create. A stray environment variable does nothing on an installed copy.

## What is not solved

{% hint style="warning" %}
* The install folder is **writable by your Windows user**, while the launcher and overlay run **elevated** from it. The launch-time checks narrow this but do not remove it. Install the package in a folder only you can write to, and do not run it from a shared or download folder.
* The programs are **not Authenticode-signed** (no code-signing certificate yet), so Windows shows "unknown publisher".
* Offsets come from a third-party community source; their *correctness* is trusted, their *format* is validated.
{% endhint %}

## Reporting a security problem

Send the details privately to support (see [Collect diagnostics](../troubleshooting/collecting-diagnostics.md)); do not post them publicly.
