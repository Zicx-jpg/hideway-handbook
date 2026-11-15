# Health and shield bars

## Short answer

Enemy health and shield are not available. Fortnite only sends them to your own client for you and your squad. In the last full 15-minute recording (build 43.10) Hideway read health for 100 % of the teammate samples and for 0.3 % of the enemy samples. The three places a health value can live were all empty for enemies, so there is nothing more to read. This is a limit of the game, not a setting.

When there is no value, Hideway draws no bar. It does not draw a full or empty bar that it made up.

## What you will see

| Situation | On screen |
|---|---|
| A teammate whose health was read | Health and shield bars |
| An enemy | No bar, apart from the rare moment the game does send a value |
| A knocked player | Shown as knocked, whatever the number is |

**Health numbers** follows the same rule, and **Low health highlight** (a pulsing red outline) only appears when a real value was read.

## Check it yourself

**Debug > Data health > Health / shield** says what you have right now:

| The row says | It means |
|---|---|
| LIVE | Almost every enemy's health is read |
| PARTIAL, teammates only | You get your squad, not the enemies |
| PARTIAL, enemies N of M | Some enemies, not all |
| MISSING | Nothing is readable: check Offset health > Health |
| WAITING | No players yet, or the first tick |

The log has the same split, for example `health: 2 direct (2 mates, 0 enemies) ... 10 unknown (0 mates, 10 enemies)`. The `HEALTH probe` lines show what each of the three sources holds for a few players; all zeros means the game sent nothing.

## What Hideway tries before it gives up

1. The player's health set, read directly.
2. The same set, found again if the first read was out of date.
3. The base value of that set.
4. The copy that Fortnite keeps in the player's state.

If none gives a believable number the player is marked unknown and nothing is drawn.

## Related options

* **Bar style**: Classic, or Segmented (split in four so 25, 50 and 75 % are easy to see).
* **Bar side**: which side of the box.
* **Damage trail**: the lost part of a bar drains down slowly.
* **Enemy ammo** and **Weapon class** are separate data and only show when the weapon was read.

Because enemy health is not available, a damage readout for enemies is not either.
