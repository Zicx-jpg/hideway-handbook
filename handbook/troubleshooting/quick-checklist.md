# Quick checklist

Work top to bottom. Stop at the first thing that is not right. Each step links to the page with the full fix.

{% stepper %}
{% step %}
### Hardware is powered and connected
Game PC on, DMA card seated, its USB cable plugged into the overlay PC (a USB port directly on the motherboard). → [DMA card](dma-card.md)
{% endstep %}

{% step %}
### Hideway starts and you are signed in
Launcher opened as administrator, license accepted, system clock correct. → [Start-up and license](startup-and-license.md)
{% endstep %}

{% step %}
### READY CHECK
Open **Debug** (Misc > Debug > Show debug page). Read the **Next:** line of the **READY CHECK** card. → [READY CHECK](../getting-started/ready-check.md)
{% endstep %}

{% step %}
### You are in a match
The lobby has no players to draw. "waiting (lobby / loading)" is normal until a match starts.
{% endstep %}

{% step %}
### OFFSET HEALTH has no red line
A red *World*, *Camera* or *Players* line usually means the game was patched. → [After a Fortnite update](../guides/after-a-fortnite-update.md)
{% endstep %}

{% step %}
### DATA HEALTH shows LIVE for what you use
Names, Team ID, Skeleton should be LIVE in a match. Health may be PARTIAL (teammates only). → [Health and shield bars](health-and-data.md)
{% endstep %}

{% step %}
### Input device (only if you use aim or trigger)
Connected in the top bar, **Test move (+/-60)** moves the mouse. → [Connect an input device](../guides/input-device.md)
{% endstep %}
{% endstepper %}

## Symptom table

| What you see | Go to |
|---|---|
| The app does not start, a message box appears | [Start-up and license](startup-and-license.md) |
| `DMA OFFLINE` in the top bar | [DMA card](dma-card.md) |
| No boxes in a match | [No ESP](no-esp.md) |
| Boxes but no names | [ESP quality](esp-quality.md#names-are-blank) |
| Boxes jump, lag or are offset | [ESP quality](esp-quality.md) |
| Skeletons look frozen | [ESP quality](esp-quality.md#skeletons-look-static) |
| No health bars on enemies | [Health and shield bars](health-and-data.md) |
| Aim does nothing | [Aim or trigger problems](aim-and-trigger.md#aim-does-nothing) |
| Aim locks on while I place a wall | [Aim or trigger problems](aim-and-trigger.md#aim-locks-on-while-i-place-a-wall) |
| Aim reaches through a wall | [Aim or trigger problems](aim-and-trigger.md#aim-reaches-through-a-wall) |
| Fortnite closed by itself | [The game closes or crashes](game-closes-or-crashes.md) |
| An update failed | [Launcher and updates](launcher-and-updates.md) |
| Phone cannot open the web radar | [Web radar](../guides/web-radar.md#phone-cannot-connect) |
| None of the above | [Collect diagnostics](collecting-diagnostics.md) |
