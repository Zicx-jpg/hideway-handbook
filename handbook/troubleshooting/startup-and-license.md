# Start-up and license

## The app does not start

| Message | What to do |
|---|---|
| *License service: license server URL is still the example placeholder* | You are running a build that was never configured for a server. Use the release you were given |
| *DMA runtime files missing / modified* | One of the DLLs next to the exe is missing or not the shipped version. Re-extract the release, or use **Restore the files** on the launcher |
| *all\ folder missing* | The offset dump must sit next to the exe (`all\classes`, `all\offsets`) |
| UAC prompt declined | Hideway needs administrator rights for the DMA driver. Accept the prompt |
| Windows SmartScreen warning | The programs are not code-signed yet. Choose **More info > Run anyway**. Do not disable Windows protections |
| An "already running" box that never goes away | Another Hideway or launcher is open (maybe hidden). Close it from Task Manager and start again |
| *Could not start* screen | Read the line shown and press **Retry**. Most causes: no internet, a wrong system clock (it must be within about 25 seconds), missing DMA hardware |

## The program starts but the overlay is black

**Visuals > HUD > Fuser mode** puts a pure-black window under the overlay for capture-card setups. Switch it off if you do not use a capture card.

## License

| Message | What to do |
|---|---|
| *Invalid / not found* | Check the key for typos. Keys are shown once and cannot be recovered: ask support to reset |
| *Device limit reached* | Ask support to deactivate an old device. Reinstalling Windows changes your device fingerprint |
| *Cannot reach license server* | The app keeps working for up to **15 minutes** offline, then locks. Check your internet connection and the **system clock** (a wrong clock fails the signed answer check) |
| *HWID mismatch* | A license is tied to one Windows account on first use. Ask support to reset it to move it |

## Web Loader sign-in does not work

The website's **Web Loader** button talks to Hideway on `127.0.0.1` port `1337`. The app must already be open on its sign-in screen. If another program uses that port, the sign-in screen says so; your license key still works.

## Sign-out and remember

**Remember on this device** stores the key encrypted for your Windows account only. **Sign out** returns to the sign-in screen. If you do not tick Remember, closing and reopening asks again.

## Still stuck?

[Collect diagnostics](collecting-diagnostics.md). Your license key is never in the diagnostics or in the log.
