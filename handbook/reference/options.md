# Options reference

Every option of Hideway, taken from the program's own option list. The text in the last column is the same text you see when you rest the cursor on a row in the menu. Colours are picked in the menu, so they show "(see menu)" instead of a default.

{% hint style="info" %}
The menu is all-in-one: every option below is on its page. Type in the search box at the top of the menu to jump to one.
{% endhint %}

## Aimbot

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable aimbot** | on / off | off |  | Master switch for aim assist. It moves the mouse through your input device, so a connected and verified device is required (Misc > Input device). |
| **Aim key** | key | Mouse 2 |  | Hold this key to aim. Click the box, then press a key or mouse button; click the box a second time to use Mouse 1 (left button). Right-click the box to clear it. |
| **Aim bone** | choice | Head | Head / Neck / Chest / Pelvis / Closest bone | Which part of the target to aim at. 'Closest bone' picks whichever joint is nearest to your crosshair. |
| **Aim between bones** | on / off | off |  | Aim at the point on the skeleton (any bone segment) that is closest to the crosshair instead of one joint. Skips segments behind a wall when Visible only is on. |
| **Field of view** | whole number | 60 | 1 to 180 | Only targets inside this cone around your crosshair are considered. Smaller = more selective. |
| **Smoothing** | number | 10. | 1. to 100. | How slowly the aim closes the gap. 1 = instant, higher = slower and less obvious. |
| **Max aim distance** | number | 150. | 5. to 500. | Targets further away than this are ignored. |
| **Team check** | on / off | on |  | Never aim at teammates. |
| **Visible only** | on / off | on |  | Only aim at targets that are visible (not behind walls). Visibility is judged by Raycast VisCheck against the level geometry; until the geometry has been read (a few seconds after a match starts) aim waits. |
| **Ignore knocked** | on / off | off |  | Skip downed players. |
| **Only with a gun in hand** | on / off | on |  | Aim and trigger stay off while you hold a build piece, the pickaxe or an empty weapon. This is what lets you place a wall with Mouse 1 as the aim key without the aim locking onto someone through it. Judged from the held item's ammo count; if the game's weapon cannot be read, aim keeps working. |
| **Prefer standing targets** | on / off | on |  | Standing players are chosen before downed ones. |
| **Target priority** | choice | Closest to crosshair | Closest to crosshair / Closest distance | How the best target is chosen: closest to the crosshair, or closest in distance. |
| **Lock until key release** | on / off | off |  | Stay on the first target until you let go of the aim key, even if another one gets closer. |
| **Dead zone** | number | 0.15 | 0. to 3. | Inside this angle the aim stops moving, so it does not shake when already on target. |
| **Target line** | on / off | on |  | Draw a line from the crosshair to the current target. |
| **Ignore bots** | on / off | off |  | Skip AI-controlled players. |
| **Draw aim FOV** | on / off | on |  | Draw the aim cone as a circle on screen. |
| **FOV circle color** | colour | (see menu) |  | Colour of the aim circle. |
| **Reaction delay** | number | 0. | 0. to 1000. | Wait this long after a target appears before starting to aim. |
| **Target switch delay** | number | 0. | 0. to 1000. | Minimum time on a target before the aim may switch to a better one. |
| **Humanizing** | on / off | off |  | Adds small natural variation to the speed of the aim movement. |
| **Jitter** | number | 0. | 0. to 10. | Adds a little random shake to each mouse step. |
| **Miss chance** | number | 0. | 0. to 100. | Percentage of the time the aim deliberately lands slightly off target. |
| **Deceleration** | number | 0. | 0. to 10. | Slows the aim down as it approaches the target. Higher = softer landing. |
| **Step limit** | whole number | 0 | 0 to 100 | Maximum mouse counts sent per step (0 = no limit). |
| **Random smoothing** | on / off | off |  | Re-rolls the smoothing between the min and max values every quarter second. |
| **Random smooth min** | number | 4. | 1. to 100. | Lowest smoothing value used by random smoothing. |
| **Random smooth max** | number | 12. | 1. to 100. | Highest smoothing value used by random smoothing. |
| **Dynamic smoothing** | on / off | off |  | Close targets are followed a little slower than distant ones. |
| **Dynamic max distance** | number | 100. | 10. to 500. | Distance at which dynamic smoothing stops having an effect. |
| **Counts per degree X** | number | 10. | 1. to 60. | Mouse counts that turn the view by one degree horizontally. Tune until the aim lands exactly on target. |
| **Counts per degree Y** | number | 10. | 1. to 60. | Mouse counts that turn the view by one degree vertically. |

