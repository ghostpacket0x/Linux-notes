# Lab 25: Backups and recovery

**Goal:** make a backup with tar and rsync, check it with checksums, simulate losing a file, and restore it.

**Linked section:** [23 Backups and recovery](../sections/23-backups-and-recovery.md)

## Steps

Create some practice data and a backup folder:

```bash
mkdir -p backup-lab/notes backup-lab/mirror
echo "chapter one" > backup-lab/notes/one.txt
echo "chapter two" > backup-lab/notes/two.txt
cd backup-lab
```

Make an archive and a checksum:

```bash
tar -czf notes-backup.tar.gz notes/
sha256sum notes-backup.tar.gz > notes-backup.tar.gz.sha256
sha256sum -c notes-backup.tar.gz.sha256
```

Make a mirror with rsync, checking first with a dry run:

```bash
rsync -av --delete --dry-run notes/ mirror/
rsync -av --delete notes/ mirror/
diff -r notes mirror && echo "mirror matches"
```

Now simulate losing a file and restore it from the archive:

```bash
rm notes/two.txt
mkdir restore && tar -xzf notes-backup.tar.gz -C restore
cp restore/notes/two.txt notes/
cat notes/two.txt
```

## What to check

- `sha256sum -c` should print `OK`.
- The dry run should list the files it would copy, and the real `rsync` should finish without errors.
- `diff -r` should print `mirror matches`.
- After the restore, `cat notes/two.txt` should print `chapter two`.

## Clean up

```bash
cd ~ && rm -r backup-lab
```
