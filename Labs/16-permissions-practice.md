# Lab 16: Permissions and ownership

**Goal:** create a file, change its permissions step by step, and read the results.

**Linked section:** [16 Permissions and ownership](../sections/16-permissions-and-ownership.md)

## Steps

```bash
mkdir -p perm-lab && cd perm-lab
echo "secret note" > notes.txt
ls -l notes.txt
chmod 600 notes.txt
ls -l notes.txt
chmod 644 notes.txt
stat -c '%a %U %G %n' notes.txt
chmod u+x notes.txt
ls -l notes.txt
```

## What to check

- After `chmod 600`, the string should be `-rw-------`, so only you can read it.
- After `chmod u+x`, the owner should have an `x` in the first group.
- `stat` should print the octal value, for example `644`.

## Clean up

```bash
cd ~ && rm -r perm-lab
```
