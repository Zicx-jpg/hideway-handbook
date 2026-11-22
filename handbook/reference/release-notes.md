# Release notes

Newest first. This is the same text the launcher shows under **Updates > What's new**.


## 3.7.7 - 2026-11-22

* Two new Fortnite-style skins in the ESP preview on the Visuals page: Squad Leader and Skull Raider.
* They're the first two now, the old outfits are still there. Use the arrows under the preview to switch.

## 3.7.6 - 2026-11-22

* Fixed a line at the bottom of the Config > ADVICE card that was cut off.
* Small fix, nothing else changed.

## 3.7.5 - 2026-11-22

* Config > ADVICE now warns you when the link to your DMA card keeps stalling during matches, and says what to try: plug it straight into a USB 3 port, swap the cable.
* Loading screens are ignored, so a healthy setup should never see it.
* When the recorder saves the last minutes on its own because the ESP really went blank, you get a message on screen, so you know there's a file to send.

## 3.7.4 - 2026-11-22

* Fixed a rare crash that could happen when the DMA card dropped out, or when you hit Disconnect, while Hideway was still reading.
* The Rolling recorder is on by default now. It only keeps the last 2 minutes in memory and doesn't write anything unless you press the save key or the ESP really goes blank. Debug > RECORDING turns it off.
* Crash lines in the log say a bit more about what the DMA link was doing.

## 3.7.3 - 2026-11-22

* The Visuals preview doesn't draw over the top bar anymore when you scroll.
* Long help notes (controller, MAKCU driver, web radar links) wrap onto a few lines instead of ending in dots.
* The info lines in Config > ADVICE aren't green anymore. Green looked like 'all good'.

## 3.7.2 - 2026-11-22

* Identical loot on the same spot is one label now, like Shield Potion x3. Visuals > LOOT ESP > Group identical loot, on by default.
* The overlay opts out of Windows power throttling, which could cause random long frames.
* ADVICE warnings go to the log too, and there are new ones for an aimbot or triggerbot with no key set, an ESP with everything turned off, and Share radar online being on.
* New Radar only preset.
* The Subtle aim assist preset described the wrong settings. Fixed.
* The Save last minutes key shows up in Config > KEYBINDS, so clashes get caught.
* Long notes on the Debug page wrap instead of being cut off.
* Saving the rolling recorder doesn't make the overlay hitch anymore.

## 3.7.1 - 2026-11-22

* New: Rolling recorder. It keeps the last 2 minutes in memory. When something odd just happened (an enemy vanished, the aim jerked), press the Save last minutes key or the button in Debug > RECORDING and it writes a file you can send. It also saves by itself when the ESP really goes blank.
* New: Config > ADVICE points out settings that probably work against you, like a low Render distance or a tiny aim field of view. It only tells you, it never changes anything.
* Loot, chest and vehicle labels stack under each other instead of piling up, and they stay off player names.

## 3.7.0 - 2026-11-22

* New: Debug > SUPPORT > Create support bundle. One zip on your Desktop with the logs, your settings (no COM port or IP), the black box and the reports, to send to support. Your Windows user name is removed and there's no key in it. The launcher's System page uses the same thing.
* The black box has a frame(ms) column and the log warns when the overlay itself hitches, so you can tell that apart from slow data.
* New: Enemy counter, off by default. A bar at the top with the enemies within 50, 150 and 300 m, how many are down and how far the nearest one is. Visuals > HUD.

## 3.6.2 - 2026-11-22

* Fixed the Aim bone setting. It hadn't done anything since 3.1.0. Head, Neck, Chest and Pelvis really aim at that part now, and Closest bone keeps the old behaviour.
* Heads up: the field of view is measured to the part you pick, so at close range a small one can miss a head. Use Closest bone, Close aim or a wider field of view.

## 3.6.1 - 2026-11-21

* Boxes don't flash between the hidden and the visible colour anymore. A player who was visible a moment ago keeps the visible colour for a split second. Aim and triggerbot aren't affected.

## 3.6.0 - 2026-11-21

