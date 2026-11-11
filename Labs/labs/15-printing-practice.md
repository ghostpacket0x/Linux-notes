# Lab 15: Printing and other tools

**Goal:** send a desktop notification and check the print queue.

**Linked section:** [15 Printing and other tools](../sections/15-printing-and-other-tools.md)

## Steps

```bash
notify-send "Practice" "Hello from the terminal"
lpq
```

## What to check

`notify-send` needs a desktop session. `lpq` should report that no printer is set up on a VM without one.

## Clean up

Nothing to clean up.
