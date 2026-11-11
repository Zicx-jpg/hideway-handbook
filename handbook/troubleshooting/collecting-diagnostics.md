# Collect diagnostics for support

A good report gets a quick answer. Send **all** of the following; it takes two minutes.

## 1. The version

Config > ABOUT, the bottom of the menu, or the launcher's About page. Example: `2.10.2`.

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

## 6. A screenshot

Say what the screenshot is of. **Do not show your license key** or the radar link (it contains an access key).

## From the launcher

The **System** page has **Copy diagnostics** and a **support bundle** zip. Neither includes your key or your user name.

## Where to send it

Discord: <https://discord.gg/hidewaydma>. Include everything above in one message or one zip.

{% hint style="warning" %}
Never post your license key, the web radar link, or the contents of `webradar.key`.
{% endhint %}
