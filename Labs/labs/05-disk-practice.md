# Lab 05: Disk usage

**Goal:** find out which folders in your home directory use the most space.

**Linked section:** [05 Disk usage](../sections/05-disk-usage.md)

## Steps

```bash
df -h
du -sh ~/* 2>/dev/null | sort -h | tail -5
```

## What to check

The last five lines are your biggest folders. Compare the root filesystem line in `df -h` with the total of your home folder.

## Clean up

Nothing to clean up. This lab only reads information.
