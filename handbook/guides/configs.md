# Configs: presets, auto-save, backups

A **config** is a named set of all your options. Hideway's config system is built so that you do not lose work: changes save by themselves, every overwrite keeps a backup, deletes go to a trash, and the program starts on the config you used last.

## The basics

| You want to | Do this |
|---|---|
| Switch config | Top-bar dropdown, or **Config > CONFIGS**, or the **Next / Previous config key** |
| Make a new one | **Config > MANAGE**: type a name, **Create from current settings** |
| Copy one | **Duplicate active as this name** |
| Rename / delete | **Rename active to this name** / **Delete active** (goes to a trash, restorable) |
| Go back to factory values | **Reset to defaults** |
| See the folder | **Open config folder** |

Names may contain letters, digits, spaces, `-`, `_` and `.`.

## Auto-save

**Auto-save config** (Misc, on by default) writes the active config **2.5 seconds after your last change**, and when the program closes. The old file is kept as a backup first. With Auto-save **off**, only **Save config** writes the file, and **CHANGES** shows what differs from the saved file, for example `Auto-save config: on > off`.

## Undo

Edits can be undone. Imports and restores are undoable too.

## Backups

Before a config file is overwritten, a copy is stored (**Config > BACKUPS**, at most one every 2 minutes, the last 20 kept). **Restore** puts one back.

## Presets

**Config > PRESETS** applies a short list of options on top of your current settings (ESP only, Clean visuals, Full visuals, Subtle aim assist). It does not touch the options it does not list.

## Share a config

* **SHARE > Copy config / Import config**: as text, for chat.
* **FILES > Export to a file / Import newest file**: through the `exports` and `import` folders inside the config folder.

Imports validate every line and ignore anything unknown. **Machine-specific settings** are never exported and never applied from shared text: input device and its address, serial port, Kmbox values, web radar, LAN access and port, audio device. Your own config files keep them.

## Switching with keys

Set **Next config key** and **Previous config key** (Misc > KEYS). A small message shows the name. The config you leave is saved first when Auto-save is on.

## Where the files are

```
%APPDATA%\Hideway\Fortnite\configs\            your configs (*.cfg), _last.txt = the one in use
%APPDATA%\Hideway\Fortnite\configs\_backups\   automatic backups
%APPDATA%\Hideway\Fortnite\configs\_trash\     deleted configs
```

A new Hideway folder, a reinstall or a new version keeps them all. Delete these folders only if you want to lose them.

{% hint style="info" %}
Older versions kept configs next to the program. They are copied to the profile folder once, never overwriting anything there.
{% endhint %}
