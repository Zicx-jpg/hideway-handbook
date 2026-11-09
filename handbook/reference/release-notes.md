# Release notes

Newest first. This is the same text the launcher shows under **Updates > What's new**.


## Latest update

* The Simple / Advanced menu is gone: the menu is now all-in-one. Every option is on its page, the **Mode** button in the top bar and the **Menu mode** option are removed, and the search box still finds any option.

## 2.10.2 - 2026-11-05

* Fix: with Mouse 1 as the aim key, clicking to place a wall no longer makes the aim lock onto an enemy behind it.
* New option Only with a gun in hand (Aimbot page, on by default): aim and trigger stay off while you hold a build piece, the pickaxe or an empty weapon.
* If the held weapon cannot be read, aim keeps working as before.

## 2.10.1 - 2026-11-03

* Data health: a new table on the Debug page shows, for every data source (names, Team ID, health and shield, weapon, skeleton, three kinds of visibility, loot, match counters), whether it is live, partial, missing, waiting or off, and how many players have it.
* Partial and missing rows say why, for example teammates only when the game sends no enemy health.
* The table is included in Copy diagnostics.

## 2.10.0 - 2026-11-03

* Security: the module and the installer are checked against the signed release at the moment they start (same file checked and run); a pasted or imported config can no longer switch on input hardware, change device addresses or open the web radar; web radar LAN access is now off by default; files read from the config folders are size-limited.
* ESP: players fade in, overlapping name labels are lifted apart. Config: see what changed since the last save, export and import through files, keys for the next and previous config.
* Launcher: the Updates page shows what is new. Skeleton: half-written bone arrays are refused. The log ends each match with one summary line.

## 2.9.1 - 2026-11-03

* Your configs now live in your user profile (%APPDATA%\Hideway\Fortnite\configs): a new Hideway folder, a reinstall or a new version keeps every config and the one you were on. Configs next to the program are copied over once.
* Skeleton poses of mid and far players refresh several times faster (time-based instead of tick-counted).
* The log now shows whether health is sent for teammates and enemies and how submit-time visibility compares with the render-time rule.
* Simple / Advanced menu, config system, ESP smoothness, health recovery, Team ID, squad list and match info from 2.7.0 to 2.9.0.

## 2.9.0 - 2026-11-03

* Simple / Advanced menu: a Mode button in the top bar. Simple shows the essentials of every page; Advanced shows every setting. Hidden settings keep their value and the search still finds everything.
* Config system, ESP smoothness setting, health recovery, Team ID, squad list and match info from 2.7.0 and 2.8.0.

## 2.8.0 - 2026-11-03

* Config system: auto-save, unsaved-changes state, Undo, backups before every overwrite, duplicate / rename / delete (to a trash) and the program starts on the config you used last.
* New ESP smoothness setting (Responsive / Balanced / Silky), measured on real recordings.
* Health and shield recovery, Team ID, squad list, match info, low health outline and enemy ammo from 2.7.0.

## 2.7.0 - 2026-11-02

* Health and shield bars recovered when the game reads 0: the program re-reads the player's health set and falls back to the copy kept in the player state, and shows no bar if neither has a real value.
* Team ID: every duo, trio and squad shows the game's own team number (coloured per team) before the name; new squad list; match info (players left, teams left) at the top of the screen.
* Low health outline, enemy ammo, bar style, side and damage trail options. Cleaner menu: the Debug page and diagnostic lines only appear when you ask for them.

## 2.6.0 - 2026-11-02

* Menu: 8 animated themes (Nebula, Sakura, Glacier, Toxic, Ember, Mono, Chroma, Custom), motion and glow on every control, new launcher motion and icons, trigger indicator ring, Show bots switched on once for configs saved by older versions.

## 2.5.2 - 2026-11-02

* Loot ESP: pickup layout found from the first samples (public hint as a search shortcut) and never proven on building pieces; reservoir sampling per class.
* Health bars only when the game exposes a value; Show bots on by default; assault rifles and SMGs (anim id 10) classed as rifle on 43.00.
* Options Visibility check, Fast position refresh and DMA stall guard now reach the pipeline. Spectator list and Audio alerts now have menu cards. Config saves are atomic.

## 2.5.1 - 2026-11-02

* Loot ESP: the pickup layout is no longer proven on building pieces (shared item definitions required, more samples per class).
* Show bots is on by default for new configs; the log says how many bots are in the match.
* The real-names verdict in the log no longer flips back and forth in bot lobbies.

## 2.5.0 - 2026-11-02