* Fixed enemies disappearing because of Render distance. The default is 500 m now, a saved value under 250 m gets raised to 400 m once, and the new Far markers option (on by default) puts a small marker with the distance on anyone beyond it.
* Health bars: the game doesn't send enemy health, so enemy bars mostly show up for teammates and knocked players only. When a real value stops coming, the bar keeps the last one, dimmed, for 10 to 12 seconds instead of blinking.
* The aim keeps its lock when the game's drawn-recently flag blinks, so it stutters less.
* The head hit area sits a bit higher, where the game really counts a headshot.
* Controller on the game PC: the key table is found more reliably.
* Black box: new far and seen columns, and normal blank spells don't flood the log anymore.

## 3.5.0 - 2026-11-19

* A controller that's only plugged into the game PC works now (Ferrum or MAKCU, no XIM, no adapter). Click the Aim key or Trigger key box and press the button on the controller. The Aimbot page shows Game PC pad: readable, and what's held.
* New Aim activation option: Aim key, Aiming down sights, or both.

## 3.4.0 - 2026-11-19

* New CONTROLLER card on the Aimbot page. It shows the pads Windows sees and what's pressed, plus a Trigger pull slider for LT and RT.

## 3.3.8 - 2026-11-18

* Controller buttons can be the Aim key or Trigger key: A, B, X, Y, bumpers, triggers, stick clicks, Back, Start and the D-pad. Works with an Xbox pad, or anything Windows shows as one, plugged into the overlay PC.
* RDMA and other custom devices start the plain way now, so players stop disappearing every now and then. FPGA cards keep the fast start.

## 3.3.7 - 2026-11-18

* New account panel: click the license row at the bottom of the launcher to see your plan and end date, add another key, buy or renew, or sign out.
* A banner warns you when your license ends within 7 days.
* Forgot password? on the sign-in screen opens Discord support.
* A release can be put on hold if it turns out bad, so launchers that haven't installed it yet stop installing it.

## 3.3.6 - 2026-11-18

* The launcher installs a newer version by itself when it starts. You'll see an Updating Hideway screen with the download, then it restarts on the new version. If the new version doesn't start, it goes back to the old one. Settings > Install updates automatically turns it off.
* A release found later in a long session waits for the next start, a running game is never interrupted, and a failed install isn't retried in a loop (it waits 6 hours).
* The installer waits a few more seconds for the new version to report in.

## 3.3.5 - 2026-11-18

* New sign-in screen in the launcher: sign in with a username and password, create an account with a license key (one key, one account), or use the old License key tab. Error messages are clearer (wrong password, username taken, key already used), and after 5 refused attempts in a minute there's a short wait.
* The launcher shows who's signed in, and Hideway.exe has the same account sign-in in its start window.
* Website, Discord and Customer panel links on the sign-in screen. A remembered account is stored encrypted like a key and renewed quietly when the session ends.

## 3.3.4 - 2026-11-17

* Own leechcore.dll (RDMA / remote DMA, or a newer LeechCore): when the launcher says your leechcore.dll doesn't match the signed release, Use my leechcore.dll trusts exactly that file. Updates keep it, and the device line of your leechcore.ini (for example rma://127.0.0.1:19058) is used to connect. Any other change to the DLL is refused again. Hideway.exe --trust-leechcore does the same without the launcher.

## 3.3.3 - 2026-11-17

* DMA: reads don't wait on memory Windows has paged out anymore, and vmm's background refresh is replaced by a light refresh every 4 seconds. This is aimed at the short periodic freezes of the ESP.
* If the game's image can't be found, the other directory table bases are tried before giving up.
* The game PC's physical memory map is saved once (memmap.txt next to the exe) and used from the next start.
* New option: Read keys from the game PC (Aimbot page, off by default). The aim key and trigger key can be any key of the game PC's own keyboard. The log says whether the key table was found.
* Weapons page: each class can turn the triggerbot on or off and use its own trigger delay (with Override on).
* Smooth skeleton and Animate frozen limbs left the menu. Both stay on.

## 3.3.2 - 2026-11-17

* Team ID colours: every squad on screen gets its own clearly different colour from a fixed palette, no more same or look-alike colours.
* Aim and trigger hold during a short read stall and ramp back in smoothly when fresh data returns, instead of overshooting.
* Includes everything from 3.3.1: the wall and build fix, live weapon ballistics, per-tick health bars and the aim ease-in.

## 3.3.1 - 2026-11-16

