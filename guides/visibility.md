# Visibility: three ways to know who is visible

"Visible" decides the box colour (visible / hidden), whether aim and trigger consider a player, and more. Hideway has **three independent sources**. Knowing them explains most "it aimed through a wall" or "it turned red too early" questions.

## 1. Render time (default)

**Visibility check: UE5 render time only.** The engine's own check: a player is visible when the game drew their mesh within a **tolerance window** of the world clock (**Visibility tolerance**, default 200 ms).

* Works from the first second of a match; reads no geometry.
* A player drawn behind **thin cover** can count as visible.
* Lower tolerance = stricter and quicker to turn hidden; higher = steadier.

## 2. Wall check (ray-cast)

**Visibility check: Unreal line of sight** or **Bones (head, chest, knee)** traces rays against the **level's collision geometry**, which Hideway reads a few seconds into a match.

* *Unreal line of sight*: one ray to the middle, one to the head, two to the capsule sides; hidden only if all are blocked.
* *Bones*: rays to the head, chest and one knee.
* Needs **Wall check (ray-cast)** (Misc > ENGINE), also used by the loot reader.
* Aim always checks the bone it wants to shoot at.
* Until the geometry is ready, **Wait for wall check** (Aimbot > VISIBILITY, on by default) pauses aim instead of trusting the render-time flag.

{% hint style="warning" %}
The wall check reads the **level's static geometry**. It does not know about **walls players build**. A target behind your own or an enemy's built wall can still count as visible.
{% endhint %}

## 3. Submit-time visibility (experimental)

**Submit-time visibility** judges from three render timestamps of each mesh (submitted, rendered, rendered on screen): submitted recently but not drawn = culled. It is checked against the world clock on every tick and ignored when the numbers do not look like times. Off by default.

In recorded matches on 43.00 the timestamps did read as times and the result agreed with the render-time rule in roughly nine of ten comparisons; whether it is *better* than the render-time rule has not been settled. The Aimbot page's **Submit-time reading** line says whether it works on your build, and **Debug > DATA HEALTH** shows its agreement.

## Which should I use?

| You want | Use |
|---|---|
| Works immediately, minimal setup | UE5 render time only (default) |
| Strict against static walls | Unreal line of sight, after a few seconds in a match |
| To experiment | Tick Submit-time visibility and watch DATA HEALTH |

For aim, combine **Visible only** with the style you chose. For the trigger, **Trigger visible only** uses the same rules plus the hitbox point under the crosshair.
