# ACE Pro for StealthChanger with KTC-Easy

A GitHub-ready starter repository for using an **Anycubic ACE Pro (Gen 1)** as a **filament dryer, filament buffer, and assisted filament transport system** for a **4-toolhead StealthChanger** running **KTC-Easy**.

## Project status

- Supported target: **ACE Pro Gen 1**
- Not yet drop-in: **ACE 2 Pro**, because community Klipper integrations target the Gen 1 USB-connected ACE Pro, while ACE 2 Pro uses RS485.[web:17][web:69][web:77]

## Why this repo exists

A StealthChanger already has one extruder per tool, so the ACE Pro should not be treated like a Bambu AMS or a single-nozzle MMU. In this build, the ACE Pro acts as:

- a 4-slot dryer,[web:43]
- a 4-lane buffer,[web:1][web:7]
- and a long-distance filament mover between spool and toolhead.[web:31][web:105]

KTC-Easy still handles tool pickup, park, and active tool selection.[web:144] This repository shows how to keep the normal `LOAD_FILAMENT` / `UNLOAD_FILAMENT` user workflow, but make those macros ACE-aware so the operator experience stays simple.[web:154]

## Repository layout

```text
acepro-stealthchanger-ktc-repo/
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── 01-overview.md
│   ├── 02-hardware-mods.md
│   ├── 03-klipper-install.md
│   ├── 04-ktc-workflow.md
│   └── 05-tuning.md
├── config/
│   ├── ace.cfg
│   └── ace_ktc_macros.cfg
├── templates/
│   └── printer.cfg.include.example
└── scripts/
    └── install-checklist.md
```

## Recommended bring-up order

1. Get StealthChanger working normally with KTC-Easy first.[web:144]
2. Get the ACE Pro driver working from Klipper and confirm `ACE_INFO` responds.[web:17][web:31]
3. Modify the ACE hardware and route one PTFE tube per tool.[web:45][web:67]
4. Tune ACE load/unload on **one tool only**.
5. Fold the ACE steps into `LOAD_FILAMENT` and `UNLOAD_FILAMENT`.
6. Clone the working pattern to T1, T2, and T3.

## Design assumption used in this repo

Start simple:

- ACE slot 0 -> T0
- ACE slot 1 -> T1
- ACE slot 2 -> T2
- ACE slot 3 -> T3

Keep that mapping until everything works.

## Important limitation

The ACE Pro is not truly standalone in this setup. It needs a live controller connection, and the workflow logic comes from your Klipper macros rather than stock Anycubic firmware behavior.[web:29][web:31]
