# Install Checklist

## Stage 1: StealthChanger baseline

- KTC-Easy installed.[web:144]
- All tools can be docked and picked up cleanly.
- Each tool extruder works by itself.

## Stage 2: ACE baseline

- ACE communication works.
- `ACE_INFO` responds.
- `ACE_FEED` works.
- `ACE_RETRACT` works.

## Stage 3: first integrated path

- Slot 0 routed to T0.
- `UNLOAD_FILAMENT TOOL=0` works.
- `LOAD_FILAMENT TOOL=0` works.
- filament parks and reloads repeatably.

## Stage 4: copy to other tools

- verify T1
- verify T2
- verify T3

## Stage 5: quality pass

- tune distances
- label slot to tool mapping
- document your final values in Git