## Weapons (per-class overrides)

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Pistol anim id** | whole number | 1 | 0 to 40 | Raw weapon animation id the game reports for pistols. Only change it if the Debug page shows another id for the weapon you hold. |
| **Shotgun anim id** | whole number | 2 | 0 to 40 | Raw weapon animation id the game reports for shotguns. Only change it if the Debug page shows another id for the weapon you hold. |
| **Rifle anim id** | whole number | 4 | 0 to 40 | Raw weapon animation id the game reports for rifles. Only change it if the Debug page shows another id for the weapon you hold. |
| **SMG anim id** | whole number | 5 | 0 to 40 | Raw weapon animation id the game reports for SMGs. Only change it if the Debug page shows another id for the weapon you hold. |
| **Sniper anim id** | whole number | 6 | 0 to 40 | Raw weapon animation id the game reports for sniper rifles. Only change it if the Debug page shows another id for the weapon you hold. |

## Triggerbot, close aim, sticky aim, prediction

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable triggerbot** | on / off | off |  | Fires automatically while an enemy is under the crosshair (needs a verified input device). |
| **Trigger key** | key | Mouse 5 |  | Key that activates the triggerbot in 'Hold key' mode. |
| **Trigger mode** | choice | Hold key | Hold key / Always on / Toggle key | Hold key: active only while the key is down. Always on: active all the time. Toggle key: press the key once to arm the trigger, again to disarm it. |
| **Trigger hitbox** | choice | Upper body | Head only / Upper body / Whole body | Which part of the target must be under the crosshair. |
| **Trigger delay** | number | 40. | 0. to 500. | Wait this long after an enemy is under the crosshair before firing. |
| **Trigger hold time** | number | 45. | 10. to 300. | How long each shot is held. |
| **Trigger max distance** | number | 60. | 5. to 300. | Do not fire at targets further away than this. |
| **Trigger team check** | on / off | on |  | Never fire at teammates. |
| **Trigger ignore knocked** | on / off | on |  | Do not fire at downed players. |
| **Trigger ignore bots** | on / off | off |  | Do not fire at AI-controlled players. |
| **Trigger visible only** | on / off | on |  | The triggerbot only fires at a visible player: the exact hitbox point under the crosshair must have nothing solid in front of it (Raycast VisCheck). Off = fires at anyone under the crosshair, even through a wall. |
| **Trigger source** | choice | Both (strictest) | Game target (UE5) / Crosshair geometry / Both (strictest) | Game target (UE5): fire when the game's own crosshair trace (TargetedFortPawn) says a player is under it - the engine already accounts for walls. Crosshair geometry: our own hitbox test on the predicted skeleton. Both: the game target AND the hitbox must agree (strictest, default). If the game target cannot be read it falls back to geometry and the Assist page says so. |
| **Trigger lead** | number | 0. | 0. to 150. | Advance the target by its velocity x this many ms before the hitbox test (geometry modes), to hit moving players despite the click delay. |
| **Trigger confirm frames** | whole number | 1 | 1 to 6 | The same player must be a valid target for this many consecutive checks before the shot is armed. 1 = instant. |
| **Trigger hold on target** | on / off | off |  | Keep the button held while the target stays valid (full-auto weapons) instead of one timed click. Safety stop after 1.5 s. |
| **Trigger shotgun range** | number | 25. | 5. to 100. | While a shotgun is equipped, never fire at targets further than this (the general max distance still applies too). |
| **Trigger reaction spread** | number | 8. | 0. to 60. | How much the reaction time varies around Trigger delay. Most reactions land close to the delay, a few are slower (never faster). 0 = always exactly the delay. |
| **Trigger pause in menu** | on / off | on |  | Never fire while the Hideway menu is open or panic is active, so a click can not be sent into the menu or the game by accident. |
| **Trigger indicator** | on / off | on |  | A small ring at the crosshair: it fills while the trigger waits out its delay and turns green while the button is down. Drawn only while the trigger is working on a target. |
| **Close aim** | on / off | off |  | Uses a different field of view, smoothing and bone for enemies within a short range. |
| **Close aim range** | number | 12. | 2. to 50. | Distance under which the close-aim settings apply. |
| **Close aim FOV** | whole number | 30 | 1 to 180 | Aim cone used inside the close range. |
| **Close aim smoothing** | number | 6. | 1. to 50. | Smoothing used inside the close range. |
| **Close aim bone** | choice | Chest | Head / Neck / Chest / Pelvis / Closest bone | Aim bone used inside the close range. |
| **Sticky aim** | on / off | off |  | Once the crosshair is near a target the aim stays attached to it. |
| **Sticky activation radius** | number | 8. | 1. to 40. | How close (in degrees) the crosshair must be before sticky aim engages. |
| **Sticky max distance** | number | 40. | 5. to 200. | Sticky aim only works on targets closer than this. |
| **Sticky smoothing** | number | 10. | 1. to 60. | Smoothing used while sticky aim is attached. |
| **Sticky slippery** | number | 0. | 0. to 10. | Lets the aim slip a little off the target so it feels less rigid. |
| **Sticky off vs groups** | on / off | off |  | Turns sticky aim off when several enemies are nearby. |
| **Sticky group distance** | number | 40. | 5. to 200. | How close enemies must be to count as a group. |
| **Prediction** | on / off | off |  | Leads moving targets for projectile weapons using their velocity. |
| **Hitscan weapon** | on / off | off |  | The equipped weapon has no bullet travel time: prediction then only applies the Prediction lead, no projectile intercept or drop. |
| **Prediction lead** | number | 0. | 0. to 150. | Move the aim point along the target's velocity by this many ms, on top of the projectile intercept. Covers input + display latency; works for hitscan weapons too. Only active while Prediction is switched on. |
| **Per-weapon ballistics** | on / off | on |  | Use a separate projectile speed and gravity for the class of the weapon you hold (pistol, rifle, SMG, shotgun, sniper) instead of the single Projectile speed / gravity. The defaults are tuned starting values. Unknown weapon class = the single values. |
| **Pistol projectile speed** | number | 24000. | 5000. to 90000. | Bullet speed used for prediction while a pistol is held (Per-weapon ballistics on). |
| **Pistol projectile gravity** | number | 1.0 | 0. to 5. | Gravity factor (bullet drop) used for prediction while a pistol is held. |
| **Rifle projectile speed** | number | 28000. | 5000. to 90000. | Bullet speed used for prediction while a rifle is held (Per-weapon ballistics on). |
| **Rifle projectile gravity** | number | 1.2 | 0. to 5. | Gravity factor (bullet drop) used for prediction while a rifle is held. |
| **SMG projectile speed** | number | 28000. | 5000. to 90000. | Bullet speed used for prediction while an SMG is held (Per-weapon ballistics on). |
| **SMG projectile gravity** | number | 1.2 | 0. to 5. | Gravity factor (bullet drop) used for prediction while an SMG is held. |
| **Shotgun projectile speed** | number | 36000. | 5000. to 90000. | Bullet speed used for prediction while a shotgun is held (Per-weapon ballistics on). |
| **Shotgun projectile gravity** | number | 2.0 | 0. to 5. | Gravity factor (bullet drop) used for prediction while a shotgun is held. |
| **Sniper projectile speed** | number | 62000. | 5000. to 90000. | Bullet speed used for prediction while a sniper rifle is held (Per-weapon ballistics on). |
| **Sniper projectile gravity** | number | 3.5 | 0. to 5. | Gravity factor (bullet drop) used for prediction while a sniper rifle is held. |
| **Projectile speed** | number | 28000. | 5000. to 90000. | Speed of the projectile in cm/s, used to work out the lead. |
| **Projectile gravity** | number | 1.2 | 0. to 5. | Gravity scale of the projectile (0 = flies straight). |
| **Prediction dot** | on / off | off |  | Draw a dot where the prediction expects the target to be. |
| **Prediction dot size** | number | 3. | 1. to 10. | Size of that dot. |

