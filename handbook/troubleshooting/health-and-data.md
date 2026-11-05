# Health and shield bars

## The short answer

**Enemy health and shield are usually not available.** In recorded matches on Fortnite 43.00, Hideway read health directly for about **three quarters of teammates** and for **about 1 % of enemies**. The game appears to send health only for you and your own squad. When the game gives no value, Hideway shows **no bar** rather than an invented one.

{% hint style="info" %}
This is an observation from real logs, not a rule Hideway can prove: the three places a health value can live (the pawn's health set, its base value, and the copy kept in the player's state) were all empty for enemies, so there is nothing more to read.
{% endhint %}

## What you will see

| Situation | On screen |
|---|---|
| Teammate whose health was read | Health and shield bars |
| Enemy whose health was not sent | **No bar** (never a full or empty bar made up) |
| Knocked player | Treated as known (a knocked player has a meaning even at 0) |

The **Health numbers** option follows the same rule: nothing is drawn when the game gives no value. **Low health highlight** (a pulsing red outline) only appears when a real health value was read.

## Check it yourself

**Debug > DATA HEALTH > Health / shield** says exactly what you have:

| Row says | Meaning |
|---|---|
| `LIVE` | Nearly every enemy's health is read |
| `PARTIAL ... teammates only; no enemy value is sent` | You get your squad, not enemies |
| `PARTIAL ... enemies N of M` | Some enemies, not all |
| `MISSING ... none readable` | Nothing readable at all: check OFFSET HEALTH > Health |
| `WAITING` | No players or no health counters yet (lobby, first tick) |

The log line has the same split: `health: 2 direct (2 mates, 0 enemies) ... 10 unknown (0 mates, 10 enemies)`. And `HEALTH probe:` lines print, for a few players every 30 s, what each of the three sources holds (all zeros means the game sent nothing).

## What Hideway tries before giving up

1. The pawn's health set, read directly.
2. The pawn's health set again, re-resolved if the first read was stale.
3. The base value of that set.
4. The copy kept in the player's state.

Only if none gives a plausible number is the player marked *unknown*, and nothing is drawn.

## Other things that show on the bar

* **Bar style**: Classic or Segmented (split in four).
* **Bar side**: which side of the box.
* **Damage trail**: the lost part drains down slowly.
* **Team ID**, **Weapon class** and **Enemy ammo** are separate data sources. Enemy ammo is shown only when the weapon was read.

## What about damage?

Because enemy health is not available, a damage readout for enemies is not either. A different signal (such as "this enemy was just hit") may exist and is being researched; do not expect it in the current version.