* Fortnite 43.00 (CL-59596594) support: new class layout, GEngine address and the new skeleton bone order.
* ESP: the FOV ring shows the real FOV of the weapon in hand, the radar arrow follows the camera, range rings with distances, spectators ignore teammates (option), platform names in words, no '0 kills', 'Hide knocked players' option.
* Player names: the program scans the player state for the real display-name field when the expected one gives no names, and logs where it found it.
* Not verified on the live game: names, bones and loot on 43.00.

## 2.4.3 - 2026-11-01

* Real player names: when the game's custom-name field is not where the dump says, the program now scans the player state, finds the field by what it reads (distinct, name-like text for several players) and logs where it found it.
* If no field is found the log says so and the placeholder names stay in use.
* The 2.4.2 menu, visibility and timestamp changes are unchanged.

## 2.4.2 - 2026-10-31

* Plainer menu: flat dark surfaces, text navigation, square tick boxes, no glow or animated effects, denser rows.
* All visibility settings now sit together on the AIMBOT page, with a line that says whether Submit-time visibility can work on your game build.
* Submit-time visibility reads the render timestamps from where the game keeps them (relative to the discovered render time) instead of a guessed address.
* Fixed slider values being cut after 7 characters (0.15 deg showed as 0.15 de).
* Flat sign-in screen and tooltips.

## 2.4.1 - 2026-10-30

* Busy matches no longer fall back to slow reads: the attach-time scatter check ignores players who took damage, got a kill or changed weapon between two reads, and a failed check is retried (20 s, 40 s, 80 s, then every 2 minutes) instead of three times.
* A failed check now names the field that disagreed in the log.
* A crash now logs the module, offset and call chain.
* When the visibility timestamps cannot be read, the log shows the floats around the discovered render time so the right offsets can be found.

## 2.4.0 - 2026-10-30