## Loot ESP

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable loot ESP** | on / off | off |  | Draws the items lying on the ground (read-only, over DMA). The reader finds the game's own item layout live and draws nothing until it has proven it - see Debug -> LOOT READER and the LOOT lines in the log. Needs the wall check on (it provides the level layout). |
| **Loot max distance** | number | 100. | 10. to 500. | Do not draw items further away than this. |
| **Loot minimum rarity** | choice | Common | Common / Uncommon / Rare / Epic / Legendary / Mythic | Hide items below this rarity. Items whose rarity could not be read are always drawn (white). |
| **Loot weapons** | on / off | on |  | Show weapons (recognised by name). |
| **Loot ammo** | on / off | off |  | Show ammo (bullets, shells, rockets, arrows). |
| **Loot heals** | on / off | on |  | Show bandages, med kits and other healing items. |
| **Loot shields** | on / off | on |  | Show shield potions, Slurp Juice, Chug Jug. |
| **Loot grenades** | on / off | on |  | Show grenades and throwables. |
| **Loot materials** | on / off | off |  | Show wood, stone and metal. |
| **Loot traps** | on / off | off |  | Show traps. |
| **Loot other items** | on / off | off |  | Show every item that is none of the above. |
| **Show containers** | on / off | on |  | Chests, ammo boxes, coolers, llamas and similar: actors that carry a display name and are recognised as containers by it. The reader prints every display name it found in the log, so unknown ones can be added. |
| **Show vehicles** | on / off | on |  | Vehicles recognised by their display name; positions are refreshed every 0.7 s. |
| **Show other named actors** | on / off | off |  | Every other actor that has a display name (usually noise): for checking what the reader sees. |
| **Hide opened containers** | on / off | on |  | Hide containers that were already searched. The game's flag is not in the dump: the reader learns it by watching which bit flips on several containers when they are opened, so it only works after a few have been opened. |
| **Container max distance** | number | 150. | 10. to 600. | Do not draw containers further away than this. |
| **Vehicle max distance** | number | 300. | 30. to 1500. | Do not draw vehicles (and, when shown, other named actors) further away than this. Before this option existed they silently used three times the loot max distance; the default of 300 m is that value for the default loot distance of 100 m. |
| **Loot distance text** | on / off | on |  | Append the distance in metres to the item name. |
| **Loot marker** | on / off | on |  | A small diamond in the rarity colour at the item. |
| **Loot snaplines** | on / off | off |  | A line from the bottom of the screen to each item. |

