# Lab 05: Processes and system information

**Goal:** start a background job, find it, and stop it.

**Linked section:** [05-processes-and-system](../sections/05-processes-and-system.md)

## Steps

```bash
sleep 300 &
jobs
ps aux | grep "[s]leep"
kill %1
jobs
```

## What to check

The first `jobs` lists the sleep job. After `kill %1`, the second `jobs` should be empty.
