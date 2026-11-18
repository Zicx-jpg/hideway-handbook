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

**Visuals > Fuser mode** puts a pure black window under the overlay for capture-card setups. Turn it off if you do not use a capture card.

## License

| Message | What to do |
|---|---|
| *Add a key* says it needs an account | You signed in with just a license key. Sign out, choose **Create account**, and the account keeps every key you add |
| *Wrong username or password.* | Check both. The same sentence is shown for an unknown username on purpose. After 5 refused attempts in a minute the launcher makes you wait before the next one (the screen shows the countdown) |
| *That username is taken.* | Pick another username on the **Create account** tab |
| *That license key has already been used.* | A key makes one account. Sign in with the account that used it, or ask support |
| *That license key is not valid.* | Check the key for typos. Keys are shown once and cannot be recovered: ask support to reset |
| *Invalid / not found* | Check the key for typos. Keys are shown once and cannot be recovered: ask support to reset |
| *Device limit reached* | Ask support to deactivate an old device. Reinstalling Windows changes your device fingerprint |
| *Cannot reach license server* | The app keeps working for up to **15 minutes** offline, then locks. Check your internet connection and the **system clock** (a wrong clock fails the signed answer check) |
| *HWID mismatch* | A license is tied to one Windows account on first use. Ask support to reset it to move it |

## Locked after about an hour

If the log ends with `locked: sig_missing` roughly an hour after you started, you are on a version before 3.2.6. The license service answered a routine check without its signature, and the program took that as a refused session and locked. From 3.2.6 on, Hideway opens a fresh session with your license instead, and an answer it cannot verify gets the same 15 minutes of grace as a lost connection. Update to 3.2.6 or later (the launcher's Updates page). A signed "banned" or "expired" answer still locks at once, as it should.

## Web Loader sign-in does not work

The website's **Web Loader** button talks to Hideway on `127.0.0.1` port `1337`. The app must already be open on its sign-in screen. If another program uses that port, the sign-in screen says so; your license key still works.

## Sign-out and remember

**Keep me signed in** (**Remember on this device** in the Hideway window) stores your account, or your key, encrypted for your Windows account only. The password is never shown again, never written to the log, and is wiped from memory once you are signed in. **Sign out** returns to the sign-in screen. If you do not tick Remember, closing and reopening asks again.

## Still stuck?

[Collect diagnostics](collecting-diagnostics.md). Your license key is never in the diagnostics or in the log.