## Reboot cards

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable reboot cards** | on / off | off |  | Marks the reboot cards of dead players (their squad can still bring them back): a ring at the place they died, the owner's nickname, the seconds left and the distance. Read-only. A card is only drawn after its numbers pass sanity checks; see Debug -> REBOOT CARDS and the REBOOT lines in the log. |
| **Spectator list** | on / off | off |  | Shows who is spectating you (names, bots marked) at the top left, and logs changes. Read-only. Config-file option: the layout it reads comes from a community post and is checked on every read, so it says so in the log when it does not match this build. |
| **Spectators: ignore teammates** | on / off | on |  | Spectator count, list and audio alert leave out players on your own team (a dead teammate watching you is not a threat). Teammates stay in the list, dimmed. Config-file option. |
| **Audio alerts** | on / off | off |  | Plays a short positional tone (left / right / distance) when an enemy comes inside the alert range, and when somebody starts spectating you. Config-file option, off by default. Tones are generated, no sound files. |
| **Audio alert volume** | whole number | 50 | 0 to 100 | Master volume of the alert tones, 0-100. |
| **Audio alert device** | whole number | -1 | -1 to 15 | Output device index for the alert tones (-1 = the Windows default). |
| **Audio alert range** | whole number | 50 | 10 to 200 | An enemy coming inside this distance (metres) plays the alert once; it re-arms when the enemy is 3 m farther than the range. |
| **Reboot card nickname** | on / off | on |  | Show the dead player's name. |
| **Reboot card time left** | on / off | on |  | Show the seconds left until the card expires (extrapolated between reads of the replicated world clock; hidden when the clock cannot be read). |
| **Reboot card distance** | on / off | on |  | Show the distance to the card in metres. |
| **Reboot card snaplines** | on / off | off |  | Draw a line from the bottom of the screen to each card. |
| **Reboot card max distance** | number | 400. | 20. to 1500. | Do not draw reboot cards further away than this. |

