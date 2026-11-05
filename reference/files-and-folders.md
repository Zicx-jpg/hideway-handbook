# Files and folders

## The package

```
Hideway\
  HidewayLauncher.exe          the only program you run (starts core\HidewayLauncher.exe)
  core\
    HidewayLauncher.exe        the multi-game hub (kept current by signed updates)
    Hideway.exe                the Fortnite module
    HidewayUpdater.exe         the installer for updates
    vmm.dll, leechcore.dll, FTD3XX.dll      DMA runtime (MemProcFS / LeechCore / FTDI), hash-checked at every start
    dbghelp.dll, symsrv.dll    Microsoft debugging runtime used by MemProcFS for symbols
    VCRUNTIME140*.dll, MSVCP140.dll         Visual C++ runtime, application-local (no separate install)
    all\                       game structure data (offsets): classes\classes.txt, offsets\offsets.txt
    modules\                   modules.json (the game catalog) and art\
    configs\                   factory defaults (your own configs are in your profile, see below)
    release.json, release.sig, release_public_key.b64, verify_package.ps1   release integrity
    update_source.txt          the release host (one https line)
    README.txt, CHANGELOG.txt
    hideway.log, hideway.log.1  the log (created at first start)
    update\                    installer working files: updater.log, journal.json, backup\, staging\
    webradar.key               the web radar access key (created when you use the web radar)
```

{% hint style="warning" %}
Never edit or delete files in `core\` by hand, except the logs. The launcher checks them against the signed manifest and will refuse to start a changed file.
{% endhint %}

## In your Windows profile

```
%APPDATA%\Hideway\Fortnite\configs\            your configs (*.cfg); _last.txt = the one in use
%APPDATA%\Hideway\Fortnite\configs\_backups\   automatic backups before every overwrite
%APPDATA%\Hideway\Fortnite\configs\_trash\     deleted configs (restorable)
%APPDATA%\Hideway\Fortnite\configs\exports\    "Export to a file" writes here
%APPDATA%\Hideway\Fortnite\configs\import\     "Import newest file" reads from here
```

Your license and "remember" data are stored encrypted for your Windows account only.

## Files that can appear later

| File | What it is |
|---|---|
| `telemetry.csv` | Written when **Telemetry CSV** is on: one row per second of measured numbers, about 5.5 hours then it restarts |
| `recordings\*.hwrec` | Flight recordings from **Debug > RECORDING**. Share only with support |
| `portable.txt` | Create it beside `Hideway.exe` to keep configs next to the program instead of in your profile |

## Size limits

Files Hideway reads from the config folders are size-limited (64 KB for a config, 256 bytes for `_last.txt`). A bigger file is refused without being read.