* Walls and builds: aim and trigger stop when the game's own crosshair trace ends in front of the target (a wall or a build a player placed). It's only used once that trace has proven reliable.
* The trigger also accepts the game's hit point on the hitbox you chose.
* Includes live weapon ballistics, per-tick health bars within 60 m and the aim ease-in from 3.2.8 to 3.3.0.
* Not confirmed on a real match yet. Look for RETICLE and BALLISTICS lines in the log.

## 3.3.0 - 2026-11-16

* Prediction: the aim reads the real projectile speed and drop of the weapon in your hand from the game. It's found automatically and was confirmed on two different weapons. The class numbers stay as a fallback, and hit-scan weapons get no travel-time lead.
* Health and shield bars update every tick within 60 m.
* The aim eases in on new targets.
* Not confirmed on a real match yet. Look for BALLISTICS lines in the log.

## 3.2.9 - 2026-11-16

* Health and shield bars: players within 60 m are read on every tick instead of every 150 ms, so bars follow a fight without stepping.
* The aim ease-in from 3.2.8 stays.
* Enemy health is still only shown when the game sends it, which it usually doesn't for enemies.

## 3.2.8 - 2026-11-16

* Aimbot: it eases in on a new target now. It starts gently instead of taking its biggest step at once, with about 30% less peak acceleration and no overshoot. It arrives roughly 40 ms later.
* The input delay compensation from 3.2.5 is unchanged.
* Checked on a real recording: leading the target by the input delay didn't improve tracking, so prediction is unchanged.

## 3.2.7 - 2026-11-15

* Skeleton: the arms and legs of far and hidden players are interpolated through the real poses, so they swing continuously instead of holding one pose and jumping to the next. Mid-range and far players get their pose read more often (every 10 and 18 ms instead of 14 and 28).
* New option: Animate frozen limbs (Visuals, Skeleton, on by default). Fortnite only animates the players it draws, so a hidden player who runs keeps one pose. Their arms and legs now swing in a running cycle while the game's pose is frozen. Drawing only, aim and trigger always use the real pose.
* Fortnite 43.10 game data unchanged.

## 3.2.6 - 2026-11-15

* Fixed: Hideway no longer locks itself about an hour into a session. When KeyAuth stopped knowing the session it answered the license check without a signature, and that ended the session (locked: sig_missing in the log). Now Hideway opens a fresh session with your license, and an answer it can't verify gets the same grace period as a lost connection.
* Demo mode: the Team ID badges show again.
* Fortnite 43.10 game data unchanged.

## 3.2.5 - 2026-11-14

* Aimbot: no more jolts. The camera answers a mouse move about 50 ms late (measured on a real match) and the aim loop kept correcting an error it had already corrected. It now subtracts the movement still in flight. In a simulation the old loop overshot a 10 degree target by 1.1 to 3.9 degrees depending on the smoothing, the new one by 0.
* ESP: bots use the normal hidden (pink) and visible (green) colours like everyone else, plus a small BOT tag, so you can read the visibility check on them. A hidden bot used to be orange-yellow.
* Fortnite 43.10 game data unchanged.

## 3.2.4 - 2026-11-13

* Aim and trigger lead: the velocity used to aim ahead of a moving player is smoothed (40 ms), so the aim point doesn't jump with every network update. About 8 times less jolt in the air and on the ground in a measured 15-minute match, with the same prediction accuracy.
* ESP smoothness is Balanced by default again (it had been forced to Responsive).
* Fortnite 43.10 game data unchanged.

## 3.2.3 - 2026-11-13

* ESP lag fix: at match start (bus, skydive, teleport) the reader doesn't drop to slow one-by-one reads (300+ ms per tick) anymore. It keeps the fast path and re-checks after 3 seconds instead of 20 to 120.
* The ESP doesn't blank when one player-list read fails. It re-reads at once and keeps the players on screen for up to 1.5 seconds.
* A player standing close in front of you isn't dropped anymore (the head is checked as well as the waist).
* On a slow link the ESP keeps players on screen between reads (the age and extrapolation limits follow the measured read interval).
* Fortnite 43.10 game data unchanged.

## 3.2.2 - 2026-11-12

* Fixed: bots show the visible colour when you can see them. They were always the bot colour, so the visibility check looked dead in bot lobbies.
* Fortnite 43.10 game data unchanged from 3.2.1.

## 3.2.1 - 2026-11-12

