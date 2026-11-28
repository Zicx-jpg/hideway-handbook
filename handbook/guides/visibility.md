# Visibility: the game's own render time

"Visible" decides the box colour (visible / hidden), whether aim and trigger consider a player, and more. Hideway uses the game's own answer: Unreal Engine stamps every character mesh with the time it was last **drawn on screen**, and a player whose stamp is within the tolerance (200 ms) of the game's clock counts as visible.

## How it works

* No level geometry has to be read, so it works from the first second of a match and follows what the renderer really did. It does not depend on the level's collision geometry, which does not contain the walls players build.
* The flag blinks: at the edge of the view or behind a thin object it flips many times a second. So a box keeps the visible colour for 150 ms after the flag dropped (hidden to visible is never delayed), and an aim target that was visible a moment ago stays eligible for 200 ms. Both are only about the colour and the lock: the rule itself is unchanged.
* The aim and the trigger also listen to the game's own crosshair trace. If it ends in front of the player (a wall, a build someone placed), they stop, even when the render-time flag still says visible. That is only used once the trace has proven it works.
* The trigger uses the same rule (**Trigger visible only**) together with the hitbox point under the crosshair, and its source is always the strictest (the game's own target and Hideway's hitbox have to agree).

{% hint style="warning" %}
The render-time flag is the engine's occlusion result, not a ray. A player drawn behind thin cover, a window or a fence can count as visible, and a player at the very edge of a wall can blink. The level's collision geometry (the wall check) is read as well, for the loot reader and as a second opinion on the triggerbot's hitbox point (it must not lie behind level geometry), but it does not decide the box colour.
{% endhint %}

## Settings

Since 3.8.4 the visibility rule is back in the menu: Aimbot page, card **VISIBILITY CHECK**, with **Visible only**, **Visibility check** (the method), **Visibility tolerance** and, with a wall-trace method, **Wait for wall check**. The defaults are the ones Hideway used while they were automatic (on, UE5 render time only, 200 ms). **Trigger visible only** is on the Triggerbot page, and each weapon tab with **Override** on has its own **Visible only** (on by default since 3.8.4).

## If something looks wrong

| You see | Try |
|---|---|
| Aim or trigger goes through a wall | A wall or a thin cover the renderer did not cull. Note the place and send a recording (see [Collect diagnostics](../troubleshooting/collecting-diagnostics.md)) |
| Boxes flash between two colours | The game's flag blinks at the edge of the view; since 3.6.1 the visible colour is kept for 150 ms. A box that stays white a long time is really hidden |
| Boxes stay hidden for everyone | Check **Debug > DATA HEALTH > Visibility**; in a lobby it is *WAITING* |

See also [Aim reaches through a wall](../troubleshooting/aim-and-trigger.md#aim-reaches-through-a-wall).
