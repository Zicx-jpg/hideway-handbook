# Visibility: Raycast VisCheck (Unreal Engine 5)

"Visible" decides the box colour (visible / hidden), whether aim and trigger consider a player, and more. Hideway judges it with **Raycast VisCheck** for Unreal Engine 5: rays are traced from your camera to the player against the **level's collision geometry**, and a player is visible only if the line is clear.

## How it works

* Hideway reads the level's collision geometry a few seconds into a match. From then on every player is checked against it.
* Aim always checks the bone it wants to shoot at.
* Until the geometry is ready, aim waits instead of guessing, so aim does not start in the first seconds of a match.
* The same rule is used by the trigger (**Trigger visible only**) together with the hitbox point under the crosshair.

{% hint style="warning" %}
The level's geometry is **static**. It does not know about **walls players build**. A target behind your own or an enemy's built wall can still count as visible.
{% endhint %}

## Settings

**Visible only** (Aimbot) makes the aim ignore targets that are not visible. There is nothing else to tune: the method is automatic.

## If something looks wrong

| You see | Try |
|---|---|
| Aim works in the first seconds of a match | It should wait for the level geometry. If it does not, report it with **Copy diagnostics** |
| Aim or trigger goes through a wall | **Visible only** is off, or the wall was built by a player (see the note above) |
| Boxes stay red / hidden for everyone | Check **Debug > DATA HEALTH**; the level may not have been read yet |

See also [Aim reaches through a wall](../troubleshooting/aim-and-trigger.md#aim-reaches-through-a-wall).
