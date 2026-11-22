# What to expect

What works, what the game does not allow, and what has not been proven in a real match yet. Last checked against version 3.2.6 and a 15-minute match on Fortnite 43.10.

## Works in real matches

* Players, names, teams, bots, camera and the fast reads (about 5 ms per read cycle).
* Skeletons, checked against recordings.
* Smooth ESP, measured on real recordings.
* Visibility from the game's render time, which agreed with the line-of-sight check in about 9 of 10 comparisons.
* Loot ESP: pickup layout, ammo and item names read correctly.
* The match summary in the log.

## Limits of the game

| What | Why |
|---|---|
| No health or shield bars on enemies | Fortnite only sends them for you and your squad. See [Health and shield bars](../troubleshooting/health-and-data.md) |
| Frozen skeletons on hidden and far players | The game barely animates what it does not draw, and far players are read less often |
| Players in the air move in small steps | Their position snaps back about 12 cm every 33 ms in the game's own movement code, and the ESP follows it |
| Visibility is the game's own render flag | It can call a player behind thin cover or a window visible and it blinks at the edge of the view (a box keeps its colour for 150 ms). The wall check reads the level's fixed geometry only, which does not contain the walls players build |
| Some weapon classes read as *Other* | Only some animation ids are confirmed |
| A patch breaks the ESP for a while | The offsets belong to one Fortnite build. See [After a Fortnite update](../guides/after-a-fortnite-update.md) |
| The game's own log is not readable | It lives on the game PC |

## Not proven in a real match yet

These pass their tests, but nobody has watched them work live:

* Aim delay compensation (3.2.5): measured on a recording and proven in a simulation.
* The smoothed aim lead (3.2.4).
* Reboot cards, the spectator list, audio alerts and facing direction.
* Squad list, match info panel, low health outline and enemy ammo. They need data the game mostly does not send, so they only appear when real values exist.
* Recovery after the DMA card drops in the middle of a session.

## Other open items

* The programs are not code-signed.
* The install folder is writable by your Windows user while the launcher and overlay run as administrator.
* Ferrum follows the vendor documentation and is the least tested of the three input devices.
* The web radar has not been tested from another machine on an untrusted network.

When any of this changes it is in the [release notes](release-notes.md) and on this page.