## Visuals

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable ESP** | on / off | on |  | Master switch for everything drawn on players. |
| **Show bots** | on / off | on |  | Also draw AI-controlled players. |
| **Show teammates** | on / off | off |  | Also draw your own team. |
| **Hide knocked players** | on / off | off |  | Do not draw players who are knocked down (off: they are drawn with the knocked colour). |
| **Render distance** | number | 300. | 10. to 1000. | Players further away than this are not drawn. |
| **Max ESP players** | whole number | 100 | 1 to 200 | Upper limit of players drawn at once (nearest first). |
| **Box style** | choice | Box | Off / Box / Corner box / 3D box | Off, a full box, or a box drawn only at the corners. |
| **Box thickness** | number | 1.5 | 0.5 to 5. | Line width of the box. |
| **Box rounding** | number | 2. | 0. to 20. | Corner roundness of the box. |
| **Box fill** | on / off | off |  | Fill the box with a transparent colour. |
| **Box gradient** | on / off | off |  | Fill the box with a vertical gradient instead of a flat colour. |
| **Box fill color** | colour | (see menu) |  | Colour (and transparency) of the filled part of the box when Box fill is on. |
| **Gradient top** | colour | (see menu) |  | Top colour of the box gradient. |
| **Gradient bottom** | colour | (see menu) |  | Bottom colour of the box gradient. |
| **Skeleton** | on / off | on |  | Draw the player's bones. |
| **Smooth skeleton** | on / off | on |  | Anchors the skeleton on the pelvis and glides pose changes over a few milliseconds, so limbs stop jittering when the game's root position steps with network updates. Off = the raw skeleton, shifted rigidly with the player. |
| **Skeleton thickness** | number | 1.2 | 0.5 to 5. | Line width of the bones. |
| **Distance-scaled lines** | on / off | on |  | Bones get thinner with distance so far players are not cluttered. |
| **Joint dots** | on / off | off |  | Draw a dot on every joint. |
| **Joint dot size** | number | 2.5 | 1. to 8. | Size of the dots drawn on the skeleton joints. |
| **Skeleton glow** | on / off | off |  | Soft glow behind the bones. |
| **Glow layers** | whole number | 3 | 1 to 6 | How many soft layers the skeleton glow is built from. More = softer, slightly more GPU work. |
| **Glow color** | colour | (see menu) |  | Colour of the skeleton glow. |
| **Head circle** | on / off | off |  | Draw a circle on the head. |
| **Head filled** | on / off | off |  | Fill the head circle. |
| **Head circle size** | number | 1. | 0.3 to 3. | Scales the head circle relative to the head size. |
| **Head circle offset** | number | 0. | -30. to 30. | Moves the head circle up (+) or down (-) in pixels to line it up with the head. |
| **Name** | on / off | on |  | Show the player's name. |
| **Distance** | on / off | on |  | Show the distance in metres. |
| **Weapon class** | on / off | off |  | Show the class of the weapon the player holds (rifle, SMG, shotgun...). |
| **Platform** | on / off | off |  | Show the player's platform (PC, Xbox, PlayStation...). |
| **Kill score** | on / off | off |  | Show the player's kills. |
| **Health + shield bars** | on / off | on |  | Bars next to the box: health and shield, read from the game. When the player's own numbers read empty, the copy kept in the player's state is used. If the game gives nothing at all, no bar is shown instead of an invented one. |
| **Health numbers** | on / off | off |  | Show health and shield as numbers (same rule: nothing is drawn when the game gives no value). |
| **Bar style** | choice | Classic | Classic / Segmented | Classic = plain bars. Segmented = the bars are split in four so you can read 25 / 50 / 75 % at a glance. |
| **Bar side** | choice | Left | Left / Right | Which side of the box the health and shield bars sit on. |
| **Damage trail** | on / off | on |  | The part of a bar that was just lost drains down slowly, so you can see how much damage a hit did. |
| **Team ID** | on / off | on |  | A small number before the name: the game's own team number. Everyone in the same duo / trio / squad carries the same number. |
| **Team ID only for squads** | on / off | on |  | Hide the number when nobody else has it (solo play), so it only shows on real teams. |
| **Team ID colours** | on / off | on |  | Give every team number its own colour, so a squad is easy to pick out in a crowd. |
| **Squad list** | on / off | off |  | A small panel at the top right: every other squad in range with its team number, members alive (and down) and the distance of the nearest one. |
| **Fade in players** | on / off | on |  | A player who comes into view fades in over a moment instead of popping onto the screen. |
| **Avoid overlapping labels** | on / off | on |  | Names and team numbers of players close together are lifted above each other so each stays readable. |
| **Match info** | on / off | on |  | Players left and teams left at the top of the screen, as the game counts them. Hidden when the game gives no sensible numbers (lobby). |
| **Low health highlight** | on / off | on |  | A pulsing red outline around an enemy whose health is below the threshold (only when a real health value was read). |
| **Low health threshold** | whole number | 35 | 10 to 80 | Health points under which the outline appears. |
| **Enemy ammo** | on / off | off |  | Rounds left in the weapon an enemy holds (read from the game; shown only when the weapon was read). |
| **Show debug page** | on / off | off |  | Adds the DEBUG page to the side bar. It shows raw readings and offsets; you do not need it for normal play. |
| **Auto-save config** | on / off | on |  | Writes the active config 2.5 seconds after your last change, and when the program closes. The old file is kept as a backup first (CONFIG > BACKUPS). Off = only Save config writes it. |
| **Next config key** | key | not set |  | Switches to the next config in the list (the one you leave is saved first when Auto-save is on). A small message shows the name. |
| **Previous config key** | key | not set |  | Switches to the previous config in the list. |
| **Snaplines** | choice | Off | Off / Bottom / Middle / Top | Lines from the screen edge or centre to every player. |
| **Snapline thickness** | number | 1. | 0.5 to 4. | Thickness of the snaplines in pixels. |
| **Off-screen arrows** | on / off | off |  | Arrows at the edge of the screen pointing to players you cannot see. |
| **Arrow radius** | whole number | 160 | 40 to 600 | Distance of the arrows from the screen centre. |
| **Crosshair** | on / off | off |  | Draw a crosshair in the centre of the screen. |
| **Crosshair size** | whole number | 9 | 2 to 40 | Size of the on-screen crosshair in pixels. |
| **Crosshair color** | colour | (see menu) |  | Colour of the on-screen crosshair. |
| **Fuser mode** | on / off | on |  | Opens a separate pure-black window under the overlay for capture-card fusers. Use the Overlay monitor setting to choose the screen. |
| **Fuser toggle key** | key | not set |  | Opens / closes the fuser window. |
| **Box color** | colour | (see menu) |  | Colour used for players you cannot currently see. |
| **Box color (visible)** | colour | (see menu) |  | Colour used for players the game is currently showing. |
| **Skeleton color** | colour | (see menu) |  | Skeleton colour for players you cannot see. |
| **Skeleton color (visible)** | colour | (see menu) |  | Skeleton colour for players the game says are visible. |
| **Text color** | colour | (see menu) |  | Text colour for players you cannot see. |
| **Text color (visible)** | colour | (see menu) |  | Text colour for players the game says are visible. |
| **Snapline color** | colour | (see menu) |  | Snapline colour for players you cannot see. |
| **Snapline color (visible)** | colour | (see menu) |  | Snapline colour for players the game says are visible. |
| **Arrow color** | colour | (see menu) |  | Colour of the off-screen arrows. |
| **Bot color** | colour | (see menu) |  | Colour used for bots (AI players) in the ESP. |
| **Knocked color** | colour | (see menu) |  | Colour used for knocked (downed) players. |
| **Teammate color** | colour | (see menu) |  | Colour used for teammates in the ESP. |
| **Highlight target** | on / off | on |  | Draw the player the aimbot is locked on (or the trigger is about to shoot) in its own colour, so you can see which player the assists picked. |
| **Target color** | colour | (see menu) |  | Colour of the highlighted target. It replaces the box, skeleton, text and snapline colours of that one player. |
| **Distance detail (LOD)** | on / off | on |  | Players farther than the LOD start distance are drawn with thinner lines and without joint dots, glow, weapon, platform and kill lines. Cleaner in a crowded lobby and cheaper to draw. |
| **Facing direction** | on / off | off |  | Draws a short line from each player's head along the direction the character looks, taken from the rotation of its mesh. Off by default: the mesh's forward axis is the Unreal convention and has not been measured on this game. |
| **LOD start distance** | number | 120. | 30. to 500. | Distance in metres beyond which a player is drawn with reduced detail. |

