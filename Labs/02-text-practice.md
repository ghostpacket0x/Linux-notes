# Lab 02: Viewing and editing text

**Goal:** create a small log file, then search and count it.

**Linked section:** [02 Viewing and editing text](../sections/02-text-and-viewing.md)

## Steps

```bash
echo "error: disk full" > log.txt
echo "all good" >> log.txt
echo "error: timeout" >> log.txt
grep -n "error" log.txt
wc -l log.txt
sort log.txt
tail -n 1 log.txt
```

## What to check

Predict each result before you run the command. `grep -n` should show two matching lines with their line numbers. `wc -l` should report 3 lines.

## Clean up

```bash
rm log.txt
```
