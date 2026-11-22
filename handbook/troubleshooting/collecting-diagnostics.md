# Collect diagnostics for support

A good report gets a quick answer. Send **all** of the following; it takes two minutes.

## The short way: one zip

**Debug > SUPPORT > Create support bundle** (Turn Debug on in Misc first), or **System > Support bundle** in the launcher. One zip appears on your Desktop with:

* `system.txt` (Windows build, CPU, memory, displays, administrator or not), `config.txt` (your settings, without COM port or IP), the last 2 MB of `hideway.log` and `hideway.log.1`, this session's log, the **black box** of the last minute and your newest saved black box files, `gameinput_debug.txt` (the controller report) and `memmap.txt`,
* optionally the newest **recording** (**Create it with the newest recording**; stop a running recording first; it can be hundreds of MB).

Your Windows user name and profile folder are removed from every text, and no license key, token or password is ever written into any of these files. Send that single zip and skip steps 2 and 3. The steps below are the manual way and still work.

## 1. The version

Config > ABOUT, the bottom of the menu, or the launcher's About page. Example: `3.2.6`.

## 2. Copy diagnostics

**Debug > OFFSET HEALTH > Copy diagnostics.** (Turn Debug on in Misc first.) It copies a report with:

* the Hideway version and offset status,
* each OFFSET HEALTH row,
* the **DATA HEALTH** table,
* frame / performance numbers,
* the input device state,
* the log.

It does **not** contain your license key.

## 3. The log files

From `core\`:

```
hideway.log
hideway.log.1      (the older half, if it exists)
```

Plain text; no keys or tokens. Do **not** delete them before sending: a restart appends to them, but a crash is most useful in the log that was written at that moment.

## 4. What you were doing

* Which page was open and which option you had just changed.
* Lobby or match? Which mode?
* Did it happen once or every time? What do you do to make it happen?
* Did the **game** close, or **Hideway**? ([The game closes or crashes](game-closes-or-crashes.md))

## 5. A recording (optional, for aim / ESP problems)

**Debug > RECORDING > Start recording** writes a `.hwrec` flight recording of raw frames and presentations. Stop it with **Stop recording**. It is about 0.5 MB per second with 15 players and capped at 1.5 GB. Share the file only with support.

### The rolling recorder: record it after it happened

A glitch that happens once an hour is hard to catch with **Start recording**. Since 3.7.4 the **Rolling recorder** (Debug > RECORDING; Debug on in Misc first) is on by default: Hideway keeps the **last 2 minutes** in memory, at most 96 MB, writing nothing to disk. When an enemy vanishes or the aim jerks:

1. Press the **Save last minutes key** (set it in the same card) or click **Save last minutes**. A notice names the file.
2. Find it in `recordings\`: `rolling_<date>_<time>.hwrec`. Send it with the log.

If the ESP really goes blank while the game still draws enemies (a **REAL** line in the log), the last 2 minutes are saved by themselves as `event_<date>_<time>.hwrec`, at most 3 per run. Only the newest 3 files of each kind are kept. **Create it with the newest recording** in the support bundle takes the newest of them. Starting a normal recording pauses the rolling one; it resumes when you stop.

## 6. A screenshot

Say what the screenshot is of. **Do not show your license key** or the radar link (it contains an access key).

## From the launcher

The **System** page has **Copy diagnostics** and a **Support bundle** zip (the same bundle as above, plus the updater log and the signed manifest). Neither includes your key or your user name.

## Where to send it

Discord: <https://discord.gg/hidewaydma>. Include everything above in one message or one zip.

{% hint style="warning" %}
Never post your license key, the web radar link, or the contents of `webradar.key`.
{% endhint %}
