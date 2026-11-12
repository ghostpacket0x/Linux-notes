# Lab 23: Finding interesting files

**Goal:** search a practice folder by name, size, age, and permissions, then act on the results.

**Linked section:** [22 Finding interesting files](../sections/22-finding-interesting-files.md)

## Steps

Create a practice folder with a few files of different kinds:

```bash
mkdir -p find-lab/docs find-lab/tmp
cd find-lab
echo "notes" > docs/notes.txt
echo "temp" > tmp/cache.tmp
dd if=/dev/zero of=docs/big.bin bs=1M count=12 2>/dev/null
chmod 666 tmp/cache.tmp
chmod 4755 docs/notes.txt
```

Now search:

```bash
find . -name "*.txt"
find . -type f -size +10M
find . -mmin -5
find . -perm -o+w -type f
find . -perm -4000 -type f
find . -name "*.tmp" -exec ls -l {} \;
```

## What to check

- `-name "*.txt"` should find `notes.txt` only.
- `-size +10M` should find `big.bin`.
- `-perm -o+w` should find `cache.tmp`, because you made it writable for everyone.
- `-perm -4000` should find `notes.txt`, because you set the SUID bit on it.

Explain in your own words why the SUID file matters, then remove the bit with `chmod u-s docs/notes.txt` and run the last search again. It should return nothing.

## Clean up

```bash
cd ~ && rm -r find-lab
```
