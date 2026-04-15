# Tuning Guide

## Tune one tool first

Always tune T0 first. Even if your build is symmetric, real PTFE routing usually is not.

## Values you will tune

### Tool-side unload distance

This is the short retract needed to get the filament out of the melt zone.

### ACE-side unload distance

This is the long retract back to a safe parked position in the PTFE path.

### ACE-side load distance

This is the long feed from the ACE toward the tool.

### Tool-side load distance

This is the final push and purge into the hotend.

## Practical method

1. Tune the tool-side unload first.
2. Tune the ACE-side unload second.
3. Tune the ACE-side load third.
4. Tune the tool-side final load and purge last.

## Recommendation

Write these values down per tool. Small path differences matter.
