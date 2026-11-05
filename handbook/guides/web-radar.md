# Web radar on your phone

The web radar shows your radar in a browser: a phone, a tablet, a second monitor. Hideway serves the page itself. **Nothing goes to the internet**: no cloud, no account.

## Turn it on

1. **Radar > WEB RADAR**: tick **Web radar**.
2. To open it from another device, tick **Allow other devices (LAN)**. Off (the default) means this PC only (`127.0.0.1`).
3. Press **Copy radar link** and open it in the other device's browser (same network).

{% hint style="warning" %}
**The link contains an access key** (saved in `webradar.key` next to the exe). Without it every request is refused, and after 12 wrong keys an address is shut out for a minute. **New access key** makes old links stop working. The key is never shown on screen, only inside the copied link. Do not post the link.
{% endhint %}

## On the page

Rotate with your view or north-up · zoom (wheel, pinch, + / −) · names · distance rings · your field of view · a player list (sort by distance / kills / health, team and bot filters) · tap a player for details · height arrows for players above / below you. Settings are remembered in the browser. The page keeps the screen on while open and reconnects by itself when Hideway restarts.

## Smoothness

Hideway sends **20 updates per second** by default (**Web radar rate** = 50 ms). The page extrapolates positions from the velocities, so motion stays smooth at your screen's refresh rate.

## Names

**Web radar names** off = names are **not sent at all**.

## Phone cannot connect?

1. Phone and PC must be on the **same network**.
2. **Windows Firewall** must allow Hideway on private networks. The first start asks; if you clicked Cancel, run this in an **admin PowerShell** (use your own port):

   ```bash
   New-NetFirewallRule -DisplayName "Hideway radar" -Direction Inbound -Protocol TCP -LocalPort 8765 -RemoteAddress LocalSubnet -Action Allow -Profile Any
   ```

   `LocalSubnet` keeps it to devices on your own network. `-Profile Any` is needed when Windows calls your Wi-Fi "Public", which is the default on many home networks.
3. Quick test: open `http://<PC address>:8765/` on the phone **without** the key. "Access key needed" means the network path works.
4. **Allow other devices (LAN)** must be on.
5. If the page says the **port is in use**, change **Web radar port**.

## Safety notes

* LAN access is **off by default** since 2.10.0, and the web radar settings are never imported from shared configs.
* Only enable LAN on a network you trust.