## Radar

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Enable radar** | on / off | on |  | Show the radar on screen. |
| **Radar shape** | choice | Circle | Square / Circle | Square or circle. |
| **Radar X** | whole number | 24 | 0 to 3840 | Horizontal position of the radar on the screen, in pixels from the left. |
| **Radar Y** | whole number | 64 | 0 to 2160 | Vertical position of the radar on the screen, in pixels from the top. |
| **Radar size** | whole number | 220 | 120 to 600 | Size of the radar in pixels. |
| **Radar range** | number | 120. | 20. to 600. | How far (in metres) the radar reaches. |
| **Radar min distance** | number | 0. | 0. to 100. | Radar: hide players closer than this (they are already on screen). |
| **Radar zoom** | number | 1. | 0.4 to 4. | Zoom multiplier for the radar. |
| **Rotate with view** | on / off | on |  | The radar turns with your camera so 'up' is always forward. Off: north stays up and your arrow turns with the camera. |
| **Draw center dot** | on / off | on |  | Radar: draw a dot at the centre (your position). |
| **Show local arrow** | on / off | on |  | Radar: draw the arrow that shows where you are looking. |
| **Radar dividers** | on / off | on |  | Radar: draw the cross and three range rings (1/3, 2/3 and full range), each labelled with its distance. |
| **Radar background** | on / off | on |  | Radar: draw the dark panel behind the dots. |
| **Radar border** | on / off | on |  | Radar: draw an outline around the radar. |
| **Radar distance text** | on / off | off |  | Radar: write the distance next to each dot. |
| **Clamp to edge** | on / off | on |  | Players beyond the radar range are pinned to its edge instead of disappearing. |
| **Radar teammates** | on / off | off |  | Radar: show teammates. |
| **Radar bots** | on / off | on |  | Radar: show bots. |
| **Radar knocked** | on / off | on |  | Radar: show knocked players. |
| **Radar background color** | colour | (see menu) |  | Colour (and transparency) of the radar panel. |
| **Radar divider color** | colour | (see menu) |  | Radar: colour of the cross and range-ring lines. |
| **Radar enemy color** | colour | (see menu) |  | Radar: colour of enemy players. |
| **Radar team color** | colour | (see menu) |  | Radar: colour of teammates. |
| **Radar bot color** | colour | (see menu) |  | Radar: colour of bots. |
| **Web radar** | on / off | off |  | Starts a small web server inside Hideway and shows the players on a radar in any browser: your phone, a tablet, a second monitor. Nothing goes to the internet (no cloud, no account): the page is served from this PC. Open the link from the Radar page (it contains your access key). Off by default. |
| **Allow other devices (LAN)** | on / off | off |  | On: phones and other PCs on your network can open the radar (Windows Firewall may ask to allow Hideway on private networks). Off: only this PC (127.0.0.1). |
| **Web radar port** | whole number | 8765 | 1024 to 65535 | TCP port of the radar page. Change it if another program already uses it (the Radar page tells you). |
| **Web radar rate** | whole number | 50 | 20 to 500 | How often the radar page gets new data. 50 ms = 20 updates per second; the page smooths the motion between updates by itself. |
| **Web radar names** | on / off | on |  | Off: player names are not sent to the radar page at all. |
| **Radar toggle key** | key | not set |  | Shows / hides the radar. |
| **Radar enlarge key** | key | not set |  | Makes the radar bigger while toggled. |

