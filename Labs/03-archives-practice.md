# Lab 03: Archives and rsync

**Goal:** pack a folder into an archive, check it, and restore it to a new place.

**Linked section:** [03 Archives and rsync](../sections/03-archives-and-rsync.md)

## Steps

```bash
mkdir -p demo && echo "hello" > demo/a.txt
tar -czf demo.tar.gz demo/
tar -tf demo.tar.gz
mkdir restore && tar -xzf demo.tar.gz -C restore
rsync -av demo/ backup/
ls restore/demo backup/
```

## What to check

Both new folders should contain `a.txt`. `tar -tf` should list `demo/` and `demo/a.txt`.

## Clean up

```bash
rm -r demo restore backup demo.tar.gz
```
