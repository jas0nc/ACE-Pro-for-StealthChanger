# ACE Pro + KTC-Easy for StealthChanger

Use an Anycubic ACE Pro (Gen 1) as a **filament dryer, filament buffer, and assisted filament loader/unloader** for a 4-toolhead StealthChanger running KTC-Easy.

> Status: **ACE Pro Gen 1 is the supported target**. ACE 2 Pro is not yet a drop-in option because community Klipper drivers currently target the USB-based Gen 1 ACE Pro, while ACE 2 Pro uses RS485.[web:17][web:69][web:77]

## What this project gives you

- A clear hardware modification plan for adapting ACE Pro to a 4-toolhead StealthChanger.[web:1][web:45][web:67]
- A practical way to integrate ACE-assisted **load** and **unload** into the usual KTC-Easy workflow, instead of treating ACE as a separate system.[web:144][web:154]
- Example Klipper config fragments and macros you can copy, tune, and version-control.
- A GitHub-ready starting point so you can share your progress with the community.

## Core idea

In a StealthChanger, each tool already has its own extruder. That means the ACE Pro is **not** used like an AMS feeding a single hotend through a 4-in-1 hub. Instead, each ACE slot maps to one toolhead:

- Slot 0 -> T0
- Slot 1 -> T1
- Slot 2 -> T2
- Slot 3 -> T3

Each slot feeds one PTFE path directly to its matching toolhead. KTC-Easy still handles tool pickup/parking, while ACE handles drying, buffering, and long filament moves in the reverse-Bowden path.[web:144][web:145][web:31]

## Repository layout

- `docs/overview.md` - how the system is meant to work
- `docs/hardware-mods.md` - physical modifications to the ACE Pro
- `docs/ktc-easy-integration.md` - what to change in your KTC-Easy macro flow
- `config/examples/ace.cfg` - example ACE driver config
- `config/examples/ace_ktc_macros.cfg` - example macros for load/unload and tool-aware ACE assist
- `scripts/install-notes.md` - install checklist and bring-up order

## Recommended bring-up order

1. Confirm your StealthChanger works normally with KTC-Easy first.[web:144][page:1]
2. Connect the ACE Pro to Klipper and confirm the driver responds.[web:17][web:31]
3. Modify the ACE filament exits and route one PTFE tube per toolhead.[web:45][web:67]
4. Make ACE-assisted manual load/unload work from the console.
5. Only then hook those steps into your KTC-Easy-friendly `LOAD_FILAMENT` and `UNLOAD_FILAMENT` macros.[web:154]

## Important limitation

The ACE Pro cannot really be treated as a fully standalone dryer/AMS brain in this setup. It needs a controller connection, and your Klipper macros provide the workflow logic when used off an Anycubic stock printer.[web:29][web:31]
