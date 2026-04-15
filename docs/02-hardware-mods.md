# Hardware Modifications

## Goal

Adapt the ACE Pro so it can feed four separate StealthChanger tools cleanly and repeatably.[web:1][web:45]

## Step 1: Use one channel per tool

Do not use a 4-in-1 printhead hub. For a StealthChanger, route one ACE output per tool:

- Slot 0 -> T0
- Slot 1 -> T1
- Slot 2 -> T2
- Slot 3 -> T3

## Step 2: Improve PTFE exits

The stock ACE routing is not ideal for long reverse-Bowden paths. Add pass-through fittings or a printed exit support so each PTFE tube leaves the ACE cleanly and does not rub a sharp edge.[web:45]

Suggested parts:

- 4x PC4-M6 pass-through fittings
- 4mm OD PTFE tube
- optional printed rear exit bracket or interface plate

## Step 3: Give the buffer room

The ACE buffer is sensitive to tube routing and placement, so leave clearance around the machine and avoid tight bends right at the output.[web:67][web:7]

Practical rules:

- Leave at least 12-15 cm around the ACE where the tubes exit.
- Use broad curves, not tight bends.
- Make sure docked tools do not tug directly on the ACE exits.

## Step 4: Connect the ACE to Klipper

The Gen 1 ACE Pro is practical here because it can present as a USB CDC-ACM serial device when adapted correctly, often referenced as `/dev/serial/by-id/usb-ANYCUBIC_ACE_0-if00`.[web:17][web:105] That is the key difference versus ACE 2 Pro, which uses RS485.[web:69][web:77]

## Step 5: Validate mechanically before tuning macros

Before software integration, prove all three of these:

1. ACE can grab filament in the chosen slot.
2. ACE can move filament through the full PTFE path.
3. Tool pickup and parking do not disturb the buffer.
