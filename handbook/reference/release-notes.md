# Release notes

Newest first. This is the same text the launcher shows under **Updates > What's new**.


## 3.7.0 - 2026-11-22

* **One-click support bundle.** **Debug > SUPPORT > Create support bundle** (and the launcher's **System > Support bundle**, which now uses the same code) writes one zip on your Desktop: system facts, your settings without COM port or IP, the last 2 MB of the logs, this session's log, the black box of the last minute and your newest saved dumps, the controller report and the memory map. **Create it with the newest recording** adds the newest recording. The Windows user name and profile folder are removed from every text and no key is ever in these files.
* **The black box sees overlay hitches.** A new **frame(ms)** column holds the longest overlay frame of every half second, and a log line (**OVERLAY**, at most once a minute) says when at least 5 frames took over 20 ms and over 2.5 times the usual. A box that freezes for 30 ms is a hitch of the overlay, not of the data, and until now nothing told the two apart.
* **Enemy counter (new, off by default).** A bar at the top of the screen: enemies within 50, 150 and 300 m, how many are down, and how far the nearest one is. Visuals > HUD.
* **Tests.** New zip writer, checked by an independent reader and by .NET's own ZipFile; support bundle, redaction and black box frame pacing are covered.

## 3.6.2 - 2026-11-22

* **The Aim bone choice works again.** Since the one-menu release (3.1.0) *Aim between bones* was forced on and it overrode the choice for every player with a readable skeleton: whatever the dropdown said (also the per-weapon ones and Close aim bone), the aim went to the point of the body nearest to the crosshair and never to the head. Now **Head, Neck, Chest and Pelvis** aim at that part (the head a little above its joint, where the game counts a head hit) and **Closest bone** keeps the old behaviour (the nearest point of the body, between the joints). A chosen part that is behind a wall falls back to the nearest exposed part of the body, so a player peeking with only an arm showing is still followed.
* **Things to know.** The Field of view is measured to the chosen part: at close range the head sits far above the chest, so a small field of view may not engage there; use Close aim, a bigger field of view or Closest bone. If you liked the old feel, pick **Closest bone**; the factory choice stays Head.

## 3.6.1 - 2026-11-21

* **Boxes no longer flash between the hidden and the visible colour.** The game's *drawn recently* flag blinks (about 1000 flips for the players in view in a recorded 30-minute match, half of the hidden stretches shorter than 250 ms), and every blink turned the box, skeleton and text white and green again. A player that was visible a moment ago now keeps the visible colour for 150 ms after the flag drops; hidden to visible is never delayed. Only the colour changes: the aim and the triggerbot read the flag themselves.

## 3.6.0 - 2026-11-21

* **No more ESP that vanishes because of the distance.** The usual cause of an enemy disappearing for a few seconds was **Render distance**: a saved value of 150 m left out every enemy farther away, even though Hideway was reading them. The default is now **500 m**, a config saved with a value under 250 m is raised **once** to 400 m (the log says so), and the new **Far markers** option (on by default) draws a small marker with the distance on any player beyond Render distance, up to 1500 m, so nobody simply vanishes.
* **Health bars: steadier, and honest about what the game sends.** On a 30-minute recording of a real match (282 players) the game never updated an enemy's health: the only enemies with numbers were knocked players (0 to 1 hp), teammates that were flagged as enemies for a moment when a match changed, and a few values frozen at first sight (30 hp for the whole match, for instance). That is why enemy bars show up about once in ten: there is nothing to read for the other nine. When the game stops sending a player's health after a real read, the bar now keeps the **last real value, dimmed** (a ~ in front of the number) for 12 s for a teammate and 10 s for an enemy, instead of blinking in and out. A knocked or dying player never keeps one, and nothing is invented: no real value, no bar.
* **Head volume.** The game's own trace hits a head up to about 16 cm above the head joint, so a head area centred on the joint sat too low. The aim's skeleton now reaches 14 cm above the head joint (the aim goes to the point of the body nearest to your crosshair, so it follows the crosshair up the head), a single-bone Head point sits 3 cm above the joint, and the triggerbot's head area is a 13 cm sphere around that point.
* **Aim: the lock survives a blink.** In a recorded 30-minute match the game's "drawn recently" flag of an enemy right next to the crosshair flipped about 210 times, and half of its visible stretches lasted under 250 ms. With **Visible only** each blink dropped the lock (no movement while it lasted) and the ease-in started again from zero when the enemy was back, so the aim stuttered. The locked enemy now stays eligible for 200 ms after the flag was last true (the wall check and the game's own crosshair trace still veto a real wall), and when nobody qualifies for a moment the lock and the ease-in progress are kept for 300 ms. On that recording this removes about a third of the lock restarts.
* **Controller on the game PC: the key table is found by what is in it.** The first live report showed the search by surroundings missing the table and accepting an empty one of another object. Hideway now accepts an array only if its elements are keys whose names it can read (*Gamepad Right Trigger*, *Left Mouse Button*...), checks every array of the object, and learns which byte means *pressed* from the keys you press while the card is open. The report gameinput_debug.txt lists every array it looked at, the raw bytes of the first keys and what was learned.
* **Black box.** Two new columns, **far** (far markers drawn) and **seen** (enemies the game itself rendered on screen), and a new log line when the game renders enemies on screen while the ESP draws none for a second (*REAL*): that is a true disappearance, not an enemy out of view. Normal blank spells (everybody listed is behind you or outside the view, the lobby, the end of a match) are no longer written to the log one by one - a live log had 170 of them in 50 minutes - and no longer use up the 3 automatic saves per run: only a real disappearance is saved to the **blackbox** folder.
* The HEALTH probe lines now also print the pawn damage counters, the health-bar object and the local damage dealt, read-only, to look for any other source of enemy health.

