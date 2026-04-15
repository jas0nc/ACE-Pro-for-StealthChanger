# KTC Workflow Integration

## Main idea

Keep the normal user-facing actions:

- `LOAD_FILAMENT TOOL=n`
- `UNLOAD_FILAMENT TOOL=n`
- `CHANGE_MATERIAL TOOL=n`

That is the best operator experience because KlipperScreen already recognizes the conventional `LOAD_FILAMENT` and `UNLOAD_FILAMENT` macro names in the Extrude panel.[web:154]

## Macro layers

Split your macros into small pieces:

### ACE-side helpers

- `_ACE_SET_ACTIVE_LANE TOOL=n`
- `_ACE_LOAD_TO_TOOL_ENTRY TOOL=n`
- `_ACE_UNLOAD_FROM_TOOL TOOL=n`

### Tool-side helpers

- `_TOOL_PREHEAT_FOR_LOAD TEMP=x`
- `_TOOL_PREHEAT_FOR_UNLOAD TEMP=x`
- `_TOOL_EXTRUDER_LOAD TOOL=n`
- `_TOOL_EXTRUDER_UNLOAD TOOL=n`

### User-facing macros

- `LOAD_FILAMENT TOOL=n`
- `UNLOAD_FILAMENT TOOL=n`
- `CHANGE_MATERIAL TOOL=n`

## Recommended unload sequence

1. Select the target tool.
2. Heat for unload.
3. Use the tool extruder to retract out of the melt zone.
4. Use ACE for the long retract back through the reverse-Bowden path.[web:146][web:149]

## Recommended load sequence

1. Fit the new spool in the matching ACE slot.
2. Insert filament until ACE grabs it.[web:22][web:36]
3. Select the target tool.
4. Heat for load.
5. Use ACE to advance filament through the long PTFE path.
6. Use the tool extruder to complete loading and purge.

## Why this is cleaner than separate ACE-only commands

A new StealthChanger builder already has enough to learn. Reusing familiar load and unload actions keeps the workflow understandable, while the internals become smarter.[web:144][web:154]
