# Known limits and what is verified

Honest status of version **2.10.2**. *Seen live* means it was observed working in a real match on Fortnite 43.00. *Offline only* means it passes tests on synthetic or recorded data but nobody has watched it work in a real match yet.

## Seen live

| Feature | Notes |
|---|---|
| Player names, bots, teams, camera, scatter reads | On 43.00 |
| Loot ESP | The pickup layout is proven live: ammo and item names read correctly |
| Skeletons | Bones verified correct against a recording |
| Smooth ESP | Measured on real recordings |
| Match counters in the log | The per-match summary line is written |

## Limits you will run into

| Limit | Why |
|---|---|
| **No enemy health / shield bars** | The game does not appear to send enemy health: read directly for about 1 % of enemies and about three quarters of teammates. No bar is drawn instead of an invented one |
| **Hidden and far players' skeletons look static** | The game itself barely animates what it does not draw; distant players are also read less often |
| **Built walls are invisible to the wall check** | It reads the level's static geometry only. A target behind a player-built wall can still count as visible |
| **Weapon classes are only partly known** | Only some core animation ids are confirmed on 43.00. Others read as `Other` |
| **Offsets follow the game build** | After a Fortnite patch there can be a gap without ESP until new offsets are released |
| **The game's log is not readable** | Fortnite's own log and crash report live on the game PC |

## Offline only (not yet watched in a real match)

* Reboot cards
* Spectator list (the layout comes from a community post and is checked on every read)
* Audio alerts
* Facing direction
* Fade-in and label placement
* Squad list, match info panel, low health outline, enemy ammo (the data they need is mostly not sent; they appear only when real values exist)
* Skeleton joint filter (2.10.0)
* The "Only with a gun in hand" rule in 2.10.2: derived from a recording (pickaxe ammo 0, build tool ammo 0 about 95 % of the time), not yet seen in a match with a wall placed
* Recovery after the DMA card drops mid-session

## Other open items

* Programs are not Authenticode-signed.
* The install folder is writable by your user while the launcher and overlay run elevated.
* Ferrum: follows the manufacturer's documentation but is the least proven of the three devices.
* The web radar has not been penetration-tested from another machine.

{% hint style="info" %}
When something here changes, it is in the [Release notes](release-notes.md) and this page is updated.
{% endhint %}