* VisCheck (read-only): visible / occluded / out-of-view from the mesh's three render timestamps (submitted, rendered, rendered on screen) with a confidence and a self-check against the world clock; optional 'Submit-time visibility' (off by default)
* ESP: new 3D box style, facing-direction line (off by default), spectator counter that shows ? when it cannot be read
* Backend: projected-data cache (2D box, 8 corners of the 3D box and the 16 skeleton points per player, validated against the ESP's own projection to 0.0001 px); the facing direction and render timestamps are read on every path

## 2.3.0 - 2026-10-30

* Ferrum support rebuilt from the vendor's official documentation: 3 Mbaud, physical-button stream, API version shown, documented reply recognised
* WebRadar: WebSocket endpoint (/api/ws) next to the existing stream, same key, viewer cap and rate limits
* New read-only extras (config file options, off by default): spectator list, audio alerts with positional tones
* Game build check on every attach: warns when the game was updated but the offset data was not
* Backend: math library, ballistic simulator, spatial events, versioned data providers, snapshot primitive; scatter reads no longer zero buffers twice
* Quality: 27-program test gate, AddressSanitizer runner (16 programs clean)

## 2.2.1 - 2026-10-30

* Fortnite class data refreshed from the 2026-10-24 dump: weapon data, ammo and weapon class offsets and the skeleton arrays now match the current game build (the old file was from before the last game update)
* A new automatic check refuses a release whose class data and offsets come from different game builds
* Support tooling: tools\make_classes_from_dump.ps1 rebuilds the class data from a public dump with a change report

## 2.2.0 - 2026-10-29

* Triggerbot: new Toggle key mode, pauses while the menu is open or panic is on, and a Reaction spread setting (most reactions close to the delay, a few slower)
* ESP: the player the aimbot is locked on or the trigger is about to shoot gets its own colour; far players are drawn with reduced detail (LOD)
* CONFIG: new KEYBINDS card lists every hotkey and flags conflicts
* Launcher: System page can save a support bundle (one zip, no keys, user name removed)
* The log now rotates to hideway.log.1 instead of being deleted when it is full

## 2.1.2 - 2026-10-29

* Library: the Fortnite card now shows the Hideway Fortnite box art (a signed picture file; the launcher only draws it when its hash matches the signed release)
* Card layout taller to show the whole picture

## 2.1.1 - 2026-10-29

* Cleaner package: the only program at the top of the folder is HidewayLauncher.exe, everything else is inside the core folder
* README and install page updated for the new layout

## 2.1.0 - 2026-10-29

* New: Hideway Launcher (HidewayLauncher.exe) - one hub for every Hideway game. Sign in once, pick a game from the library, press Launch. Fortnite is the first module; more games arrive as signed updates without a new launcher.
* The launcher checks a game's files against the publisher's signed manifest before it starts them (Ready / Files modified / Files missing), and its System page checks Windows, administrator rights, DMA runtime files, the card's USB bridge and the input device with one 'Next:' line for anything not green.
* Updates, Settings and About live in the launcher; a failed update restores the previous version and brings the launcher back by itself.
* Hideway.exe still starts on its own exactly as before.
* Tested: 15 offline suites plus 42 launcher tests (strict catalog parser, integrity against a real signed release), real clicks through every launcher page, and a real Launch click that starts the game module.

## 2.0.6 - 2026-10-29

* DMA: if the card drops off the bus (cable, USB reset) Hideway now notices, closes the link and reconnects by itself, and the status says DMA OFFLINE instead of waiting for Fortnite.
* Aim and trigger: the lead now uses the player's acceleration (capped, weighted by confidence) - on recorded matches the median miss 100 ms ahead is about 30% smaller, the worst cases are unchanged.
* READY CHECK: wraps its next step over lines, shows the Fuser state (black window under the overlay) and a short offsets line; the tester README explains each red or orange row.
* Tested: 15 offline suites including a simulated card drop and return.

## 2.0.5 - 2026-10-29

* Names: player names are now read from the game's real display-name field (the previous field holds a placeholder when names are hidden); the live log says which field is used.
* Skeleton: anchored on the pelvis and smoothed - limbs no longer jitter when the root position steps with network updates (about 6-15x less joint jitter on recorded matches). New option: Visuals -> Skeleton -> Smooth skeleton.
* New READY CHECK: a checklist (DMA card, Fortnite, game data, camera, input device, offsets) on the Debug page, and on the Aimbot page until everything is ready, with the one thing to do next.
* Status: the top bar tells DMA OFFLINE from WAITING FOR FORTNITE.

## 2.0.4 - 2026-10-29

* Status: the top bar and watermark now tell apart DMA OFFLINE (the card does not answer), WAITING FOR FORTNITE (the card is connected but the game is not found on the target PC) and DMA ONLINE. Before, a connected card showed DMA offline whenever Fortnite was not running.
* Internal: no change to sign-in, updates or features.

## 2.0.3 - 2026-10-28

* Visibility: the check now defaults to UE5 render time (the game's own check). Misc/Aimbot: new VISIBILITY card with the check, its tolerance and a status line; the old Wall check style setting is replaced by Visibility check.
* Performance: with the UE5 check and loot ESP off the level geometry reader is no longer started.
* Menu clean-up: options appear only when their switch is on (skeleton, box, head, snaplines, arrows, crosshair, loot, reboot cards, radar, web radar, prediction, close/sticky aim, weapon overrides); engine switches moved to Misc -> ENGINE (ADVANCED, shown with Advanced debug); Rainbow FOV removed; duplicate rows removed from Config.

## 2.0.2 - 2026-10-28

* New motion estimator: one velocity / acceleration estimate per player shared by the ESP, aim lead and trigger lead. On recorded matches the position 100 ms ahead is about 2x closer (p95 76 cm -> 33 cm). Switch: Misc -> Motion estimator.
* New Debug -> LATENCY card: measures the delay from a mouse move to the game camera (10 tiny moves that cancel out) and can set Prediction lead / Trigger lead from it.
* New option: Measured input latency.
* Internal: more offline tests; no changes to sign-in or the update system.

## 2.0.1 - 2026-10-28

* Menu: every option now has a help text; removed all third-party names from the menu and help.
* Menu: fixed the '##Rifle' style suffix showing on the Weapons page; text that does not fit now ends with '...' instead of being cut off.
* Aimbot: the Prediction lead now only applies while Prediction is switched on.
* Overlay: if VSync does not pace the frames (over 300 fps) the overlay caps itself at 240 fps instead of using a whole CPU core.
* Config: nan / inf values in hand-edited or shared configs are refused; new installs start from factory defaults.
* Sign-in screen: the Web Loader hint no longer overlaps the buttons; the menu and sign-in screen now show the real version number; CONFIG - UPDATES explains itself in demo mode.

## 2.0.0 - 2026-10-28

* First tester release.
* Sign in with a license key or with the KeyAuth Web Loader button (browser handoff on 127.0.0.1:1337).
* Signed automatic updates with rollback (CONFIG - UPDATES).
* Loot, container, vehicle and reboot-card markers (read-only).
* Trigger bot and aim use the Unreal Engine 5 visibility check.