## 3.5.0 - 2026-11-19

* **A controller that is only plugged into the game PC now works.** Hideway reads the game's own input table through the DMA card, so the **Aim key** and **Trigger key** can be a button of a controller that only the game PC sees (Ferrum or MAKCU, no XIM, no adapter): click the box, then press the button on the controller (the box says *key or pad*). The CONTROLLER card on the Aimbot page shows **Game PC pad: readable** and, live, the keys held in the game (**Held in game**).
* **Aim activation.** New option: **Aim key**, **Aiming down sights** or **Key or aiming down sights**. With the second one the aim follows what the game says (you hold LT / right mouse), whatever the controller is.

## 3.4.0 - 2026-11-19

* **CONTROLLER card (Aimbot page).** Shows the pads Windows sees on the overlay PC and the buttons held right now, and has the **Trigger pull** slider for LT / RT when a trigger is your Aim key or Trigger key.

## 3.3.8 - 2026-11-18

* **Controller buttons as aim and trigger keys.** Click the **Aim key** or **Trigger key** box and press a controller button (A, B, X, Y, LB, RB, LT, RT, the stick clicks, Back, Start or the D-pad). It works with an Xbox pad, or any pad Windows shows as one, connected to the **overlay PC**. A pad that is only plugged into the game PC cannot be read from here.
* **RDMA and other custom devices start the plain way.** With your own leechcore.dll and a device= line, Hideway no longer uses the FPGA shortcuts (no refresh shortcut, no memory map): vmm refreshes the way it always did, so players stop disappearing now and then. The FPGA card keeps the fast start.

## 3.3.7 - 2026-11-18

* **Account panel.** Click the license row at the bottom of the launcher: it shows your account, plan and end date, and **Add a key** adds another license key to your account (renew early or stack time). **Buy or renew a key** opens the shop and **Sign out** is there too.
* **Expiry warning.** When your license ends within 7 days the launcher shows a banner with **Renew** and **Add a key**, and the end date turns orange (red under 3 days).
* **Forgot password?** on the sign-in screen opens the Discord support so you can get it reset.
* **Pause switch for updates.** If a release has a problem the publisher can put it on hold: launchers that have not installed it yet stop installing it by themselves and the Updates page says why. A fixed version (a new number) lifts it by itself.

