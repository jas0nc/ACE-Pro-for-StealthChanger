# Klipper Install

## Bring-up order

Do not try to install everything at once.

### Phase 1: StealthChanger first

Confirm KTC-Easy is working and your four tools can be picked up and parked reliably.[web:144]

### Phase 2: ACE communication second

Install a supported ACE Pro integration and confirm Klipper can talk to the unit.[web:31][web:52][web:57]

Checks:

- device appears in `/dev/serial/by-id/`
- ACE config loads without errors
- `ACE_INFO` responds
- manual `ACE_FEED` and `ACE_RETRACT` work

### Phase 3: one lane only

Start with slot 0 -> T0 only. Do not scale to all four lanes until you have one lane working cleanly.

## Example include structure

Add these to your `printer.cfg`:

```ini
[include config/ace.cfg]
[include config/ace_ktc_macros.cfg]
```

If your config tree lives elsewhere, adjust the paths to match your Klipper layout.