## Misc: system, keys, input device, DMA

| Option | Type | Default | Range / choices | What it does |
|---|---|---|---|---|
| **Notifications** | on / off | on |  | Show pop-up notices (connections, toggles, warnings). |
| **Notify feature toggles** | on / off | on |  | Show a notification when a feature is switched on or off with its key. |
| **Notify DMA state** | on / off | on |  | Show a notification when the DMA link connects, drops or recovers. |
| **Notify FPS drops** | on / off | off |  | Show a notification when the frame rate drops below the threshold. |
| **FPS drop threshold** | whole number | 30 | 5 to 120 | Show a notification when the overlay falls below this many frames per second. |
| **Watermark** | on / off | on |  | Show the small Hideway status badge. |
| **FPS limit** | on / off | off |  | Cap the overlay frame rate (use with VSync off). |
| **FPS limit value** | whole number | 120 | 30 to 500 | The cap, in frames per second. |
| **VSync** | on / off | on |  | Match the overlay to your display refresh rate for smooth drawing. |
| **Smooth ESP** | on / off | on |  | Moves players and the camera between data updates so boxes glide instead of stepping. Stale data is removed automatically. |
| **ESP smoothness** | choice | Balanced | Responsive / Balanced / Silky | Responsive = boxes follow every new reading at once (more visible steps). Balanced = default. Silky = corrections are absorbed more slowly: about a third less jitter in measured recordings, but the boxes sit a little further from the raw readings (a few cm). Needs Smooth ESP. |
| **Motion estimator** | on / off | on |  | One motion estimate per player (velocity, acceleration, confidence) shared by the ESP, aim lead and trigger lead. Follows strafes, stops and direction changes much more closely. Off = the previous constant-velocity model. |
| **Overlay monitor** | whole number | 1 | 1 to 8 | Which screen the overlay (and the fuser window) covers. |
| **Always on top** | on / off | on |  | Keep the overlay above other windows. |
| **Menu theme** | choice | Nebula | Nebula / Sakura / Glacier / Toxic / Ember / Mono / Chroma (cycles) / Custom | Colours of the whole menu. Chroma drifts through the colours; Custom uses the colour picker of the corner popup (the gear in the bottom-left). |
| **Menu animations** | on / off | on |  | Slow aurora, floating lights, the shimmer along the top edge and breathing halos. Off = still colours, a little lighter on the GPU. |
| **Menu accent** | colour | (see menu) |  | The colour of the Custom theme (also in the corner popup). Choosing a colour there switches the theme to Custom. |
| **Menu key** | key | Insert |  | Opens and closes this menu. |
| **Panic key** | key | not set |  | Instantly hides everything and stops reading the game. Press again to resume. |
| **Master toggle key** | key | not set |  | Turns all cheat features on or off without closing the menu. |
| **Exit key** | key | End |  | Closes Hideway. |
| **Enable input device** | on / off | off |  | Connect to a MAKCU, Ferrum or KMBox NET so aim and trigger can move the mouse. |
| **Device type** | choice | Auto-detect | Auto-detect / MAKCU / Ferrum / KMBox NET | Auto-detect finds a MAKCU or Ferrum on a serial port. KMBox NET connects over the network. |
| **Serial port** | text | empty |  | COM port of the device (for example COM3). Leave empty to auto-detect. |
| **Baud rate** | choice | Auto | Auto / 4000000 / 2000000 / 1000000 / 921600 / 115200 / 3000000 | Serial speed. Auto probes the usual rates, 4 Mbaud first. |
| **Auto reconnect** | on / off | on |  | Reconnect automatically if the device is unplugged or stops answering. |
| **Read game-PC mouse buttons** | on / off | on |  | Lets the input device (MAKCU / KMBox) report the mouse buttons of the GAME PC, so the aim and trigger keys work from the mouse you are actually holding, not only from the overlay PC. Hideway's own clicks are ignored. |
| **Kmbox IP** | text | 192.168.2.188 |  | IP address shown on the KMBox NET screen. |
| **Kmbox port** | text | 1234 |  | UDP port shown on the KMBox NET screen. |
| **Kmbox UUID** | text | 1234ABCD |  | 8-character code shown on the KMBox NET screen. |
| **Fast DMA reads (scatter)** | on / off | on |  | Reads many values from the game in one round trip. Hideway checks it against normal reads on live data and switches itself off if they disagree. |
| **Thin skeleton reads** | on / off | on |  | In crowded matches the card link is the bottleneck. Off-screen and distant players do not get a skeleton read every tick, and mid-range ones refresh their pose every 2nd-4th tick (the box keeps updating every tick). Turn off only to compare. |
| **Fast position refresh** | on / off | on |  | In a crowded match one full read of every player takes 15-20 ms. With this on, between two full reads Hideway re-reads only where everybody is (a few ms for 100 players), so boxes and skeletons move with data that is about half as old. Does nothing when the full read is already fast (small lobbies). Needs the high-rate camera lane. |
| **Wall check (ray-cast)** | on / off | on |  | Reads the level's collision geometry (used by Raycast VisCheck and by the loot reader). |
| **DMA stall guard** | on / off | on |  | MemProcFS refreshes its process list in the background and every read waits for it: on this setup a 105 ms freeze every ~10 s, which shows up as a box lag blip. With the guard on that refresh is paused and done by hand only when the game has to be found again. Turn off only to compare. |
| **High-rate camera lane** | on / off | on |  | A dedicated thread reads the camera hundreds of times a second so boxes stay locked while you turn. |
| **ESP time offset** | whole number | 0 | -30 to 60 | Shifts the moment the overlay predicts for. Raise it if boxes trail behind the game image, lower it if they lead. Default 0. |
| **Measured input latency** | whole number | 0 | 0 to 300 | Time from a mouse move leaving Hideway until the game camera turns (Debug -> LATENCY -> Measure). 0 = not measured. Use it as the Prediction / Trigger lead. |
| **Advanced debug** | on / off | off |  | Show raw addresses and discovered offsets on the Debug page. |
| **Player list** | on / off | off |  | Show the players Hideway currently reads on the Debug page. |
| **Statistics** | on / off | on |  | Show timing and counters on the Debug page. |
| **Telemetry CSV** | on / off | off |  | Write one row per second of measured numbers (prediction error, data age, visibility flips, aim / trigger counters) to telemetry.csv next to the exe. Bounded: about 5.5 hours, then it restarts. |