* Fortnite 43.10 (CL-60118918): new game data (classes and offsets), not verified in a live match yet. Auto-update game data can still replace it with a signed pack.
* Wardogs v1.00 module in the launcher (ESP, radar, nearby-enemy warning, black fuser window, web radar, aim assist through MAKCU / Ferrum / KMBox NET).
* The download site moved to download.hideway.cc.

## 3.2.0 - 2026-11-12

* New game: Wardogs (v1.00) in the launcher. ESP with boxes, skeleton, names, distance, off-screen arrows, radar and a nearby-enemy warning.
* Wardogs also has a black fuser window, a web radar / tactical map for a phone or second screen, and aim assist through MAKCU / Ferrum / KMBox NET.
* The menu, logo and KeyAuth sign-in are shared with the Fortnite build.

## 3.1.0 - 2026-11-09

* One simple menu: no Simple/Advanced mode, one list.
* Automatic now (not in the menu): gun-in-hand rule, aim between bones, UE5 visibility, trigger source, per-weapon ballistics, smooth ESP, engine switches, weapon detection.
* Humanizing is one switch.
* Aim calibration measures counts per degree by itself.
* Assist page is now Triggerbot; close aim, sticky aim and prediction moved to Aimbot.
* One Loot card.
* Updates are only in the launcher.

## 3.0.0 - 2026-11-08

* Customer care update. The launcher has a new Help page: report a problem in one click with your diagnostics attached, and read the answer of support in the same place. The overlay's Debug page can send a report too.
* A help page on the web lets you check your license and move it to a new PC yourself. Announcements from support show in the launcher and the overlay.
* New Team panel (your squadmates' health, shield, weapon and distance) and a Radar auto range option.

## 2.10.10 - 2026-11-07

* New Black box on the Debug page: it keeps the last minute of what the overlay had and drew (counts only, no names or positions). Copy it or save it to a file and send it to support.
* If the ESP goes blank for more than half a second, Hideway now logs the reason and saves that minute by itself.

## 2.10.9 - 2026-11-07

* Fix: the Web radar names option now works. In 2.10.8 it was ignored, so player names were always sent to the web radar and to the online share even when it was switched off.
* If you use Share radar online with names off, update now.

## 2.10.8 - 2026-11-07

* Share radar online: a friend on another network can now open your web radar. Turn it on in the Radar page, press Copy online link and send it. It is off by default, and New online link cuts everyone off.
* The local radar link is easier to use: Allow other devices (LAN) is visible in Simple mode, and the Radar page says which link works where.

## 2.10.7 - 2026-11-07

* The launcher now greets you: a short welcome with three setup steps the first time, and after each update a What's new message with the changes and a support link.
* Nothing changes in the game overlay in this version.

## 2.10.6 - 2026-11-07

* Calmer look across the launcher sign-in screen and the website: flat dark design, one accent colour, no glow or orbiting effects, plainer wording.
* The sign-in screen now shows the logo, the name and three plain facts, and the home page text is simpler.

## 2.10.5 - 2026-11-07

* New launcher look: a flat dark design with a sidebar, a top bar showing live Server / DMA card / Input device status, and a Your library page with search (Ctrl+K), All / Installed / Coming soon tabs and product cards.
* Signed files status with a shield on every card, a refresh button for the checks, and the same style on every launcher page.

## 2.10.4 - 2026-11-07

* The wall check now sees the walls and floors you build: new pieces are picked up within about a second, edited pieces are re-read and destroyed ones are removed, so aim and trigger no longer pick a player standing behind your own wall.
* Debug page: the Wall check row shows how many player builds were placed.

## 2.10.3 - 2026-11-07

* Fix: the Team ID badge no longer disappears for members of a squad. A team number now counts as a squad for the whole match, even while a squadmate is out of range.
* Fix: your own team number no longer blinks to 0 about one frame in ten, so your real teammates are never treated as enemies by the team check, the ESP colours or the radar.
* Radar: view cone, height arrows, squad colours, movement direction ticks, an N marker, an optional team number, dim dots beyond the range and a better draw order (RADAR page, READABILITY card).
* Game data updates after a Fortnite patch: Hideway can fetch a pack of new offsets signed by Hideway, install it only when your game is not found with your current files, check it against the running game and go back to your previous files if it does not work (MISC page, GAME DATA card; switch: Auto-update game data).

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
