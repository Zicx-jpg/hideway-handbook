# Glossary

| Term | Meaning |
|---|---|
| **DMA** | Direct Memory Access. A PCIe card in the game PC that lets another PC read the game's memory over USB, without running code on the game PC |
| **JTAG port** | The card's second USB-C port, used only to flash firmware. The other one is the DATA port |
| **VT-d / IOMMU** | The BIOS feature (Intel / AMD) that restricts what PCIe devices may read; DMA setups usually need it off |
| **FT601** | The FTDI USB 3 chip on most DMA cards; its driver shows in Device Manager |
| **Page file** | Windows' overflow area on the drive. The card cannot read it, so low RAM makes data vanish |
| **Pass-through** | An input device that forwards your real mouse and only adds its own movement |
| **Game PC / overlay PC** | The PC running Fortnite (with the card) / the PC running Hideway |
| **Overlay** | The transparent window Hideway draws ESP, radar and the menu on |
| **ESP** | Boxes, skeletons, names and other information drawn on players |
| **Offsets** | Positions of fields inside the game's structures. Each Fortnite patch can move them. They live in `all\` |
| **UWorld / GameState** | The game's world object and the object holding match-wide data (players left, teams left) |
| **Pawn** | A player's in-world character object |
| **PlayerState** | The per-player record: name, team, platform, kills and a copy of some values |
| **Team ID** | The game's own team number, shown before the name |
| **Tick** | One full read-and-update cycle of Hideway's player lane |
| **Data age** | How old what is on screen is |
| **Scatter reads** | Reading many values in one round trip over the card |
| **Camera lane** | A dedicated thread that reads the camera hundreds of times a second |
| **Governor** | The load control that thins skeleton reads when the card link is the bottleneck |
| **Wall check** | Reading the level's collision geometry so rays can be traced to see if a player is behind something |
| **Render time** | The time the game last drew a player's mesh; the basis of the default visibility check |
| **Submit time** | The time a mesh was last submitted to the renderer; used by the experimental visibility mode |
| **Core animation id** | The raw number the game reports for the type of the held weapon |
| **Input device** | A hardware device (MAKCU, Ferrum, KMBox NET) that moves and clicks the mouse for aim and trigger |
| **MAKCU / Ferrum / KMBox NET** | The three supported input devices |
| **Fuser** | A capture-card setup that merges the game picture and the overlay; "Fuser mode" gives it a pure-black window |
| **Web radar** | The radar served as a web page for a phone or second screen |
| **Config** | A named set of all options |
| **Preset** | A short list of options applied on top of your settings |
| **Signed release** | A release whose manifest is signed by the publisher; every file's SHA-256 is checked against it |
| **Launcher** | `HidewayLauncher.exe`, the front door that verifies, starts and updates the game module |
| **Module** | A game's program inside the launcher; today only Fortnite |
| **Recording (`.hwrec`)** | A flight recording of raw frames for support |
| **READY CHECK** | The Debug card that lists each part of the setup in green / orange / red |
| **DATA HEALTH** | The Debug card that lists each data source and how many players have it |
