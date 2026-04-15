# Overview

## What this setup is

This setup uses an Anycubic ACE Pro as an external 4-lane support system for a StealthChanger. It is not acting like a classic single-nozzle MMU. Instead, each ACE lane maps to one toolhead, and each toolhead keeps its own extruder and hotend.[web:144]

## Functional split

Think about the system in three layers:

- **KTC-Easy** manages toolchanger behavior: pickup, park, active tool, and tool config.[web:144]
- **Tool extruder** handles short, precise nozzle-side moves.
- **ACE Pro** handles drying, buffering, and long filament moves through the reverse-Bowden path.[web:31][web:105]

## Why this matters

If you keep these roles separate, the macro design becomes much easier. You do not want one giant macro trying to hide every detail. You want one layer for tool-side moves and one layer for ACE-side moves.