## 3.3.6 - 2026-11-18

* **Automatic updates.** When the launcher starts it installs a newer signed version by itself: an Updating Hideway screen with the download, then the launcher restarts on the new version. A version that does not start is rolled back. Settings > Install updates automatically turns it off.
* A release found later in a long session waits for the next start, a running game is never interrupted, and a failed install is not retried in a loop (6 hours).
* The installer now waits a few seconds for the health report when the new version hands over to an elevated copy of itself.

## 3.3.5 - 2026-11-18

* New sign-in screen in the launcher: **Sign in** with a username and password, **Create account** with a license key (one key makes one account), or the old **License key** tab. Clear messages (wrong password, username taken, key already used), an inline show/hide for secrets, and a short wait after 5 refused attempts in a minute.
* The launcher shows who is signed in (rail and Settings), and Hideway.exe has the same account sign-in on its own start-up window.
* Footer links (Website, Discord, Customer panel) on the sign-in screen. A remembered account is stored encrypted like a key and renewed silently when the session ends.

## 3.3.4 - 2026-11-17

* Own leechcore.dll (RDMA / remote DMA, or a newer LeechCore): when the launcher card says leechcore.dll does not match the signed release, **Use my leechcore.dll** trusts exactly that file. Hideway.exe --trust-leechcore does the same without the launcher. The file is then kept by updates, and the device line of your leechcore.ini (for example rma://127.0.0.1:19058) is used for the connection. Any other change to the DLL is refused again.
## 3.3.3 - 2026-11-17

* DMA: reads no longer wait on memory that Windows has paged out, and vmm's background refresh is replaced by a light manual refresh every 4 seconds. This is aimed at the short periodic freezes of the ESP.
* If the game's image cannot be found, the other directory table bases are tried before giving up.
* The physical memory map of the game PC is saved once (memmap.txt next to the exe) and used from the next start.
* New option Read keys from the game PC (Aimbot page, off by default): the aim key and the trigger key can be any key of the game PC's own keyboard. The log says whether the key table was found.
* Weapons page: each class can switch the triggerbot on or off and use its own trigger delay (with Override on).
* Smooth skeleton and Animate frozen limbs are no longer in the menu; both stay on.
## 3.3.2 - 2026-11-17

* Team ID colours: every squad on screen now gets its own clearly different colour from a fixed palette (no more same or look-alike colours).
* Aim and trigger hold during a short read stall and ramp back in smoothly when fresh data returns, instead of overshooting. 3.3.1 wall and build fix, live weapon ballistics, per-tick health bars and aim ease-in included.

## 3.3.1 - 2026-11-16

* Walls and builds: aim and trigger now stop when the game own crosshair trace ends in front of the target (a wall or a build placed by a player), used only once that trace has proven reliable.
* Trigger also accepts the game hit point on the chosen hitbox.
* Live weapon ballistics, per-tick health bars within 60 m and aim ease-in from 3.2.8 to 3.3.0 included.
* Not yet confirmed on a real match: look for RETICLE and BALLISTICS lines in the log.

## 3.3.0 - 2026-11-16

* Prediction: the aim now reads the real projectile speed and drop of the weapon in your hand from the game (found automatically, confirmed on two different weapons, class numbers kept as fallback; hit-scan weapons get no travel-time lead).
* Health and shield bars update every tick within 60 m.
* Aim ease-in on new targets.
* Not yet confirmed on a real match: look for BALLISTICS lines in the log.

## 3.2.9 - 2026-11-16

* Health and shield bars: players within 60 m now have their health and shield read on every tick instead of every 150 ms, so bars follow a fight without stepping.
* Aim ease-in from 3.2.8 kept.
* Enemy health is still only shown when the game sends it (it usually does not for enemies).

## 3.2.8 - 2026-11-16

* Aimbot: the aim now eases in on a new target (starts gently instead of with its biggest step at once, about 30 percent less peak acceleration, no overshoot, arrives roughly 40 ms later).
* Input delay compensation from 3.2.5 unchanged.
* Checked against a real recording: leading the target by the input delay did not improve tracking, so prediction is unchanged.

## 3.2.7 - 2026-11-15

* Skeleton: the arms and legs of far and hidden players are shown interpolated through the real poses, so they swing continuously instead of holding one pose and jumping to the next. Poses of mid-range and far players are read more often (every 10 and 18 ms instead of 14 and 28)
* New option Animate frozen limbs (Visuals, Skeleton; on by default): Fortnite only animates the players it draws, so a hidden player that runs keeps one pose. Its arms and legs now swing in a running cycle for as long as the game's own pose is frozen. Drawing only: aim and trigger always use the real pose
* Fortnite 43.10 game data unchanged

## 3.2.6 - 2026-11-15

* Fix: the program no longer locks itself about an hour into a session. When KeyAuth stops knowing the session it answers the license check without a signature, and that answer used to end the session (locked: sig_missing in the log). Hideway now opens a fresh session with your license, and an answer that cannot be verified gets the same grace period as a lost connection
* Demo mode: the Team ID badges show again
* Fortnite 43.10 game data unchanged

## 3.2.5 - 2026-11-14

* Aimbot: no more jolts. The camera answers a mouse move about 50 ms late (measured on a real match) and the aim loop kept re-correcting an error it had already corrected; it now subtracts the motion still in flight. In a simulation the old loop overshot a 10 degree target by 1.1 to 3.9 degrees depending on the smoothing, the new one by 0
* ESP: bots use the normal hidden (pink) / visible (green) colours like everybody else and carry a small BOT tag, so the visibility check can be read on them (a hidden bot used to be orange-yellow)
* Fortnite 43.10 game data unchanged

## 3.2.4 - 2026-11-13

* Aim and trigger lead: the velocity used to aim ahead of a moving player is smoothed (40 ms), so the aim point no longer jumps with every network update - about 8x less jolt in the air and on the ground in a measured 15-minute match, with the same prediction accuracy
* ESP smoothness is Balanced by default again (it was forced to Responsive)
* Fortnite 43.10 game data unchanged

## 3.2.3 - 2026-11-13

* ESP lag fix: the reader no longer drops to slow one-by-one reads (300+ ms per tick) at match start when the bus, a skydive or a teleport moves players; it keeps the fast path and re-checks after 3 s instead of 20-120 s
* ESP no longer blanks when one player-list read fails: it is re-read at once and the players stay on screen for up to 1.5 s
* ESP no longer drops a player standing close in front of you (the head is checked as well as the waist)
* On a slow link the ESP keeps players on screen between reads (age and extrapolation limits follow the measured read interval)
* Fortnite 43.10 game data unchanged

## 3.2.2 - 2026-11-12

* Fix: bots now show the 'visible' colour when you can see them (they were always the bot colour, so the visibility check looked dead in bot lobbies)
* Fortnite 43.10 game data unchanged from 3.2.1

## 3.2.1 - 2026-11-12

* Fortnite 43.10 (CL-60118918): new game data (classes and offsets) - not verified in a live match yet; Auto-update game data can still replace it with a signed pack
* Wardogs v1.00 module in the launcher (ESP, radar, nearby-enemy warning, black fuser window, web radar, aim assist through MAKCU / Ferrum / KMBox NET)
* Download site moved to download.hideway.cc

## 3.2.0 - 2026-11-12

* New game: Wardogs (v1.00) in the launcher - ESP with boxes, skeleton, names, distance, off-screen arrows, radar, nearby-enemy warning
* Wardogs: black fuser window, web radar / tactical map for a phone or second screen, aim assist through MAKCU / Ferrum / KMBox NET
* Hideway menu, logo and KeyAuth sign-in shared with the Fortnite build

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
