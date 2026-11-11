  # Lab 01: Files and navigation

**Goal:** create a folder, add a file, move it, and find it again.

**Linked section:** [01 Files and navigation](../sections/01-files-and-navigation.md)

## Steps

```bash
mkdir practice && cd practice
touch notes.txt
mkdir labs
mv notes.txt labs/
ls -lah labs/
find . -name "notes*"
cd ~ && rm -r practice
```

## What to check

`find` should show `./labs/notes.txt` before you delete the folder.

## Clean up

The last line deletes the `practice` folder. Only run it when you're finished.
