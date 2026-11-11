# Lab 09: Packages

**Goal:** install a small tool, check that it works, then remove it.

**Linked section:** [09 Packages](../sections/09-packages.md)

## Steps

```bash
sudo apt update
apt search tree
sudo apt install tree
tree -L 1
apt list --installed | grep tree
sudo apt remove tree
```

## What to check

After `apt remove`, running `tree` should report "command not found".

## Clean up

The last line removes the package.
